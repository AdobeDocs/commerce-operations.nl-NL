---
title: AWS S3-emmertje voor externe opslag configureren
description: Configureer uw Commerce-project voor gebruik van de AWS S3-opslagservice voor externe opslag.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# AWS S3-emmertje voor externe opslag configureren

De [ Eenvoudige Dienst van de Opslag van Amazon (Amazon S3) ][AWS S3] is de dienst van de objecten opslag die industrie-leidende scalability, gegevensbeschikbaarheid, veiligheid, en prestaties aanbiedt. De AWS S3-service gebruikt emmers, of containers, voor gegevensopslag. Deze configuratie vereist u om a _privé_ emmer tot stand te brengen. Voor Adobe Commerce op wolkeninfrastructuur, zie [ verre opslag voor Commerce op de infrastructuur van de Wolk vormen ](cloud-support.md).

>[!WARNING]
>
>Adobe ontmoedigt het gebruik van openbare emmers sterk, omdat het een ernstig veiligheidsrisico vormt.

**om verre opslag met de adapter van AWS S3 toe te laten**:

1. Login aan uw Amazon S3 dashboard en creeer a _privé_ emmer.

1. Opstelling [ AWS IAM ] rollen. U kunt ook toegang en geheime sleutels genereren.

1. Schakel de standaardopslag voor de database uit.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configureer Commerce om het privéemmertje te gebruiken. Zie [ Verre opslagopties ](remote-storage.md#remote-storage-options) voor een volledige lijst van parameters.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Mediabestanden synchroniseren met externe opslag.

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx configureren

Nginx vereist extra configuratie om Authentificatie met de `proxy_pass` richtlijn uit te voeren. Voeg de volgende proxygegevens toe aan het `nginx.conf` -bestand:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Verificatie

Als u toegang en geheime sleutels in plaats van [ AWS IAM ] rollen gebruikt, moet u de [`ngx_aws_auth` module Nginx ][ngx repo] omvatten.

### Machtigingen

De S3-integratie is afhankelijk van de mogelijkheid om cacheafbeeldingen te genereren en op te slaan op het lokale bestandssysteem. Daarom zijn de omslagtoestemmingen voor `pub/media` en gelijkaardige folders het zelfde voor S3 als wanneer het gebruiken van lokale opslag.

### Bestandsbewerkingen

U wordt ten zeerste aangeraden om bij de ontwikkeling van de codering of extensie de methoden van de [!DNL Commerce] -bestandsadapter te gebruiken, ongeacht het type bestandsopslag. Wanneer u S3 gebruikt voor opslag, moet u geen native I/O-bewerkingen voor PHP-bestanden gebruiken, zoals `copy` , `rename` of `file_put_contents` , omdat S3-bestanden zich niet in het bestandssysteem bevinden. Zie [ DriverInterface.php ](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) voor codevoorbeelden.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth

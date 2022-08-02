---
title: AWS S3-emmertje voor externe opslag configureren
description: Configureer uw Commerce-project om de AWS S3-opslagservice voor externe opslag te gebruiken.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# AWS S3-emmertje voor externe opslag configureren

De [Amazon Simple Storage Service (Amazon S3)][AWS S3] is een service voor objectopslag die toonaangevende schaalbaarheid, beschikbaarheid van gegevens, beveiliging en prestaties biedt. De AWS S3-service gebruikt emmers, of containers, voor gegevensopslag. Voor deze configuratie moet u een _privé_ emmertje.

>[!WARNING]
>
>Adobe ontmoedigt het gebruik van openbare emmers ten zeerste omdat het een ernstig veiligheidsrisico vormt.

**Externe opslag inschakelen met de AWS S3-adapter**:

1. Meld u aan bij het Amazon S3-dashboard en maak een _privé_ emmertje.

1. Instellen [AWS IAM] rollen. U kunt ook toegang en geheime sleutels genereren.

1. Schakel de standaardopslag voor de database uit.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Vorm Handel om de privé emmer te gebruiken. Zie [Opties voor externe opslag](remote-storage.md#remote-storage-options) voor een volledige lijst van parameters.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Nginx configureren

Nginx vereist een extra configuratie om Authentificatie met uit te voeren `proxy_pass` richtlijn. Voeg de volgende proxygegevens toe aan de `nginx.conf` bestand:

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

Als u toegang en geheime sleutels in plaats van gebruikt [AWS IAM] rollen, moet u omvatten [`ngx_aws_auth` Nginx-module][ngx repo].

### Machtigingen

De S3-integratie is afhankelijk van de mogelijkheid om cacheafbeeldingen te genereren en op te slaan op het lokale bestandssysteem; daarom, omslagtoestemmingen voor `pub/media` en soortgelijke directory&#39;s zijn hetzelfde voor S3 als bij gebruik van lokale opslag.

### Bestandsbewerkingen

Het wordt ten zeerste aanbevolen [!DNL Commerce] bestandsadaptermethoden in de ontwikkeling van codering of extensie, ongeacht het type bestandsopslag. Gebruik geen native I/O-bewerkingen van PHP-bestanden, zoals `copy`, `rename` of `file_put_contents`, omdat S3-bestanden zich niet in het bestandssysteem bevinden. Zie [DriverInterface.php] voor codevoorbeelden.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
[DriverInterface.php]: https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18

---
title: Externe opslag voor handel in cloudinfrastructuur
description: Zie de richtlijnen voor het instellen van externe opslag voor Adobe Commerce op cloudinfrastructuur.
source-git-commit: 0653d90d92e264b62fcc648f2b1307c013e9be54
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Externe opslag configureren voor handel op Cloud-infrastructuur

Beginnen met de `ece-tools` pakket 2002.1.5, kunt u een omgevingsvariabele gebruiken om de module van de Verre Opslag toe te laten; de externe opslagmodule echter _beperkt_ ondersteuning voor Adobe Commerce op cloudinfrastructuur. Adobe kan de service voor opslagadapters van derden niet volledig oplossen.

## Omgevingsvariabele

De `REMOTE_STORAGE` de variabele wordt gebruikt tijdens [implementatiefase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) van een wolkeninfrastructuurproject.

### `REMOTE_STORAGE`

- **Standaard**—_Niet ingesteld_
- **Versie**—Handel 2.4.2 en hoger

Een _opslagadapter_ om mediabestanden op te slaan in een permanente, externe opslagcontainer met behulp van een opslagservice, zoals AWS S3. Schakel de module Externe opslag in om de prestaties van Cloud-projecten te verbeteren met complexe configuraties met meerdere servers die bronnen moeten delen. Hieronder ziet u een voorbeeld van configuratie voor externe opslag met de `.magento.env.yaml` bestand:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Variabele instellen met Cloud CLI

Stel de `REMOTE_STORAGE` variabele als een [variabele op milieuniveau](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) zodat bestanden niet worden gedeeld tussen productie-, staging- en integratieomgevingen. Door de variabelen op het niveau van de omgeving in te stellen, hebt u de flexibiliteit om alleen externe opslag te gebruiken in bepaalde omgevingen, zoals het gebruik van externe opslag in de integratieomgeving.

**De externe opslagvariabele toevoegen met de Cloud CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Hiermee maakt u een `REMOTE_STORAGE` variabele met de opgegeven JSON-configuratie. De `REMOTE_STORAGE` De variabele neemt een koord JSON om verre opslag te vormen. Hieronder ziet u een voorbeeld van JSON-configuratie.

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Nadat u de configuratie creeert en opstelt, zouden de plaatsingslogboeken informatie over de verre opslagconfiguratie moeten omvatten, bijvoorbeeld `INFO: Remote storage driver set to: "aws-s3"`

### Variabele instellen met projectwebinterface

Alternatief, kunt u de Interface van het Web van het Project gebruiken om de variabele aan het aangewezen milieu toe te voegen.

**Om de verre opslagvariabele toe te voegen gebruikend de Interface van het Web van het Project**:

1. In de _Projectwebinterface_ selecteert u de omgeving aan de linkerkant.

1. Klik op de knop **Omgeving configureren** pictogram.

1. In de _Omgeving configureren_ klik op de knop **Variabelen** tab.

1. Klikken **Variabele toevoegen**.

1. In de _Naam_ veld, Enter `env:REMOTE_STORAGE`

1. In de _Waarde_ in het veld, voegt u de JSON-configuratie toe.

1. Selecteren **JSON-waarde** en **Gevoelig**; deselecteren **Overerving door onderliggende omgevingen**.

1. Klikken **Variabele toevoegen**.

### Optionele verificatie gebruiken

De `key` en `secret` zijn optioneel. Wanneer u de variabele maakt, kunt u de `key` en `secret` door `sensitive` optie. Met deze instelling zijn de waarden niet zichtbaar in de webinterface. Zie [Zichtbaarheid variabele](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) in de _Handleiding Handel in Cloud-infrastructuur_.

Als u een andere authentificatiemethode wilt gebruiken, laat weg `key` en `secret` uit de JSON-configuratie. Vorm de alternatieve authentificatiemethode, en verifieer dat de server aan het S3 emmertje wordt gemachtigd.

### Externe opslag synchroniseren

Nadat u de externe opslagmodule hebt ingeschakeld, synchroniseert u de huidige mediabestanden naar de externe opslaglocatie.

**De synchronisatie starten**:

1. Gebruik SSH om u aan te melden bij de externe omgeving met geconfigureerde externe opslag.

1. Start de synchronisatie.

```bash
bin/magento remote-storage:sync 
```

## Snelle configuratie

Als u ervoor kiest om de oplossing voor externe opslag te gebruiken met een Adobe Commerce-project voor cloudinfrastructuur, gebruikt u de [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) richtsnoeren in de _Snel_ documentatie om ervoor te zorgen dat Fastly Image Optimization werkt met AWS S3.

Wees voorbereid met uw [Snelle referenties](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Bij Pro-projecten gebruikt u SSH om verbinding te maken met uw server en krijgt u de snelste referenties van de `/mnt/shared/fastly_tokens.txt` bestand. Staging- en productieomgevingen hebben unieke gegevens. U moet de geloofsbrieven voor elke milieu krijgen.

De externe opslag voor cloudprojecten blijven instellen met de volgende taken:

1. Een [Snelle ondersteuning voor integratie](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. VCL-logica maken voor [AWS S3-verificatie](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. VCL-logica maken voor [back-endverzoeken aan de AWS S3 bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).

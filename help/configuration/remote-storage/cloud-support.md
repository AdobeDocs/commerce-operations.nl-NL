---
title: Externe opslag voor Commerce op cloudinfrastructuur
description: Zie de richtlijnen voor het instellen van externe opslag voor Adobe Commerce op cloudinfrastructuur.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Externe opslag voor Commerce configureren op Cloud-infrastructuur

Beginnend met het `ece-tools` pakket 2002.1.5, kunt u een omgevingsvariabele gebruiken om de Verre module van de Opslag toe te laten; nochtans, heeft de Verre module van de Opslag _beperkte_ steun op Adobe Commerce op wolkeninfrastructuur. Adobe kan de service van de externe opslagadapter niet volledig oplossen.

## Omgevingsvariabele

De `REMOTE_STORAGE` variabele wordt gebruikt tijdens [ stelt fase ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=nl-NL) van een project van de wolkeninfrastructuur op.

### `REMOTE_STORAGE`

- **Gebrek** - _niet plaats_
- **Versie** - Commerce 2.4.2 en later

Vorm a _opslagadapter_ om media dossiers in een blijvende, verre opslagcontainer op te slaan gebruikend de opslagdienst, zoals AWS S3. Schakel de module Externe opslag in om de prestaties van Cloud-projecten te verbeteren met complexe configuraties met meerdere servers die bronnen moeten delen. Hieronder ziet u een voorbeeld van een configuratie voor externe opslag met behulp van het bestand `.magento.env.yaml` :

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

Plaats de `REMOTE_STORAGE` variabele als [ milieu-vlakke veranderlijke ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=nl-NL) zodat de dossiers niet tussen de Productie, het Opvoeren, en milieu&#39;s van de Integratie worden gedeeld. Door de variabelen op het niveau van de omgeving in te stellen, hebt u de flexibiliteit om alleen externe opslag te gebruiken in bepaalde omgevingen, zoals het gebruik van externe opslag in de integratieomgeving.

**om de verre opslagvariabele toe te voegen gebruikend Cloud CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Hierdoor wordt een `REMOTE_STORAGE` -variabele gemaakt met de opgegeven JSON-configuratie. De `REMOTE_STORAGE` -variabele gebruikt een JSON-tekenreeks om externe opslag te configureren. Hieronder ziet u een voorbeeld van JSON-configuratie:

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

Nadat u de configuratie en implementatie hebt gemaakt, moeten de implementatielogboeken informatie bevatten over de configuratie van de externe opslag, bijvoorbeeld `INFO: Remote storage driver set to: "aws-s3"`

### Variabele instellen met projectwebinterface

Alternatief, kunt u de Interface van het Web van het Project gebruiken om de variabele aan het aangewezen milieu toe te voegen.

**om de verre opslagvariabele toe te voegen gebruikend de Interface van het Web van het Project**:

1. In de _Interface van het Web van het Project_, selecteer het milieu van de linkerzijde.

1. Klik **vormen milieu** pictogram.

1. In _vorm Milieu_ mening, klik de **Variabelen** tabel.

1. Klik **toevoegen Variabele**.

1. Op het _gebied van de Naam_, ga `REMOTE_STORAGE` in

1. Op het _gebied van de Waarde_, voeg de configuratie JSON toe.

1. Selecteer **waarde JSON** en **Gevoelig**; schrap **Inheritable door kindmilieu&#39;s**.

1. Klik **toevoegen Variabele**.

### Optionele verificatie gebruiken

`key` en `secret` zijn optioneel. Wanneer u de variabele maakt, kunt u de opties `key` en `secret` verbergen door de optie `sensitive` te selecteren. Met deze instelling zijn de waarden niet zichtbaar in de webinterface. Zie [ Variabele zicht ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=nl-NL#visibility) in _Commerce op de gids van de Infrastructuur van de Wolk_.

Als u een andere verificatiemethode wilt gebruiken, laat u `key` en `secret` weg uit de JSON-configuratie. Vorm de alternatieve authentificatiemethode, en verifieer dat de server aan het S3 emmertje wordt gemachtigd.

### De externe opslag synchroniseren

Nadat u de externe opslagmodule hebt ingeschakeld, synchroniseert u de huidige mediabestanden naar de externe opslaglocatie.

**om de synchronisatie** te beginnen:

1. Gebruik SSH om u aan te melden bij de externe omgeving met geconfigureerde externe opslag.

1. Start de synchronisatie.

```bash
bin/magento remote-storage:sync 
```

## Snelle configuratie

Als u verkiest om de verre opslagoplossing met een Adobe Commerce op het project van de wolkeninfrastructuur te gebruiken, gebruik [ Amazon S3 ](https://docs.fastly.com/en/guides/amazon-s3) begeleiding in de _snelst_ documentatie om ervoor te zorgen dat de Snelle Optimalisering van het Beeld met AWS S3 werkt.

Ben voorbereid met uw [ Snelle geloofsbrieven ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL#get-fastly-credentials). Bij Pro-projecten gebruikt u SSH om verbinding te maken met uw server en de snelste referenties van het `/mnt/shared/fastly_tokens.txt` -bestand op te halen. Staging- en productieomgevingen hebben unieke gegevens. U moet de geloofsbrieven voor elke milieu krijgen.

De externe opslag voor cloudprojecten blijven instellen met de volgende taken:

1. Vorm de integratie van de a [ snel steunen ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Creeer logica VCL voor [ de authentificatie van AWS S3 ](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Creeer logica VCL voor [ achterste verzoeken aan het emmertje van AWS S3 ](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).

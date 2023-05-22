---
title: Overzicht van serviceconfiguratiepaden
description: Zie een lijst van de waarden van de de dienstenconfiguratie.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Overzicht van serviceconfiguratiepaden

In deze sectie worden de namen van variabelen en configuratiepaden weergegeven die beschikbaar zijn voor opties in de beheerdersruimte onder **Winkels** > Instellingen > **Configuratie** > **Services**.

De [`magento app:config:dump` command](../cli/export-configuration.md) deze waarden naar het gedeelde configuratiebestand schrijft, `app/etc/config.php`, die onder broncontrole moeten staan. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](override-config-settings.md#environment-variables). Dit onderwerp doet _niet_ list [gevoelige en systeemspecifieke waarden](config-reference-sens.md).

## Web API-paden voor handel

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Services** > **Web-API**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Standaardresponstekenreeks | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anonieme toegang voor gasten toestaan | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth-paden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Services** > **OAuth**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Levensduur klanttoken (uren) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur beheertoken (uren) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mogelijkheid tot opschonen | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth Consumer credentials HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth Consumer credentials HTTP Post timeout | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

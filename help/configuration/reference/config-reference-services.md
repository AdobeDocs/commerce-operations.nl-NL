---
title: Overzicht van serviceconfiguratiepaden
description: Meer informatie over serviceconfiguratiepaden en waarden vindt u in Adobe Commerce Admin-instellingen. Ontdek Web API, OAuth, en de configuratieopties van de de dienstintegratie.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Overzicht van serviceconfiguratiepaden

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **de Diensten** op.

Het [`magento app:config:dump` bevel &#x200B;](../cli/export-configuration.md) schrijft deze waarden aan het gedeelde configuratiedossier, `app/etc/config.php`, dat in broncontrole zou moeten zijn. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [&#x200B; de milieuvariabelen van het Gebruik om configuratiemontages &#x200B;](override-config-settings.md#environment-variables) met voeten te treden. Dit onderwerp __ lijst [&#x200B; niet gevoelige en systeem-specifieke waarden &#x200B;](config-reference-sens.md).

## Commerce Web API-paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Diensten** > **Web API**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Standaardresponstekenreeks | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anonieme toegang voor gasten toestaan | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Handmatige paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Diensten** > **OAuth**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Levensduur klanttoken (uren) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur beheertoken (uren) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mogelijkheid tot opschonen | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth Consumer credentials HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth Consumer credentials HTTP Post timeout | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

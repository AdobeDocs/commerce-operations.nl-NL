---
title: De cache beheren
description: Beheer geheim voorgeheugentypes en bekijk geheim voorgeheugenstatus van de bevellijn gebruikend Commerce CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# De cache beheren

{{file-system-owner}}

## Cachetypen

U kunt het Adobe Commerce-cachebeheersysteem gebruiken om de prestaties van uw site te verbeteren. Dit onderwerp verklaart hoe de beheerders of de ontwikkelaars van het Systeem met toegang tot de de toepassingsserver van de Handel geheime voorgeheugens van de bevellijn kunnen beheren.

>[!NOTE]
>
>
>De beheerders van de handelplaats kunnen het geheime voorgeheugen van Admin beheren gebruikend het hulpmiddel van het Systeem van het Beheer van het Geheime voorgeheugen. Zie [Cachebeheer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) in de _Admin Systems Guide_.


## De status van de cache weergeven

Van de bevellijn van de de toepassingsserver van de Handel, bekijk het statuut van het geheime voorgeheugen gebruikend `cache:status` Commerce CLI command.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Hieronder volgt een monster:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Voor een gedetailleerde beschrijving van de standaardcachetypen die door Adobe Commerce worden ondersteund, raadpleegt u [Cursussen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) in de _Admin Systems Guide_.


## Cachetypen in- of uitschakelen

Met deze opdracht kunt u alle cachetypen of alleen de door u opgegeven typen in- of uitschakelen. Het onbruikbaar maken van geheim voorgeheugentypes is nuttig tijdens ontwikkeling omdat u de resultaten van uw veranderingen ziet zonder het moeten het geheime voorgeheugen leegmaken; nochtans, heeft het onbruikbaar maken van geheim voorgeheugentypes een nadelig effect op prestaties.

>[!INFO]
>
>Beginnend in versie 2.2, kunt u geheim voorgeheugentypes slechts toelaten of onbruikbaar maken gebruikend de bevellijn terwijl het runnen van Handel op productiemodus. Als het runnen van Handel op ontwikkelaarwijze, kunt u geheim voorgeheugentypes toelaten of onbruikbaar maken gebruikend de bevellijn of manueel. Voordat u dit doet, moet u handmatig `<magento_root>/app/etc/env.php` schriftelijk door de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

U kunt schoonmaken (ook wel _flush_ of _vernieuwen_) gebruikt via de opdrachtregel of de beheerder.

Opdrachtopties:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Indien weggelaten `[type]` schakelt alle cachetypen tegelijkertijd in of uit. De `type` Deze optie is een lijst met cachetypen die door spaties worden gescheiden.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

U kunt als volgt cachetypen en hun status weergeven:

```bash
bin/magento cache:status
```

U kunt bijvoorbeeld de cache van de volledige pagina en de DDL-cache uitschakelen:

```bash
bin/magento cache:disable db_ddl full_page
```

Monsterresultaat:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Als u een cachetype inschakelt, wordt dat cachetype automatisch gewist.

>[!INFO]
>
>Vanaf versie 2.3.4 plaatst de Handel alle systeemEAV attributen in het voorgeheugen aangezien zij worden teruggewonnen. Op deze manier verbetert het in cache plaatsen van EAV-kenmerken de prestaties, omdat hierdoor minder aanvragen voor invoegen/selecteren naar de DB worden ingediend. Nochtans, verhoogt het ook de grootte van het geheim voorgeheugennetwerk. Ontwikkelaars kunnen aangepaste EAV-kenmerken in cache plaatsen door het `bin/magento config:set dev/caching/cache_user_defined_attributes 1` gebruiken. Dit kan ook worden gedaan bij de beheerder [Modus Ontwikkelaar](../bootstrap/application-modes.md) door instellen **Winkels** > Instellingen **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **Instellingen voor caching** > **Door gebruiker gedefinieerde kenmerken in cache opslaan** tot **Ja**.

## Cachetypen opschonen en leegmaken

>[!NOTE]
>
>Cache van meerdere pagina&#39;s kan tegelijkertijd en automatisch ongeldig worden gemaakt **_zonder_** deze entiteiten bewerken. Bijvoorbeeld wanneer een product in de catalogus is toegewezen aan een categorie of wanneer er een product in de catalogus is [!UICONTROL related product rule] wordt gewijzigd.

Als u verouderde items uit de cache wilt verwijderen, kunt u _schoon_ of _flush_ cachetypen:

- Het schoonmaken van een geheim voorgeheugentype schrapt alle punten van toegelaten het geheim voorgeheugentypes van de Handel slechts. Met andere woorden, deze optie beïnvloedt andere processen of toepassingen niet omdat het slechts het geheime voorgeheugen wist dat de Handel gebruikt.

  Uitgeschakelde cachetypen worden niet schoongemaakt.

  >[!TIP]
  >
  >Maak altijd de cache schoon nadat u versies van Adobe Commerce hebt bijgewerkt, een upgrade hebt uitgevoerd van Magento Open Source naar Adobe Commerce of B2B hebt geïnstalleerd voor Adobe Commerce of een willekeurige module.

- Als u een cachetype leegmaakt, wordt de cacheopslag gewist. Dit kan van invloed zijn op andere procestoepassingen die dezelfde opslag gebruiken.

Cachetypen leegmaken als u al geprobeerd hebt de cache te reinigen en er nog steeds problemen zijn die u niet kunt isoleren.

Opdrachtgebruik:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Wanneer `[type]` is een door spaties gescheiden lijst met cachetypen. Weglaten `[type]` Hiermee worden alle cachetypen tegelijk gewist of verwijderd. Als u bijvoorbeeld alle typen cache wilt leegmaken, voert u

```bash
   bin/magento cache:flush
```

Monsterresultaat:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>U kunt de cachetypen ook opschonen en leegmaken in de beheerfunctie. Ga naar **Systeem** > **Gereedschappen** > **Cachebeheer**. **Opslag in één cache** is gelijk aan `bin/magento cache:flush`. **Cache van Magento leegmaken** is gelijk aan `bin/magento cache:clean`.

---
title: De cache beheren
description: Cachetypen beheren en de cachestatus weergeven via de opdrachtregel met Commerce CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# De cache beheren

{{file-system-owner}}

## Cachetypen

U kunt het Adobe Commerce-cachebeheersysteem gebruiken om de prestaties van uw site te verbeteren. Dit onderwerp verklaart hoe de beheerders of de ontwikkelaars van het Systeem met toegang tot de de toepassingsserver van Commerce geheime voorgeheugens van de bevellijn kunnen beheren.

>[!NOTE]
>
>
>De beheerders van de handelplaats kunnen het geheime voorgeheugen van Admin beheren gebruikend het hulpmiddel van het Systeem van het Beheer van het Geheime voorgeheugen. Zie [ Beheer van het Geheime voorgeheugen ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) in de _Gids van Systemen Admin_.


## De status van de cache weergeven

Bekijk de status van de cache via de opdrachtregel van de Commerce-toepassingsserver via de `cache:status` Commerce CLI-opdracht.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Hieronder volgt een monster:

```
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
>Voor een gedetailleerde beschrijving van de standaardgeheim voorgeheugentypes die door Adobe Commerce worden gesteund, zie [ Caches ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) in de _Gids van Systemen Admin_.


## Cachetypen in- of uitschakelen

Met deze opdracht kunt u alle cachetypen of alleen de door u opgegeven typen in- of uitschakelen. Het onbruikbaar maken van geheim voorgeheugentypes is nuttig tijdens ontwikkeling omdat u de resultaten van uw veranderingen ziet zonder het moeten het geheime voorgeheugen leegmaken; nochtans, heeft het onbruikbaar maken van geheim voorgeheugentypes een nadelig effect op prestaties.

>[!INFO]
>
>Vanaf versie 2.2 kunt u castypen alleen in- of uitschakelen via de opdrachtregel terwijl Commerce in de productiemodus wordt uitgevoerd. Als u Commerce uitvoert in de ontwikkelaarsmodus, kunt u cachetypen in- of uitschakelen via de opdrachtregel of handmatig. Alvorens dit te doen, moet u `<magento_root>/app/etc/env.php` manueel schrijfbaar maken door de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).

U kunt (ook die als _wordt bedoeld flush_ of _verfrissen_) geheim voorgeheugentypes gebruikend of de bevellijn of Admin.

Opdrachtopties:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Wanneer u `[type]` weglaat, worden alle cavetypen tegelijkertijd in- of uitgeschakeld. De optie `type` is een lijst met cachetypen die door spaties worden gescheiden.

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

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Als u een cachetype inschakelt, wordt dat cachetype automatisch gewist.

>[!INFO]
>
>Vanaf versie 2.3.4 worden alle EAV-kenmerken van het systeem door Commerce in cache opgeslagen wanneer deze worden opgehaald. Op deze manier verbetert het in cache plaatsen van EAV-kenmerken de prestaties, omdat hierdoor minder aanvragen voor invoegen/selecteren naar de DB worden ingediend. Nochtans, verhoogt het ook de grootte van het geheim voorgeheugennetwerk. Ontwikkelaars kunnen aangepaste EAV-kenmerken in cache plaatsen door de opdracht `bin/magento config:set dev/caching/cache_user_defined_attributes 1` uit te voeren. Dit kan ook van Admin worden gedaan terwijl op [ wijze van de Ontwikkelaar ](../bootstrap/application-modes.md) door **Opslag** te plaatsen > de Configuratie van Montages **&#x200B;**&#x200B;> **Geavanceerd** > **Ontwikkelaar** > **Caching Montages** > **Gedefinieerde Gebruiker van het Geheime voorgeheugen Attributen** aan **ja**.

## Cachetypen opschonen en leegmaken

>[!NOTE]
>
>Het veelvoudige paginacache kan gelijktijdig en automatisch worden ongeldig gemaakt **_zonder_** deze entiteiten die uitgeven. Bijvoorbeeld wanneer een product in de catalogus wordt toegewezen aan een categorie of wanneer [!UICONTROL related product rule] wordt gewijzigd.

Om verouderde punten van het geheime voorgeheugen te zuiveren, kunt u __ schoonmaken of __ geheime voorgeheugentypes leegmaken:

- Als u een cachetype wist, worden alleen alle items van de ingeschakelde Commerce-cachetypen verwijderd. Met andere woorden, deze optie heeft geen invloed op andere processen of toepassingen omdat alleen de cache wordt gewist die door Commerce wordt gebruikt.

  Uitgeschakelde cachetypen worden niet schoongemaakt.

  >[!TIP]
  >
  >Maak altijd de cache schoon nadat u versies van Adobe Commerce hebt bijgewerkt, een upgrade van Magento Open Source naar Adobe Commerce hebt uitgevoerd of B2B voor Adobe Commerce of een willekeurige module hebt geïnstalleerd.

- Als u een cachetype leegmaakt, wordt de cacheopslag gewist. Dit kan van invloed zijn op andere procestoepassingen die dezelfde opslag gebruiken.

Cachetypen leegmaken als u al geprobeerd hebt de cache te reinigen en er nog steeds problemen zijn die u niet kunt isoleren.

Opdrachtgebruik:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Waar `[type]` een door spaties gescheiden lijst met cachemypen is. Als u `[type]` weglaat, worden alle cavetypen tegelijkertijd gewist of leeggemaakt. Als u bijvoorbeeld alle typen cache wilt leegmaken, voert u

```bash
   bin/magento cache:flush
```

Monsterresultaat:

```
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
>U kunt de cachetypen ook opschonen en leegmaken in de beheerfunctie. Ga naar **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**. **de Opslag van het Geheime voorgeheugen van de Duw** is gelijkwaardig aan `bin/magento cache:flush`. **het Geheime voorgeheugen van Magento van de Duw** is gelijkwaardig aan `bin/magento cache:clean`.

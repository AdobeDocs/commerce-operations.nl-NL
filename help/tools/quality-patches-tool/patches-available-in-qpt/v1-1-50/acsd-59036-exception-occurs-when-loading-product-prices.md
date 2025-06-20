---
title: 'ACSD-59036: Er treedt een uitzondering op bij het laden van productprijzen met zowel onderste als bovengrens ingesteld op $0'
description: Pas de ACSD-59036-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een uitzondering optreedt bij het laden van productprijzen waarbij zowel de onder- als de bovengrens is ingesteld op *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-59036: Een uitzondering treedt op wanneer het laden van productprijzen met zowel lagere als hogere grenzen die aan *$0* worden geplaatst

De ACSD-59036-patch verhelpt het probleem waarbij een uitzondering optreedt bij het laden van productprijzen met zowel lagere als hogere begrenzingen ingesteld op *$0* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59036. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een uitzondering komt voor wanneer het laden van productprijzen met zowel lagere als hogere grenzen die aan *worden geplaatst 0*.

Het probleem doet zich voor omdat het algoritme geen NULL-waarden verwerkt wanneer de query met prijsbereiken wordt geladen. Om dit te bevestigen, kunnen wij controleren als zowel de lagere als hogere waaiers ONGELDIG zijn, en als zij, een waarde van *0* voor beide grenzen toewijzen. Dit zou om het even welke fouten moeten verhinderen worden geworpen.

<u> Stappen om </u> te reproduceren:

1. Creeer *13* eenvoudige producten.
1. Wijs alle *13* producten aan een categorie toe.
1. Stel de prijs van één product in op *$1322,94* .
1. Stel de prijs van alle andere producten in op *$0* .
1. Configureer [!DNL OpenSearch] als een zoekprogramma.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** en plaats de **[!UICONTROL PLP]** telling aan *16*.
1. Plaats **[!UICONTROL Price Navigation Step Calculation]** aan *Automatisch (vergelijk producttellingen)*.
1. Voer de volledige redex uit.
1. Open de pagina *[!UICONTROL Category]* .

<u> Verwachte resultaten </u>:

Op de pagina *[!UICONTROL Category]* worden alle producten weergegeven.

<u> Ware resultaten </u>:

Er treedt een fout op:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

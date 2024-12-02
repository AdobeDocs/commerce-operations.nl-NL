---
title: 'MDVA-43983: De producten die als "Niet afzonderlijk zichtbaar"worden geplaatst verschijnen in onderzoeksresultaten'
description: Met de MDVA-43983-patch wordt het probleem opgelost waarbij de producten die als "Niet afzonderlijk zichtbaar" zijn ingesteld, nog steeds in de geavanceerde zoekresultaten van de catalogus worden weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: De producten die als &quot;Niet afzonderlijk zichtbaar&quot;worden geplaatst verschijnen in onderzoeksresultaten

Met de MDVA-43983-patch wordt het probleem opgelost waarbij de producten die als &quot;Niet afzonderlijk zichtbaar&quot; zijn ingesteld, nog steeds in de geavanceerde zoekresultaten van de catalogus worden weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De producten die als &quot;Niet afzonderlijk zichtbaar&quot;worden geplaatst verschijnen nog in catalogus geavanceerde onderzoeksresultaten.

<u> Stappen om </u> te reproduceren:

1. Creeer een attribuut met **Type van Invoer van de Catalogus voor de Eigenaar van de Opslag** als **Vervolgkeuzelijst** of **Visueel Staal** (bijvoorbeeld, Kleur).
1. Plaats **Gebruik in Onderzoek** als **ja** en **Zichtbaar in Geavanceerd Onderzoek** als **ja**.
1. Voeg enkele kenmerkopties toe.
1. Creeer producten met **Zichtbaarheid** als **niet Afzonderlijk** zichtbaar.
1. Opties voor het kenmerk Kleur toewijzen.
1. Ga naar de **Catalogus Geavanceerde pagina van het Onderzoek** op de storefront.
1. Selecteer alleen de optie Kleurkenmerk in het veld Kleurkenmerk en laat de rest van de velden leeg of ongewijzigd.
1. Verzend een geavanceerd zoekformulier.
1. Bekijk de zoekresultaten.

<u> Verwachte resultaten </u>:

Producten die zijn ingesteld als &quot;Niet afzonderlijk zichtbaar&quot;, worden niet weergegeven in de geavanceerde zoekresultaten van de catalogus.

<u> Ware resultaten </u>:

Producten die zijn ingesteld als &quot;Niet afzonderlijk zichtbaar&quot; worden weergegeven in de geavanceerde zoekresultaten van de catalogus.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

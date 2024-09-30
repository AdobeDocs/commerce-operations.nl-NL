---
title: 'ACSD-51700: Fout bij het schakelen tussen winkelweergaven op downloadbare pagina voor productbewerking.'
description: Pas de ACSD-51700-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een fout optreedt bij het schakelen tussen de winkelweergaven op een downloadbare productbewerkingspagina in de beheerder.
feature: Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700: fout bij het schakelen tussen winkelweergaven op de downloadbare pagina voor productbewerking

De ACSD-51700-patch verhelpt het probleem waarbij een fout optreedt bij het schakelen tussen de winkelweergaven op een downloadbare productbewerkingspagina in de beheerder. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51700. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

## Probleem

Er treedt een fout op wanneer wordt geschakeld naar een andere winkelweergave op een downloadbare productbewerkingspagina in de beheerder.

<u> Stappen om </u> te reproduceren:

1. Maak een downloadbaar product met een naam, [!DNL SKU] en prijs. Voeg geen koppelingen toe en sla het product op.
1. Schakel van alle winkelweergaven over naar de standaardwinkelweergave.
1. Maak een koppeling voor het downloadbare product en sla deze op.
1. Schakel van de standaardwinkelweergave naar alle winkelweergaven.

<u> Verwachte resultaten </u>:

De gekoppelde producten zijn zichtbaar.

<u> Ware resultaten </u>:

De volgende fout wordt weergegeven:

*Vervangen Functionaliteit: number_format (): Het overgaan van ongeldig tot parameter #1 ($num) van type float wordt afgekeurd in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php op lijn 228*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: "ACSD-48212: product import wijst product aan verkeerde bron toe"
description: Pas de ACSD-48212-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product door het importeren aan de verkeerde bron wordt toegewezen.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: bij het importeren van producten wordt een product aan de verkeerde bron toegewezen

De ACSD-48212-patch verhelpt het probleem waarbij het product door het importeren aan de verkeerde bron wordt toegewezen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48212. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt door het importeren aan de verkeerde bron toegewezen.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire inventarisbron.
1. Een product maken met alleen de standaardinventarisbron.
1. Het product exporteren.
1. Voer `bin/magento cron:run` uit.
1. Open **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]** .
1. Selecteer het product in het raster.
1. Wijs de toewijzing van de voorraad ongedaan met het menu *[!UICONTROL mass action]* .
1. Voer `bin/magento cron:run` uit.
1. Wijs de secundaire bron toe via het menu *[!UICONTROL mass action]* .
1. Voer `bin/magento cron:run` uit.
1. Verwijder het product via het menu *[!UICONTROL mass action]* .
1. Voer `bin/magento cron:run` uit.
1. Importeer het product met behulp van de eerder geëxporteerde CSV.
1. Controleer de brontoewijzing.

<u> Verwachte resultaten </u>:

Het product wordt alleen aan de standaardbron toegewezen.

<u> Ware resultaten </u>:

Het product wordt toegewezen aan zowel gebrek als secundaire bron.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

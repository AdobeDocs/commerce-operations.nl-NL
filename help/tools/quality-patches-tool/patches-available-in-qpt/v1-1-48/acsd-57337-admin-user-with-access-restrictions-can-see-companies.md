---
title: 'ACSD-57337: Admin-gebruiker met toegangsbeperkingen kan alle bedrijven bekijken in het *Companies*-raster'
description: Pas de ACSD-57337-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder met toegangsbeperkingen voor specifieke websites bedrijven kan bekijken vanaf alle websites in het *Companies*-raster.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: De gebruiker van Admin met toegangsbeperkingen kon alle bedrijven in het *net van 0} Bedrijven bekijken {*

Het ACSD-57337 flard lost de kwestie op waar een admin gebruiker met toegangsbeperkingen aan specifieke websites bedrijven van alle websites in het *Bedrijven* net kon bekijken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57337. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een admin gebruiker met toegangsbeperkingen aan specifieke websites kon bedrijven van alle websites in het *Bedrijven* net bekijken.

<u> Stappen om </u> te reproduceren:

1. Maak een aanvullende website, sla deze op en vergelijk deze.
1. Maak enkele bedrijven die zijn toegewezen aan verschillende websites.
1. Maak een beheerdersrol en stel het rolbereik in op de gemaakte website.
1. Creeer admin, en wijs het aan de gecreeerde rol toe.
1. Log in met een nieuwe beheerder.
1. Open **[!UICONTROL Customers]** > **[!UICONTROL Companies]** en bekijk de lijst met bedrijven.

<u> Verwachte resultaten </u>:

De bedrijven die aan de extra website zijn toegewezen zijn zichtbaar in het *netwerk van Bedrijven*.

<u> Ware resultaten </u>:

Alle bedrijven zijn zichtbaar in het *net van 0} Bedrijven {.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

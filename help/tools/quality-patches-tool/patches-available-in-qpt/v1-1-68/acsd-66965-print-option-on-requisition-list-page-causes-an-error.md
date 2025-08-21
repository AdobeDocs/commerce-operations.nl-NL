---
title: 'ACSD-66965: [!UICONTROL Print] -optie op [!UICONTROL Requisition List] -pagina veroorzaakt een fout'
description: Pas de ACSD-66965-patch toe om een probleem in Adobe Commerce op te lossen waarbij de optie [!UICONTROL Print] op de pagina [!UICONTROL Requisition List] een fout veroorzaakt.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: **[!UICONTROL Print]** -optie op **[!UICONTROL Requisition List]** -pagina veroorzaakt een fout

De ACSD-66965-patch verhelpt het probleem waarbij de optie **[!UICONTROL Print]** op de **[!UICONTROL Requisition List]** -pagina een fout veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66965. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**[!UICONTROL Print]** op de pagina **[!UICONTROL Requisition List]** veroorzaakt een fout vanwege een verwijzing naar een null-object in `Grid.php` .

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** .
1. Stel **[!UICONTROL Enable Company]** , **[!UICONTROL Enable Shared Catalog]** en **[!UICONTROL Enable Requisition List]** in op `Yes` .
1. Maak twee eenvoudige producten.
1. Meld u aan bij de winkel en open de pagina **[!UICONTROL My Account]** .
1. Maak een aanvraaglijst.
1. Wijs beide producten aan de aanvraaglijst toe.
1. Open de aanvraaglijst en maak een lijst van de producten.
1. Klik op **[!UICONTROL Print]**.

<u> Verwachte resultaten </u>:

Met de optie **[!UICONTROL Print]** op de pagina **[!UICONTROL Requisition List]** wordt de afdrukvoorvertoning zonder fouten weergegeven.

<u> Ware resultaten </u>:

Het volgende foutenbericht verschijnt: *een fout is voorgekomen tijdens toepassingslooppas. Zie uitzonderingslogboek voor details.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

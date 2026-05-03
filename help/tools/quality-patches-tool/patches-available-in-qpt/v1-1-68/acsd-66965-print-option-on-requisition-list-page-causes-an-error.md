---
title: 'ACSD-66965: [!UICONTROL Print] op de pagina veroorzaakt een fout[!UICONTROL Requisition List]'
description: Pas de ACSD-66965-patch toe om een probleem in Adobe Commerce op te lossen waarbij de optie [!UICONTROL Print] op de pagina [!UICONTROL Requisition List] een fout veroorzaakt.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: ccd0920a-074c-4851-a45a-09c43b04fe64
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-66965: **[!UICONTROL Print]** op de pagina veroorzaakt een fout **[!UICONTROL Requisition List]**

De ACSD-66965-patch verhelpt het probleem waarbij de optie **[!UICONTROL Print]** op de **[!UICONTROL Requisition List]** -pagina een fout veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66965. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

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
1. Klik op **[!UICONTROL Print]** .

<u> Verwachte resultaten </u>:

Met de optie **[!UICONTROL Print]** op de pagina **[!UICONTROL Requisition List]** wordt de afdrukvoorvertoning zonder fouten weergegeven.

<u> Ware resultaten </u>:

Het volgende foutbericht wordt weergegeven: *een fout is voorgekomen tijdens toepassingslooppas. Zie uitzonderingslogboek voor details.*

```text
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

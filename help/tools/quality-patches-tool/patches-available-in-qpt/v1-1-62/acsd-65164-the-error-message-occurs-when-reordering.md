---
title: 'ACSD-65164: Foutbericht bij opnieuw ordenen van configureerbaar product met één aangepaste optie voor selectievakje geselecteerd'
description: Pas de ACSD-65164-patch toe om het Adobe Commerce-probleem op te lossen waarbij het foutbericht *Sommige geselecteerde itemopties zijn momenteel niet beschikbaar* wanneer een configureerbaar product opnieuw wordt geordend met één geselecteerde aangepaste optie voor selectievakjes.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: Foutbericht bij opnieuw ordenen van configureerbaar product met één aangepaste optie voor selectievakje geselecteerd

ACSD-65164 flardfixes de kwestie waar het foutenbericht *sommige geselecteerde puntopties momenteel niet beschikbaar zijn* voorkomt wanneer het opnieuw ordenen van een configureerbaar product met één enkele geselecteerde checkbox douaneoptie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 wordt geïnstalleerd. De patch-id is ACSD-65164. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het opnieuw ordenen van een configureerbaar product met één enkele geselecteerde checkbox douaneoptie, keert het systeem een foutenmelding terug: *sommige geselecteerde puntopties zijn momenteel niet beschikbaar*.

### Stappen voor replicatie:

1. Ga in het deelvenster Beheer naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]** .
1. Onder **[!UICONTROL Customizable Options]**, voeg de optie van a *Checkbox* toe.
   * Plaats de checkbox optie als *Vereist*.
   * Voeg twee optiewaarden toe.
1. Navigeer aan de Storefront en login als geregistreerde klant.
1. Voeg het product aan de kar toe met één geselecteerde checkbox optie.
1. Ga naar **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]** .
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** om hetzelfde product toe te voegen.

**Verwachte Resultaten:**

Het product moet met succes aan het winkelwagentje worden toegevoegd.

**Ware Resultaten:**

Er wordt een foutbericht weergegeven:

*Kon niet het product met SKU &quot;24-MB01&quot;aan het winkelwagentje toevoegen: Sommige geselecteerde puntopties zijn momenteel niet beschikbaar.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

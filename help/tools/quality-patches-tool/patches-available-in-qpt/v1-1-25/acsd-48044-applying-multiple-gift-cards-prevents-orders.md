---
title: 'ACSD-48044: het toepassen van meerdere cadeaukaarten voorkomt dat orders worden geplaatst'
description: Pas de ACSD-48044-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het toepassen van meerdere cadeaukaarten op één bestelling met meerdere verzendingen ertoe leidt dat bestellingen niet kunnen worden geplaatst.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044: het toepassen van meerdere cadeaukaarten voorkomt dat orders worden geplaatst

De ACSD-48044-patch verhelpt het probleem dat het toepassen van meerdere cadeaukaarten op één bestelling met meerdere verzendingen ertoe leidt dat bestellingen niet kunnen worden geplaatst. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u meerdere cadeaukaarten op één bestelling met meerdere verzendingen toepast, kunnen geen bestellingen worden geplaatst.

<u> Stappen om </u> te reproduceren:

1. Installeer een schone versie van Adobe Commerce.
1. Maak een eenvoudig product met een prijs van $100 en een ander eenvoudig product met een prijs van $10.
1. Meld u aan bij [!UICONTROL Admin panel] en maak twee cadeaukaarten.

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $ 25

1. Maak een klant met twee adressen.
1. Voeg twee producten aan de kar toe.

   * Voeg eerst het product $10 toe en voeg vervolgens het product $100 toe. De uitgave kan niet worden gereproduceerd als eerst het product van $100 wordt toegevoegd.

1. Ga naar het winkelwagentje en voeg de twee cadeaukaarten toe die u hebt gemaakt.
1. Klik op **[!UICONTROL Ship to Multiple Addresses]** op de winkelwagentje pagina.
1. Wijs elk product aan een verschillend adres toe.
1. Ga naar de pagina **[!UICONTROL Shipping information]** .
1. Ga naar de pagina **[!UICONTROL Billing information]** .
1. Ga naar de pagina **[!UICONTROL Review Your Order]** waar u de uitgave kunt zien.
1. Plaats de bestelling.

<u> Verwachte resultaten </u>:

* Cadeaukaarten worden correct toegepast op het totale bedrag.
* Bestellingen worden geplaatst.

<u> Ware resultaten </u>:

Cadeaukaartbedragen worden gemengd met een fout *&quot;Corrigeer de code van de cadeaukaart.&quot;* wanneer u de volgorde plaatst.

* Eerste product:

   * Creditcard verwijderen (00GXM6SUGBLW) - $15.00
   * Cadeaukaart verwijderen (02KB8M0H0GRD) - $0,00

* Tweede product:

   * Creditcard verwijderen (00GXM6SUGBLW) - $ 25,00
   * Cadeaukaart verwijderen (02KB8M0H0GRD) - $ 35,00

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

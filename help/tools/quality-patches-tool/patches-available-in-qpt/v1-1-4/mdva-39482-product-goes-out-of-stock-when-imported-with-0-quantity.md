---
title: 'MDVA-39482: Het product is uit voorraad als het wordt geïmporteerd met de hoeveelheid ''0'' en de optie ''backorders'' ingeschakeld'
description: In de MDVA-39482 is bepaald dat het product uit de voorraad komt als het met "0"-hoeveelheid wordt ingevoerd als MSI en backorders zijn ingeschakeld en de drempel voor de uit-van-voorraad wordt ingesteld op een minwaarde. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MDVA-39482. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Data Import/Export, Orders, Products
role: Admin
exl-id: 9d705ebf-2372-4e59-b447-cdb5b0db32f4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: Het product is uit voorraad als het wordt geïmporteerd met de hoeveelheid &#39;0&#39; en de optie &#39;backorders&#39; ingeschakeld

In de MDVA-39482 is bepaald dat het product uit de voorraad komt als het met &quot;0&quot;-hoeveelheid wordt ingevoerd als MSI en backorders zijn ingeschakeld en de drempel voor de uit-van-voorraad wordt ingesteld op een minwaarde. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-39482. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product gaat uit voorraad als het wordt ingevoerd met &quot;0&quot; hoeveelheid wanneer MSI en backorders worden toegelaten en de Drempel van de Voorraad aan een minwaarde wordt geplaatst.

<u> Eerste vereisten </u>:

1. MSI- en voorbeeldgegevens moeten worden geïnstalleerd.
1. Ga naar **Opslag** > **Configuraties** > **Catalogus** > **Voorraad**:
   * Achterorden instellen op &quot;Aantal onder 0 toestaan&quot;
   * Drempel voor verstreken bestanden instellen op &quot;-10&quot;

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor SKU **in Voorraad** is en hoeveelheid **24-MB01** heeft.
1. Importeer de CSV van de voorraden. Zorg ervoor dat u &quot;Stock Sources&quot; selecteert in Type entiteit:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Controleer de voorraadstatus van het product nadat de voorraden zijn ingevoerd.

<u> Verwachte resultaten </u>:

24-MB01 is **in Voorraad** in Storefront.

<u> Ware resultaten </u>:

24-MB01 is **uit-van-voorraad** in Storefront.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.

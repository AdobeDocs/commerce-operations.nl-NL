---
title: 'MDVA-43232: Het sorteren van producten in visuele handelaar door Speciale Prijs aan Hoogste (of Onder) veroorzaakt een fout'
description: De patch MDVA-43232 verhelpt het probleem dat het sorteren van producten in visuele merchandiser door Special Price to Top (of Bottom) een fout veroorzaakt bij het opslaan van de categorie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232: Het sorteren van producten in visuele handelaar door Speciale Prijs aan Hoogste (of Onder) veroorzaakt een fout

De patch MDVA-43232 verhelpt het probleem dat het sorteren van producten in visuele merchandiser door Special Price to Top (of Bottom) een fout veroorzaakt bij het opslaan van de categorie. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als producten in visuele handelaren worden gesorteerd op Speciale prijs naar Boven (of Onder), treedt een fout op bij het opslaan van de categorie.

<u> Stappen om </u> te reproduceren:

1. Controleer of er twee websites zijn.
1. Navigeer aan **Opslag** > **Configuratie** > **Catalogus** > **Prijs** en plaats het Reikwijdte van de Prijs van de Catalogus = Website.
1. Opnieuw, navigeer aan **Slaat** > **Configuratie** > **Catalogus** > **Visuele Merchandiser** > **Zichtbare Attributen voor de Regels van de Categorie** > en voeg Speciale Prijs toe.
1. Maak een eenvoudig product en wijs de producten toe aan beide websites.
1. Voeg een speciale prijs toe aan het standaardbereik van het product.
1. Schakel over naar het bereik van de andere winkel en overschrijf zowel de prijs als de speciale prijs van dat product.
1. Voer een `catalog_product_price` redex uit.
1. Ga naar **Catalogus** > **Categorieën** en creeer een nieuwe categorie.
1. Voeg een categorieregel toe aan filterproducten met een speciale prijs.
1. Sla de categorie op.
1. Stel onder de sectie Producten in categorie Sorteervolgorde = Speciale prijs boven (of Onder) in.
1. Sla de rubriek opnieuw op.

<u> Verwachte resultaten </u>:

De categorie wordt zonder fouten opgeslagen.

<u> Ware resultaten </u>:

Er wordt een uitzondering gegenereerd:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

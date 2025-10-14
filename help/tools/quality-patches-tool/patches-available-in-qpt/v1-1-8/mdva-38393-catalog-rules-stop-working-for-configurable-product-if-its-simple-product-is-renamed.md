---
title: 'MDVA-38393: De regels van de Catalogus werken niet meer voor configureerbaar product als zijn eenvoudig product wordt hernoemd'
description: De patch MDVA-38393 verhelpt het probleem waarbij de catalogusregels niet meer werken voor een configureerbaar product als het eenvoudige product een andere naam krijgt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 is geïnstalleerd. De patch-id is MDVA-38393. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393: De regels van de Catalogus werken niet meer voor configureerbaar product als zijn eenvoudig product wordt hernoemd

De patch MDVA-38393 verhelpt het probleem waarbij de catalogusregels niet meer werken voor een configureerbaar product als het eenvoudige product een andere naam krijgt. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 geïnstalleerd is. De patch-id is MDVA-38393. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De regels van de catalogus werken niet meer voor een configureerbaar product als zijn eenvoudig product wordt hernoemd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met een bijbehorend eenvoudig product.
1. Maak een categorie.
1. Wijs slechts het configureerbare product aan de nieuwe categorie toe.
1. Nieuwe catalogusregels maken:
   * Voorwaarde = Categorie bevat \&lt;new category id>
   * Actie = 50% korting
   * Actief = Ja
1. Voer opnieuw index uit.
1. Controleer het configureerbare product op de frontend (de korting zou moeten worden toegepast).
1. Controleer de tabel `catalogrule_product` (het eenvoudige product moet een korting hebben).
1. Ga naar Admin en wijzig de naam van het eenvoudige product. Hiermee voegt u een record toe aan de tabel `catalogrule_product_cl` .
1. De uitsnede of de opdracht `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` uitvoeren.
1. Controleer de `catalogrule_product` tabel.

<u> Verwachte resultaten </u>:

Het configureerbare product heeft een korting.

<u> Ware resultaten </u>:

* De kortingsrecords die voor de eenvoudige producten zijn gemaakt, ontbreken in de tabel `catalogrule_product` .
* Het configureerbare product aan de voorzijde heeft de volledige originele prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

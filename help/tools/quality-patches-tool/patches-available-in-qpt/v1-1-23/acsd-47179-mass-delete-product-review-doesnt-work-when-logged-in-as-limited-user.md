---
title: 'ACSD-47179: het massaal verwijderen van productoverzichten werkt niet wanneer aangemeld als beperkte gebruikersrol'
description: Pas de ACSD-47179-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het massaal verwijderen van productoverzichten niet werkt wanneer u bent aangemeld als een beperkte gebruikersrol.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: het massaal verwijderen van productoverzichten werkt niet wanneer het programma als beperkte gebruikersrol wordt geopend

De ACSD-47179-patch verhelpt het probleem dat het massaal verwijderen van productoverzichten niet werkt wanneer u bent aangemeld als een beperkte gebruikersrol. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 wordt geïnstalleerd. De patch-id is ACSD-47179. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De massale schrapping van productoverzichten werkt niet wanneer het programma geopend als beperkte gebruikersrol.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire website.
1. Maak een gebruikersrol die beperkt is tot de secundaire website met volledige toestemming voor de volgende secties:
   * Catalogus
   * Klant
   * Marketing
1. Maak een product en wijs het toe aan de secundaire website.
1. Voeg twee recensies toe aan het product vanaf de voorzijde.
1. Meld u aan bij de [!DNL Commerce] Admin met behulp van de beperkte beheerder die zojuist is gemaakt.
1. Probeer verwijderde revisies in behandeling opnieuw te publiceren.

<u> Verwachte resultaten </u>:

Een beheerder met voldoende machtigingen kan het verwijderen van revisies in behandeling openbaar maken.

<u> Ware resultaten </u>:

U krijgt de volgende fout: _iets ging fout. Uitzondering die in support_report.log_ wordt geproduceerd

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

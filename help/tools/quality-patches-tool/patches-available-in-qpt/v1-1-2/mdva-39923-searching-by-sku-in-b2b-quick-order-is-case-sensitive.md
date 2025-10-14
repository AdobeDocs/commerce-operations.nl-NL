---
title: 'MDVA-39923: Onderzoek door SKU in B2B snelle orde functionaliteit is case-sensitive'
description: De patch MDVA-39923 verhelpt het probleem waarbij klanten een fout krijgen wanneer ze de bestelling via SKU doorzoeken in de functie voor snelle bestelling van B2B met een ander geval dan het geval waarin de naam wordt opgeslagen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39923. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923: Onderzoek door SKU in B2B snelle orde functionaliteit is case-sensitive

De patch MDVA-39923 verhelpt het probleem waarbij klanten een fout krijgen wanneer ze de bestelling via SKU doorzoeken in de functie voor snelle bestelling van B2B met een ander geval dan het geval waarin de naam wordt opgeslagen. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-39923. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het zoeken door SKU in B2B snelle orde functionaliteit is case-sensitive en toont een fout wanneer een verschillend geval wordt gebruikt dan waarmee SKU wordt bewaard.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Login aan admin en ga naar **Sporen** > **Configuratie** > **B2B**.
1. Laat **Gedeelde Catalogus** en **Snelle Orde** toe.
1. Een product maken met SKU in hoofdletters, bijvoorbeeld TEST20-1234
1. Wijs gecreeerd product aan de **Gedeelde Catalogus** toe.
1. Login als klant en klik op **Snelle Orde**.
1. Voer de SKU in kleine letters in, bijvoorbeeld test20-1234.

<u> Verwachte resultaten </u>:

Het product moet ongeacht het gebruikte geval worden gevonden.

<u> Ware resultaten </u>:

Het volgende foutenbericht wordt ontvangen: *1 product(en) vereist (en) uw aandacht*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

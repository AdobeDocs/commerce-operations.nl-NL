---
title: 'ACSD-63182: Fout bij het opslaan van een product na het dupliceren van een bundelproduct'
description: Pas de ACSD-63182-patch toe om het Adobe Commerce-probleem op te lossen wanneer een fout optreedt tijdens het opslaan van een product nadat een bundelproduct is gedupliceerd met MSI ingeschakeld.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182: Fout bij het opslaan van een product na het dupliceren van een bundelproduct

De ACSD-63182-patch verhelpt het probleem dat een eenvoudig product dat als bundeloptie wordt gebruikt, niet kan worden opgeslagen na de duplicatie van het bundelproduct. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63182. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op wanneer u een eenvoudig product opslaat dat wordt gebruikt als een bundeloptie nadat u het bundelproduct hebt gedupliceerd.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe MSI-bron en -voorraad.
1. Creeer twee eenvoudige producten: **p1** en **p2**.
1. Creeer een bundelproduct **b1** met **p1** en **p2** als gebundelde opties.
1. Bewerk het **bundelproduct b1** en klik *** [!UICONTROL Save and Duplicate] &#x200B;***.
1. Bewerk het **eenvoudige product p1** en klik **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

Het product wordt zonder fout opgeslagen.

<u> Ware resultaten </u>:

De volgende fout wordt weergegeven:
*Uitzondering: Punt (Magento\Catalog\Model\Product\Interceptor) met zelfde identiteitskaart &quot;XXX&quot;bestaat reeds.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

---
title: 'ACSD-66301: Het verplaatsen van producten van een bestelling naar het winkelwagentje in Commerce Admin leidt tot een verschil in hoeveelheid'
description: Pas de ACSD-66301-patch toe om het Adobe Commerce-probleem op te lossen, waarbij producten in het winkelwagentje van de klant niet worden verwijderd wanneer ze aan de bestelling worden toegevoegd.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 1e56c38713344b117ca3882861ced35e602b3239
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-66301: wanneer producten van een bestelling in Commerce Admin naar de winkelwagen worden verplaatst, komen de hoeveelheden niet overeen

De ACSD-66301-patch verhelpt het probleem waarbij het verplaatsen van producten van een bestelling naar het winkelwagentje in de Admin-pleister leidt tot een niet-overeenkomende hoeveelheid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66301. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p10, 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u producten van een bestelling terugbrengt naar het winkelwagentje in Commerce Admin, komen de hoeveelheden niet overeen.

<u> Stappen om </u> te reproduceren:

1. Maak een gebruiker via de winkel.
2. Voeg een product aan het winkelwagentje met hoeveelheid toe = *5*.
3. Ga naar het deelvenster Beheer en open de gebruikersaccount waar het product is toegevoegd.
4. Klik op **[!UICONTROL Create Order]**.
5. In het linkervenster kunt u de activiteiten van de klant bekijken, inclusief het toegevoegde product en aantal.
6. Voeg het product aan de orde toe.
7. Werk de hoeveelheid = *4* in de belangrijkste ordesectie bij.
8. Klik op **[!UICONTROL Update Items and Quantities]** .
9. Breng de geselecteerde items van de bestelling over naar het winkelwagentje van de klant.

<u> Verwachte resultaten </u>:

Product toegevoegd aan het winkelwagentje met de nieuwe hoeveelheid = *4*.

<u> Ware resultaten </u>:

Product toegevoegd aan het winkelwagentje met de oude hoeveelheid = *5*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

---
title: 'ACSD-57570: Oplossen voor beperkte toegang van gebruikers tot gedeelde catalogi'
description: Pas de ACSD-57570-patch toe om het Adobe Commerce-probleem te verhelpen waarbij een beperkte beheerder met toegang tot een bepaalde winkel niet consistent alle gedeelde catalogi kan bekijken die aan producten zijn toegewezen of klantgegevens kan opslaan, wat leidt tot systeeminconsistenties.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570: Oplossen voor beperkte toegang van gebruikers tot gedeelde catalogi

De ACSD-57570-patch verhelpt het probleem dat een beperkte beheerder met toegang tot een bepaalde winkel niet altijd alle gedeelde catalogi kan bekijken die aan producten zijn toegewezen of klantgegevens kan opslaan, wat leidt tot systeeminconsistenties. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-57570. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beperkte admin-gebruiker met toegang tot een bepaalde winkel kan niet altijd alle gedeelde catalogi zien of klanten opslaan, wat tot inconsistenties leidt. Bij meerdere winkels kan de beperkte beheerder geen nieuwe bedrijven of aangepaste gedeelde catalogi zien.

<u> Stappen om </u> te reproduceren:

1. Opslaan instellen in de volgende volgorde:
   * Maak een nieuwe website met de naam W2.
   * Maak een nieuwe winkelweergave voor de standaardwebsite.
   * Maak een nieuwe winkel met de naam W2S2 voor website W2.
   * Maak een nieuwe winkelweergave met de naam W2S2SV1 voor de winkel W2S2.
   * Maak nog een nieuwe winkelweergave met de naam W2S2SV2 voor de winkel W2S2.
   * Een bedrijf voor W2 maken.
1. Producten toewijzen:
   * Sommige producten alleen aan W1 toewijzen.
   * Sommige producten alleen aan W2 toewijzen.
   * Sommige producten toewijzen aan W1 en W2.
1. Maak een aangepaste gedeelde catalogus en wijs hieraan alle producten toe.
1. Creeer een rol van douaneadmin met toegang tot slechts **W2S2**, niet **W2**.
1. Wijs de beperkte admin-gebruiker toe aan de nieuwe aangepaste admin-rol.
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Toegang controleren:
   * Controleer welke bedrijven je kunt zien.
   * Controleer welke gedeelde catalogi u kunt zien.
   * Open de lijst met producten en controleer of u alle gedeelde catalogi kunt zien waaraan de producten zijn toegewezen.

<u> Verwachte resultaten </u>:

Het gedrag moet consistent zijn.

<u> Ware resultaten </u>:

Als u slechts één extra website, opslag, en opslagmening creeert, kan de beperkte admin gebruiker het bedrijf, de gedeelde catalogus, en beide gedeelde catalogi in de productlijst zien. Bij de bovenstaande instelling kan de beperkte beheerder het nieuwe bedrijf of de aangepaste gedeelde catalogus niet zien en wordt alleen de standaard gedeelde catalogus weergegeven in de productlijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

---
title: 'MDVA-41164: Kan bedrijf met de attributen van de douaneklanten niet opslaan of uitgeven'
description: Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: Kan bedrijf met de attributen van de douaneklanten niet opslaan of uitgeven

Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van welk type dan ook niet opslaan of bewerken.

<u> Eerste vereisten </u>:

B2B-module is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Laat Bedrijf in **opslag** > **Config** > **B2B Eigenschappen** toe.
1. Creeer een klantenattribuut in **Slaat** > **Attributen** > **Klanten** > **toevoegen Nieuw Attribuut**:
   * Invoertype: Bestand (bijlage)
   * Tonen in winkelcentrum: Ja
   * Sorteervolgorde: alle
   * Forms voor gebruik in: alles selecteren
1. Creeer een nieuw bedrijf in **Klanten** > **Bedrijven** > **voeg Nieuw Bedrijf** toe en upload een dossier voor de nieuwe hierboven gemaakte attributen.

<u> Verwachte resultaten </u>:

De gebruiker kan de creatie van het bedrijf voltooien en de gehechtheid wordt geupload zonder enige fout.

<u> Ware resultaten </u>:

* U krijgt een foutenmelding: *het iets ging verkeerd terwijl het bewaren van dossier.*
* Het logboek van de uitzondering bevat een verslag als het volgende:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.

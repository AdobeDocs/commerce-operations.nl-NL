---
title: 'MDVA-43091: Kan gebundeld product niet bestellen bij Admin'
description: De MDVA-43091-patch lost het probleem op waarbij gebruikers geen gebundeld product kunnen bestellen bij de Commerce Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 is geïnstalleerd. De patch-id is MDVA-43091. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: d2812f97-107c-4db9-93cc-7004344fcc95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43091: Kan gebundeld product niet bestellen bij Admin

De MDVA-43091-patch lost het probleem op waarbij gebruikers geen gebundeld product kunnen bestellen bij de Commerce Admin. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 geïnstalleerd is. De patch-id is MDVA-43091. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het proberen om tot gebundeld product van Admin opdracht te geven, werpt het de volgende fout: *u kunt geen decimale hoeveelheid voor dit product gebruiken.*

<u> Stappen om </u> te reproduceren:

1. Een schone Adobe Commerce installeren.
1. Maak twee eenvoudige producten.
1. Maak een gebundeld product met twee opties.
1. Maak een klantenaccount op de voorzijde.
1. Ga naar **Admin** > **Verkoop** > **Orden** > **creeer Nieuwe Orde**.
   * Selecteer de klantenaccount die u zojuist hebt gemaakt.
   * Probeer het gebundelde product aan de kar toe te voegen.

<u> Verwachte resultaten </u>:

Admin-gebruiker kan het product met één hoeveelheid toevoegen aan het winkelwagentje.

<u> Ware resultaten </u>:

De gebruiker Admin krijgt de volgende fout: *u kunt decimale hoeveelheid voor dit product niet gebruiken.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

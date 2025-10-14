---
title: 'ACSD-66093: de naamvelden van de gastklant staan e-mailinvoer toe die tot ongeldige bestelberichten leidt'
description: Pas de ACSD-66093-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mailadressen kunnen worden ingevoerd in de velden **[!UICONTROL First Name] ** en **[!UICONTROL Last Name] ** en een e-mail met een ongeldige orderbevestiging kunnen worden verzonden.
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093: de naamvelden van de gastklant staan e-mailinvoer toe die tot ongeldige bestelberichten leidt

De ACSD-66093-patch verhelpt het probleem dat e-mailadressen kunnen worden ingevoerd in de velden **[!UICONTROL First Name]** en **[!UICONTROL Last Name]** van de gastklant, wat resulteert in een e-mail met bevestiging van een ongeldige bestelling. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-66093. De kwestie is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p11

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailadressen kunnen worden ingevoerd in de velden **[!UICONTROL First Name]** en **[!UICONTROL Last Name]** van de gastklant. Dit heeft geleid tot een e-mail met bevestiging van de bestelling.

<u> Stappen om </u> te reproduceren:

1. Voeg producten aan de kar als gastklant toe.
2. Ga naar Afrekenen.
3. Vul het e-mailadres in met &quot;test1@gmail.co&quot;.
4. Vul **[!UICONTROL First Name]** met &quot;<test2@gmail.co>&quot;.
5. Vul **[!UICONTROL Last Name]** met &quot;<test3@gmail.co>&quot;.
6. Vul andere vereiste velden in.
7. Plaatsingsvolgorde.

<u> Verwachte resultaten </u>:

Validatieberichten moeten worden weergegeven om aan te geven dat de velden **[!UICONTROL First Name]** en **[!UICONTROL Last Name]** niet geldig zijn, zoals *Voornaam ongeldig is! en Achternaam is ongeldig!* en de volgorde mag niet worden geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt geplaatst.
**[!UICONTROL First Name]** - en **[!UICONTROL Last Name]** -velden worden opgeslagen als ingevoerde velden.
Bevestigingsbericht voor bestelling wordt verzonden naar alle drie e-mails: test1@gmail.co, test2@gmail.co en test3@gmail.co.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

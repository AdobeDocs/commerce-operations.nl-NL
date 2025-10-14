---
title: 'MDVA-43859: Fout "Geen dergelijke entiteit met customerId ="het programma wordt geopend wanneer de geschrapte klant het programma opent'
description: De patch MDVA-43859 lost het probleem op waar fout *No zulk een entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859: Fout &quot;Geen dergelijke entiteit met customerId =&quot;het programma wordt geopend wanneer de geschrapte klant het programma opent

Het flard MDVA-43859 bevestigt de kwestie waar de fout *geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount aan de voorzijde.
1. Meld u af en meld u aan bij de klantenaccount die u in stap 1 hebt gemaakt.
1. Laad de backend in een andere browser en ga naar het klantenraster.
1. Verwijder de klant die u in stap 1 hebt gemaakt.
1. Ga terug naar de eerste browser en probeer u af te melden.

<u> Verwachte resultaten </u>:

De klant wordt zonder fout omgeleid naar de aanmeldingspagina.

<u> Ware resultaten </u>:

De klant krijgt de volgende fout: *geen dergelijke entiteit met customerId =*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

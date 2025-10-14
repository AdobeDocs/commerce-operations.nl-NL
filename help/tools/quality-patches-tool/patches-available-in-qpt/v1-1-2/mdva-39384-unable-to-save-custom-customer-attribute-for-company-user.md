---
title: 'MDVA-39384: Onbekwaam om douanekenmerk van de klant voor bedrijfgebruiker te bewaren'
description: De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: Onbekwaam om douanekenmerk van de klant voor bedrijfgebruiker te bewaren

De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepast klantkenmerk voor een bedrijfsgebruiker wordt niet opgeslagen.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > Montages > **Configuratie** > **Eigenschappen B2B** en plaats **toelaten Bedrijf** aan ja.
1. Een aangepast klantkenmerk maken:
   * Vereiste waarden: Ja (optioneel, inschakelen zodat de validatiefout wordt weergegeven).
   * Tonen in winkelcentrum: Ja.
   * Forms to Use In: All available in the list.
1. Creeer een Bedrijf en login als bedrijfadmin.
1. Navigeer naar de bedrijfsstructuur in uw account.
1. Klik op **toevoegen Gebruiker** verbinding.
1. Vul het formulier met het aangepaste kenmerk.
1. Klik **sparen**.

<u> Verwachte resultaten </u>:

De waarden van de douanekenmerken worden bewaard met de nieuwe bedrijfgebruiker.

<u> Ware resultaten </u>:

De waarden van de douanekenmerken worden NIET bewaard met de nieuwe bedrijfgebruiker.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

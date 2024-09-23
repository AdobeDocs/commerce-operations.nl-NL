---
title: 'MDVA-39384: Kan aangepast kenmerk van klant niet opslaan voor zakelijke gebruiker'
description: De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: Onbekwaam om douanekenmerk van de klant voor bedrijfgebruiker te bewaren

De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

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

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

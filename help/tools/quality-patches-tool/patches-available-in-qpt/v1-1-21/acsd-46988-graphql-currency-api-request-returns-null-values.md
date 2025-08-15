---
title: 'ACSD-46988: GraphQL API-aanvraag retourneert null-waarden'
description: De ACSD-46988-patch verhelpt het probleem waarbij de GraphQL API-aanvraag null-waarden retourneert voor een aangepaste valuta. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46988. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988: GraphQL API-aanvraag retourneert null-waarden

De ACSD-46988-patch verhelpt het probleem waarbij de GraphQL API-aanvraag null-waarden retourneert voor een aangepaste valuta. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 wordt geïnstalleerd. De patch-id is ACSD-46988. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aanvraag voor API voor GraphQL-valuta retourneert null-waarden voor een aangepaste valuta.

<u> Stappen om </u> te reproduceren:

1. Aangepaste valuta configureren in de Admin. Ga naar **Systeem** > **Configuratie** > **Algemeen** > **Opstelling van de Valuta**.
1. Verzend een GraphQL-aanvraag met de volgende payload:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u> Verwachte resultaten </u>:

De aanvraag retourneert valutawaarden in plaats van null-waarden.

<u> Ware resultaten </u>:

De aanvraag retourneert meerdere null-waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Hulpmiddelen van het Patroon van de Kwaliteit > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de gids van het Hulpmiddel van het Patroon van de Kwaliteit.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

Voor gebruikers ter plaatse:

* Uitvoeren: `composer require symfony/intl:"~5.4.11"`

Voor gebruikers van Cloud:

* Uitvoeren: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` - en `composer.lock` -bestanden samen met het patchbestand naar de opslagplaats.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.

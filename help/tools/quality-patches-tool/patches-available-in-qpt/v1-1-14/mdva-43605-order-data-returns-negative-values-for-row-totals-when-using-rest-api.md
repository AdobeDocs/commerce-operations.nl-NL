---
title: 'MDVA-43605: De gegevens van de orde keren negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API'
description: De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605: De gegevens van de orde keren negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API

De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ordegegevens geven negatieve waarden voor rijtotalen weer bij gebruik van de Rest API.

<u> Stappen om </u> te reproduceren:

1. Gratis verzending inschakelen.
1. Navigeer aan **Configuratie** > **Catalogus** > **Prijs** > en plaats het Reikwijdte van de Prijs van de Catalogus = Website.
1. Navigeer aan **Configuratie** > **Verkoop** > **Belasting** en update:
   * Belastingklasse voor verzending = belastbare goederen
   * Berekeningsinstellingen:
      * Catalogusprijs = inclusief belasting
      * Verzendprijs = inclusief prijs
      * Korting op prijzen toepassen = inclusief belasting
   * Weergave-instellingen prijs: inclusief belasting (alle velden)
   * Weergave-instellingen voor winkelwagentje: inclusief BTW (alle velden)
   * Orders, facturen, creditnota&#39;s:
      * Verzendbedrag weergeven = inclusief btw
1. Maak een belastingtarief voor de VS (staat = &#39;*&#39;), tarief percentage = 24,00
1. Maak een belastingregel met bovenstaande BTW-tarief.
1. Maak een regel voor de winkelwagenprijs met een specifieke coupon en een korting = $50 van het vaste bedrag voor de hele winkelwagen.
1. Maak vier producten met de volgende prijzen: $ 8,90, $ 5,90, $ 6,90 en $ 5,95.
1. Maak een beheerdersvolgorde met vier van deze producten met behulp van de couponcode die in de vorige stap is gemaakt. Gebruik de gratis verzending.
1. Betaling is niet vereist omdat de couponcode het carttotaal dekt.
1. Haal de orde op die enkel via Rest API eindpunt werd gecreeerd:

   ```json
   GET rest/V1/orders/1
   ```

<u> Verwachte resultaten </u>:

De waarden van `base_row_total` en `base_row_total_incl_tax` in de reactie zijn nul.

<u> Ware resultaten </u>:

De velden `base_row_total` en `base_row_total_incl_tax` in het antwoord hebben negatieve waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

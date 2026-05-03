---
title: 'ACSD-54680: B2B Citaat voor een product met Veelvoudige Toegewezen Bronnen kan worden verwerkt'
description: Pas de ACSD-54680-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het B2B-citaat voor een product met Meerdere toegewezen bronnen niet kan worden verwerkt.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# ACSD-54680: B2B Citaat voor een product met Veelvoudige Toegewezen Bronnen kan niet worden verwerkt.

De ACSD-54680-patch verhelpt het probleem waarbij het B2B-citaat voor een product met Meerdere toegewezen bronnen niet kan worden verwerkt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54680. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

B2B Citaat voor een product met Veelvoudige Toegewezen Bronnen kan niet worden verwerkt.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** en maak twee nieuwe bronnen: **Source 1** en **Source 2**.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** en maak een nieuwe voorraad: **Beeld A**, wijs het aan de belangrijkste website toe, en wijs **Source 1** en **Source 2** aan het toe.
1. Creeer een Eenvoudig product, wijs **Source 1** en **Source 2** toe, en plaats Qty = *2* voor elke bron. (de verkoopbare hoeveelheid van het product zou *4* als resultaat moeten zijn).
1. Maak een bedrijfsaccount.
1. Ga naar **[!UICONTROL Storefront]** en meld u aan bij de bedrijfsaccount.
1. Voeg het eenvoudige product aan het winkelwagentje met hoeveelheid toe = *4*.
1. Open *[!UICONTROL Shopping cart]* en klik op **[!UICONTROL Request a quote]** knop.
1. Voeg een opmerking en aanhalingsteken toe en klik op **[!UICONTROL Send a Request]** .
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** .
1. Onlangs verzonden offerte openen.

<u> Verwachte resultaten </u>:

De vermelde items bevatten het geordende product.

<u> Ware resultaten </u>:

De pagina-sectie met items waarnaar wordt verwezen, is leeg en het is niet mogelijk om het aanhalingsteken te verwerken.
`var/log/system.log` contains

```text
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

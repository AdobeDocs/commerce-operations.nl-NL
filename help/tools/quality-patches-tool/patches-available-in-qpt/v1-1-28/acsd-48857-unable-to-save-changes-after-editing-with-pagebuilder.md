---
title: ACSD-48857 Kan wijzigingen niet opslaan na bewerken met  [!DNL Page Builder]
description: Pas de ACSD-48857-patch toe om het Adobe Commerce-probleem op te lossen waarbij de gebruiker na het bewerken met  [!DNL Page Builder] geen wijzigingen kan opslaan.
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-48857 Kan wijzigingen niet opslaan na bewerking met [!DNL Page Builder]

De ACSD-48857-patch verhelpt het probleem waarbij de gebruiker na het bewerken met [!DNL Page Builder] geen wijzigingen kan opslaan. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-48857. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruiker kan geen wijzigingen opslaan na bewerking met [!DNL Page Builder] .

<u> Stappen om te reproduceren </u>

1. Meld u aan bij de beheerwebsite.
1. Navigeer naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** om een lege CMS-pagina te maken.
1. Voer dit SQL-script uit om de volgende **[!UICONTROL Content]** -veldwaarde in te stellen:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Ga terug naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** in Admin.
1. Bewerk de pagina.
1. Ga naar de tab **[!UICONTROL Content]** .
1. Klik op **[!UICONTROL Save]** .

<u> Verwachte resultaten </u>

HTML-inhoudsontsmetting is geïmplementeerd. Hiermee verwijdert u [!DNL Page Builder] gereserveerde HTML-kenmerken uit inhoud die is gegenereerd door de teksteditor.

<u> Ware resultaten </u>

De pagina blijft niet opgeslagen en de lader blijft draaien. In de console, wordt de volgende fout geproduceerd:

```ini
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

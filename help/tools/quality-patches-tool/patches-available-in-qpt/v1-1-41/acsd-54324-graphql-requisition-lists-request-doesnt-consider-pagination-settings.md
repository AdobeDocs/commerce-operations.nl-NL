---
title: 'ACSD-54324: Aanvraag_lijstverzoek van GraphQL neemt pagineringsmontages niet in overweging'
description: Pas het ACSD-54324 flard toe om de kwestie van Adobe Commerce te bevestigen waar het GraphQL &grave; requisition_lists' verzoek pagineringsmontages niet overweegt en alle resultaten terugkeert.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` -aanvraag houdt geen rekening met pagineringsinstellingen

De ACSD-54324-patch verhelpt het probleem dat in de GraphQL `requisition_lists` -aanvraag geen aandacht wordt besteed aan pagineringsinstellingen en retourneert alle resultaten. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-54324. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL `requisition_lists` -aanvraag houdt geen rekening met pagineringsinstellingen en retourneert alle resultaten.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Beheer en navigeer naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** .

   * Plaats *[!UICONTROL Enable Requisition List]* aan *ja*.

1. Meld u aan bij de voorzijde en ga naar **[!UICONTROL My Requisition Lists]** in het bovenste menu of vanuit **[!UICONTROL My Account]** en maak meerdere aanvragen (bijvoorbeeld: 7).
1. Nadat u een klanttoken hebt gegenereerd, voert u de onderstaande GraphQL `requisition_lists` -query voor de klant uit.

   * Zorg ervoor dat het paginaformaat kleiner is dan het totale aantal aanvraaglijsten dat u hebt gemaakt (voorbeeld: 4)

   ```graphql
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. De waarde van het veld `total_count` geeft 7 weer, terwijl de waarde 4 moet worden weergegeven.

   Het aantal punten toont ook 7 wanneer het het zelfde als de *paginagrootte* zou moeten zijn.

<u> Verwachte resultaten </u>:

* Het aantal dat als *wordt vermeld paginagrootte* is teruggekeerd onder `total_count` en niet het totale aantal verslagen.
* Het aantal punten is het zelfde als de *paginagrootte*.

<u> Ware resultaten </u>:

Het totale aantal verslagen is teruggekeerd onder `total_count`, zelfs als *paginagrootte* wordt vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

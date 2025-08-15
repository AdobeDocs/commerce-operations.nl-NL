---
title: 'ACSD-50234: Onjuiste naam van klant in bevestigingsbericht voor geplaatste bestellingen met  [!DNL PayPal]'
description: Pas de ACSD-50234-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de naam van de klant onjuist wordt weergegeven in het bevestigingsbericht voor orders die met  [!DNL PayPal] zijn geplaatst.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: Onjuiste naam van klant in bevestigingsbericht voor via [!DNL PayPal] geplaatste bestellingen

De ACSD-50234-patch verhelpt het probleem waarbij de naam van de klant onjuist wordt weergegeven in het bevestigingsbericht voor bestellingen die zijn geplaatst met [!DNL PayPal] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-50234. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bevestigingsbericht voor orders die met [!DNL PayPal] zijn geplaatst, toont de verkeerde naam van de klant.

<u> Stappen om te reproduceren </u>

1. Schakel **[!UICONTROL PayPal Express Checkout]** in.
1. Navigeer als gast naar de voorzijde.
1. Voeg producten toe aan de kar.
1. Afhandeling met **[!UICONTROL PayPal Express Checkout]** als betalingsmethode.
1. Controleer het bevestigingsbericht voor bestelling.

<u> Verwachte resultaten </u>

Het bevestigingsbericht voor de bestelling, het e-mailbericht voor de factuur en alle e-mails over de verzending worden naar de naam van de klant verzonden.

<u> Ware resultaten </u>

De de bevestiging e-mail van de orde, factuur e-mail, en alle op verzending betrekking hebbende e-mails worden gericht aan *Gast*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-49849: e-mail van de klant is vervangen door PayPal-e-mail'
description: Pas de ACSD-49849-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de e-mail van de klant is vervangen door PayPal-e-mail bij het plaatsen van een bestelling met PayPal Express via GraphQL.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849: e-mail van de klant wordt vervangen door [!DNL PayPal] e-mail

De ACSD-49849-patch verhelpt het probleem waarbij de e-mail van een klant wordt vervangen door een [!DNL PayPal's] -e-mail wanneer een bestelling wordt geplaatst met [!DNL PayPal Express] via GraphQL. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49849. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De e-mail van een klant wordt vervangen door een [!DNL PayPal's] -e-mail wanneer een bestelling wordt geplaatst bij [!DNL PayPal Express] via GraphQL.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]** .
1. Schakel [!DNL PayPal Express] in en configureer deze en stel **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** in.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en maak een eenvoudig product.
1. Voltooi het uitchecken door de gast met GraphQL. Voor meer, verwijs naar het [ GraphQL controleles ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in de Documentatie van de Ontwikkelaar van Adobe Commerce.
1. Gebruik [!DNL PayPal Express] als betalingsmethode.
1. Neem nota van e-mail u in de stap gebruikte waar u [ opstelling uw e-mail voor het karretje ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) in de Documentatie van de Ontwikkelaar van Adobe Commerce.
1. Nadat de bestelling is geplaatst, gaat u naar Adobe Commerce Admin en controleert u het e-mailbericht in de gemaakte bestelling.

<u> Verwachte resultaten </u>:

Het e-mailadres is hetzelfde als dat is ingesteld tijdens het uitchecken.

<u> Ware resultaten </u>:

De e-mailset die tijdens het uitchecken is ingesteld, wordt overschreven door de e-mailset in de [!DNL PayPal] -account.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

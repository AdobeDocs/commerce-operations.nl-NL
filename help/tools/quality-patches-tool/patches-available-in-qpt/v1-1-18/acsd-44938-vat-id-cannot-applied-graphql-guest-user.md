---
title: 'ACSD-44938: VAT_ID kan niet in  [!DNL GraphQL]  verzoek voor gastgebruiker worden toegepast'
description: ACSD-44938 flardfixes de kwestie waar &grave; VAT_ID &grave; niet in a  [!DNL GraphQL]  verzoek voor een gastgebruiker kan worden toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 is geïnstalleerd. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 3fdefc6201714c441d63574d293863e83205894b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kan niet worden toegepast in [!DNL GraphQL] -aanvraag voor gastgebruiker

De ACSD-44938-patch verhelpt het probleem dat `VAT_ID` niet kan worden toegepast in een [!DNL GraphQL] -aanvraag voor een gastgebruiker. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 geïnstalleerd is. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`VAT_ID` kan niet worden toegepast in een [!DNL GraphQL] -aanvraag voor een gastgebruiker.

<u> Stappen om </u> te reproduceren:

1. Volg de stappen die in het [[!DNL GraphQL]  worden vermeld&rbrace; leerprogramma ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in onze ontwikkelaarsdocumentatie worden vermeld om een gastkarretje tot stand te brengen.
1. Probeer `VAT_ID` voor de gastgebruiker toe te passen met [!DNL GraphQL] .

<u> Verwachte resultaten </u>:

`VAT_ID` kan op dezelfde manier worden toegepast als voor een geregistreerde klant. Zie het artikel [`createCustomerAddress` mutatie ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) in onze ontwikkelaarsdocumentatie.

<u> Ware resultaten </u>:

`VAT_ID` kan niet worden toegepast voor een gastgebruiker die [!DNL GraphQL] gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

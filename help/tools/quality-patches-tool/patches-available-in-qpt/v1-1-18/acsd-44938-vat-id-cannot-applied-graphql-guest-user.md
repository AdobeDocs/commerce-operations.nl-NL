---
title: 'ACSD-44938: VAT_ID kan niet worden toegepast in GraphQL-aanvraag voor gastgebruiker'
description: De ACSD-44938-patch verhelpt het probleem dat de VAT_ID niet kan worden toegepast in een GraphQL-aanvraag voor een gastgebruiker. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 is geïnstalleerd. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kan niet worden toegepast in GraphQL-verzoek voor gastgebruiker

De ACSD-44938-patch verhelpt het probleem dat de VAT_ID niet kan worden toegepast in een GraphQL-aanvraag voor een gastgebruiker. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 geïnstalleerd is. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

VAT_ID kan niet worden toegepast in een GraphQL-aanvraag voor een gastgebruiker.

<u> Stappen om </u> te reproduceren:

1. Volg de stappen in de [ zelfstudie van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-shopping-cart.html) in onze ontwikkelaarsdocumentatie worden vermeld om een gastkarretje tot stand te brengen die.
1. Probeer met GraphQL BTW-ID toe te passen op de gastgebruiker.

<u> Verwachte resultaten </u>:

VAT_ID kan op dezelfde manier worden toegepast als voor een geregistreerde klant. Zie [ createCustomerAddress mutation ](https://developer.adobe.com/commerce/webapi/graphql/mutations/create-customer-address.html) artikel in onze ontwikkelaarsdocumentatie.

<u> Ware resultaten </u>:

VAT_ID kan niet worden toegepast op een gastgebruiker die GraphQL gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

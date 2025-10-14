---
title: 'ACSD-49737: coupon wordt onjuist gemarkeerd als gebruikt na een mislukte kaartbetaling'
description: Pas de ACSD-49737-patch toe om de Adobe Commerce-uitgave te corrigeren waarbij de coupon onjuist is gemarkeerd als gebruikt na een mislukte kaartbetaling.
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737: De coupon wordt verkeerd gemerkt zoals *gebruikt* na een ontbroken kaartbetaling

ACSD-49737 flardfixes de kwestie waar de coupon verkeerd als *wordt gemerkt gebruikt* na een ontbroken kaartbetaling. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-49737. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De coupon wordt verkeerd gemerkt zoals *gebruikt* na een ontbroken kaartbetaling.

<u> Eerste vereisten </u>:

1. Configureer de methode **[!UICONTROL Braintree sandbox payment]** .
1. Zorg ervoor de {[** consument 0} sales.rule.update.coupon.usage opstelling en lopend is.](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=nl-NL)

<u> Stappen om </u> te reproduceren:

1. Maak een **[!UICONTROL Cart Price Rule]** met automatisch gegenereerde couponcodes.
1. Meld u aan als klant.
1. Product(en) toevoegen aan de kar.
1. Pas een automatisch gegenereerde couponcode toe.
1. Probeer een bestelling te plaatsen met een mislukte betaling.
1. Controleer het gebruik van de coupon in de **[!UICONTROL Cart Price Rule]** onder het tabblad **[!UICONTROL Manage Coupon Codes]** .

<u> Verwachte resultaten </u>:

Coupon zou niet als *gebruikt* moeten worden gemarkeerd als de betaling wordt ontbroken.

<u> Ware resultaten </u>:

* De code van de coupon zegt - gebruikt: *ja*, Gebruikte Tijden: *1*
* Couponcode is alleen geldig voor eenmalig gebruik.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

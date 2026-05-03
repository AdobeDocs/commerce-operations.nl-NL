---
title: 'ACSD-66149: IPN-handler retourneert *500* voor niet-ondersteunde typen'
description: Pas ACSD-66149 flard toe om de kwestie van Adobe Commerce te bevestigen waar de manager IPN niet gesteunde of onbekende types van IPN negeert, die de kwestie veroorzaken niet worden geregistreerd, het proces onderbreken, en ook een 500 fout terugkeren.
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-66149: De manager van IPN keert *500* voor niet gesteunde types terug

De ACSD-66149-patch verhelpt het probleem waarbij de IPN-handler (Instant Payment Notification) een fout van 500 retourneert voor niet-ondersteunde of onbekende IPN-typen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66149. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De kwestie is de manager IPN keert a *500* fout voor niet gestaafde of onbekende types IPN terug. Dit gebeurt wanneer Paypal IPN verzendt terwijl sommige velden ontbreken.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepaste module die alle soorten onbekende IPN-typen van PayPal emuleert.
1. Maak ten minste één product.
1. Configureer PayPal Express met uw eigen gegevens.
1. Plaats een bestelling met PayPal Express.
1. Voer de PayPal-emulator uit.

<u> Verwachte resultaten </u>:

De toepassingIPN manager negeert onjuiste types IPN en produceert niet *500* fouten:

`Order 000000001: Status processing — HTTP 500`

<u> Ware resultaten </u>:

De toepassing produceert vele *500* fouten tijdens verwerking onjuiste IPNs en verwerkt sporadisch geen sommige orden als de verwachte gebieden afwezig zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] hulplijn
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de gids van de Infrastructuur van Commerce op de Wolk toe

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen

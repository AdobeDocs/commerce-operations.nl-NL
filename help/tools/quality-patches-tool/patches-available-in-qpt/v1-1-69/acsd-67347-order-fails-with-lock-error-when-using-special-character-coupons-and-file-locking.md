---
title: 'ACSD-67347: De volgorde mislukt met de fout ''''Kan geen vergrendeling verkrijgen'''' bij het gebruik van couponcodes'
description: Pas de ACSD-67347-patch toe op de Adobe Commerce-uitgave waar orders mislukken met de fout ''Kan geen vergrendeling verkrijgen'' wanneer couponcodes speciale tekens bevatten (bijvoorbeeld BIT/123456) en bestandsvergrendeling is ingeschakeld.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: a439e163-8b09-456c-91bd-6ee67528744e
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-67347: De orde ontbreekt met *kan geen slot* fout verwerven wanneer het gebruiken van couponcodes

ACSD-67347 flardfixes de kwestie waar de orden met a *ontbreken kan een slot* fout verwerven wanneer de couponcodes speciale karakters (bijvoorbeeld, BIT/123456) bevatten en het dossier wordt gesloten toegelaten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-67347. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p12

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De orden ontbreken met *kan geen slot* fout verwerven wanneer de coupons met speciale karakters worden gebruikt en het dossier wordt gesloten toegelaten.

<u> Stappen om </u> te reproduceren:

1. Installeer 2.4-ontwikkelen.
1. Stel de vergrendelingsconfiguratie van het bestand in in het `env.php` -bestand:

   ```text
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Maak een regel met een winkelwagentje met een coupon in de notatie van de couponcode: *BIT/123456.*
1. Maak een eenvoudig product.
1. Voeg het product toe aan het winkelwagentje en pas de couponcode toe.
1. Ga door met het afrekenen en plaats de bestelling.

<u> Verwachte resultaten </u>:

Bestellingen worden correct geplaatst omdat er geen beperkingen zijn voor het maken van couponcodes.

<u> Ware resultaten </u>:

De volgorde kan niet worden geplaatst. De volgende fout wordt weergegeven: *kan slot niet verwerven.*

```text
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

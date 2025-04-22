---
title: 'ACSD-57003: de statuswijzigingen van bestellingen worden gewijzigd in *Complete* in plaats van te worden gewijzigd in *Processing*'
description: Pas de ACSD-57003-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de bestelling verandert in *Complete* in plaats van te veranderen in *Processing*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 128107310416e97edca3b122e97456138d04073f
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003: De statusveranderingen van de orde in *Volledige* in plaats van het veranderen in *Verwerking*

ACSD-57003 herstelt de flard waar de ordestatus in *Volledige* in plaats van het veranderen in *Verwerking* verandert. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-57003. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3, 2.4.6-p8, 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p9, 2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ordestatus verandert in *Volledig* in plaats van het veranderen in *Verwerking* wanneer een orde gedeeltelijk wordt terugbetaald en gedeeltelijk verscheept.

<u> Stappen om </u> te reproduceren:

1. Creeer een orde met twee configureerbare producten.
1. Factuur alle items.
1. Alleen het eerste object verzenden.
1. Restitueer/creeer een creditnota voor slechts het verscheepte punt (*eerste punt*).
1. Controleer de orderstatus.

<u> Verwachte resultaten </u>:

De status van de orde zou in de _staat van de Verwerking_ moeten zijn.

<u> Ware resultaten </u>:

De statusveranderingen van de orde in *Volledige* na het creëren van een creditnota voor gedeeltelijk verscheept punt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

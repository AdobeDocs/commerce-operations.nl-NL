---
title: 'ACSD-64111: Verhelpt *InvalidArgumentException: Class does not exist* error when setting nested conditions for a Product component in  [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-64111: Verhelpt *InvalidArgumentException: De klasse bestaat niet* fout wanneer het plaatsen van genestelde voorwaarden voor een component van het Product in [!DNL Page Builder]

Het ACSD-64111 flard bevestigt de kwestie waar *InvalidArgumentException: De klasse bestaat niet* fout komt in `vendor/magento/module-rule/Model/ConditionFactory.php:50` voor wanneer het plaatsen van genestelde voorwaarden voor een component van het Product in [!DNL Page Builder]. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 wordt geïnstalleerd. De patch-id is ACSD-6411. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden)  2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een fout *InvalidArgumentException: Klasse bestaat niet in /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php* wordt geworpen wanneer het toevoegen van een *[!UICONTROL Conditions Combination]* in [!DNL Page Builder] de voorwaarde van de Producten widget.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Adobe Commerce-beheerder.
1. Ga naar **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** .
1. Een nieuwe pagina toevoegen (of een bestaande pagina bewerken).
1. Vouw de sectie **[!UICONTROL Content]** uit en klik op **[!UICONTROL Edit with Page Builder]** .
1. Voeg een nieuwe rij toe en vervolgens de **[!UICONTROL Products]** -widget.
1. Configureer de **[!UICONTROL Products]** -widget.
1. Selecteer **[!UICONTROL Condition]** onder **[!UICONTROL Select Products By]** .
1. Voeg een nieuwe voorwaarde toe en selecteer **[!UICONTROL Conditions Combination]** van dropdown.

<u> Verwachte resultaten </u>:

Geen fouten in logbestanden.

<u> Ware resultaten </u>:

De onderstaande uitzondering wordt opgenomen in de logboeken:

*report.CRITICAL: InvalidArgumentException: De klasse bestaat niet in vendor/magento/module-rule/Model/ConditionFactory.php:50*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens niet correct bijgewerkt in de winkelweergave'
description: Pas de ACSD-53658-patch toe om het Adobe Commerce-probleem op te lossen, waarbij **[!UICONTROL Recently Viewed Product]** gegevens niet correct worden bijgewerkt in de winkelweergave.
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave

De ACSD-53658-patch verhelpt het probleem waarbij **[!UICONTROL Recently Viewed Product]** -gegevens niet correct worden bijgewerkt in de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-53658. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Recently Viewed Product]** -gegevens worden niet correct bijgewerkt in de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Beheer.
1. Maak een tweede opslagweergave voor de standaardwebsite.
1. Maak een eenvoudig product.
1. Stel een andere productnaam in voor de nieuwe winkelweergave.
1. Maak een **[!UICONTROL Recently Viewed Product]** -widget.
1. Configureer deze widget voor weergave op de startpagina.
1. Open de productpagina in de Storefront vanuit de standaardwinkelweergave.
1. Open de startpagina.
1. Schakel over naar de tweede winkelweergave met de opslagschakelaar.

<u> Verwachte resultaten </u>:

De productnaam wordt bijgewerkt in de widget.

<u> Ware resultaten </u>:

De productnaam wordt niet bijgewerkt in de widget.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

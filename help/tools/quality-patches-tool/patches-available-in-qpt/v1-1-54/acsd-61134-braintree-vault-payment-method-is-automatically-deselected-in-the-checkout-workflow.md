---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] betaalmethode wordt automatisch uitgeschakeld in de uitcheckworkflow'
description: Pas ACSD-61134 flard toe om de kwestie van Adobe Commerce op te lossen waar de * [!UICONTROL Braintree Vault]* betalingsmethode automatisch in het controlewerkschema wordt geschrapt wanneer een verkoopster hun facturerings adres door * [!UICONTROL My billing and shipping address are the same] * checkbox uit te schakelen bijwerkt.
feature: Checkout
role: Admin, Developer
source-git-commit: 459f1e70464e4df04dc306ee403730798f0f9b9e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* betaalmethode wordt automatisch uitgeschakeld in de uitcheckworkflow

De ACSD-61134-patch verhelpt het probleem waarbij de betalingsmethode *[!UICONTROL Braintree Vault]* automatisch wordt uitgeschakeld in de workflow voor het uitchecken wanneer een winkelier zijn factureringsadres bijwerkt door het selectievakje *[!UICONTROL My billing and shipping address are the same]* uit te schakelen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 wordt geïnstalleerd. De patch-id is ACSD-61134. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7-bèta1.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p7

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De betalingsmethode *[!UICONTROL Braintree Vault]* wordt automatisch uitgeschakeld in de workflow voor uitchecken.

<u> Stappen om </u> te reproduceren:

1. Configureer de betalingsmethode *[!DNL Braintree]* met *[!UICONTROL Vault]* ingeschakeld.
1. Een kaart uitchecken en opslaan in de *[!UICONTROL Vault]* .
1. Nog een product uitchecken.
1. Voeg op de pagina *[!UICONTROL Shipping]* een nieuw verzendadres toe, zodat u twee adressen kunt selecteren.
1. Selecteer op de pagina *[!UICONTROL Payment]* de betalingsmethode en klik op **[!UICONTROL My billing and shipping addresses are the same]** .

<u> Verwachte resultaten </u>:

De geselecteerde betalingsmethode blijft geselecteerd.

<u> Ware resultaten </u>:

De geselecteerde betalingsmethode is uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.


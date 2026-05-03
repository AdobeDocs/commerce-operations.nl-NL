---
title: 'ACSD-65938: E-mails met een creditcard worden verzonden, zelfs als de factuur niet is gemaakt'
description: Pas de ACSD-65938-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mails met een cadeaukaart zijn verzonden voordat de factuur is opgeslagen en toegewezen, zodat e-mails worden geactiveerd nadat de factuur correct is opgeslagen.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: a6e85c9a-cbf6-4b4a-927b-43ec2ce827fc
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-65938: E-mails met een creditcard worden verzonden, zelfs als de factuur niet is gemaakt

De ACSD-65938-patch verhelpt een probleem waarbij e-mails met een cadeaukaart zijn verzonden voordat de factuur is opgeslagen en toegewezen. Met deze correctie worden e-mailberichten nu pas geactiveerd nadat de factuur is opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-65938. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mails met een creditcard zijn verzonden voordat werd bevestigd dat de factuur is gemaakt en opgeslagen. Dit heeft ertoe geleid dat e-mailberichten worden verzonden, zelfs als het aanmaken van de factuur is mislukt.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster **[!UICONTROL Admin]** .
2. Navigeer aan **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**, en plaats **[!UICONTROL Generate Gift Card Account when Order Item is]** aan *Gecodeerde*.
3. Maak een nieuw cadeaukaartproduct.
4. Voeg een geschenkproduct toe aan de winkelwagentje en ga verder met **[!UICONTROL checkout]** . U kunt **[!UICONTROL Check/Money Order]** gebruiken als betalingsmethode.
5. Plaats de bestelling.
6. Wijzig `OrderRepository` om een uitzondering tijdens ordsplaatsing te simuleren.
7. Verzend een POST-aanvraag naar `rest/default/V1/order/<ORDER_ID>/invoice` met de volgende payload:

   ```json
   {
     "capture": true,
     "notify": true
   }
   ```


<u> Verwachte resultaten </u>:

Er wordt geen e-mail met een cadeaukaart verzonden als het aanmaken van de factuur mislukt.

<u> Ware resultaten </u>:

E-mail met creditcard wordt verzonden, ook al is het aanmaken van de factuur mislukt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

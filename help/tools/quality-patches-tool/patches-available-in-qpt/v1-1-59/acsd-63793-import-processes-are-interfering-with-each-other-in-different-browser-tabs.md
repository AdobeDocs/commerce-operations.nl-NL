---
title: 'ACSD-63793: de processen van de invoer beïnvloeden elkaar in verschillende browser lusjes'
description: Pas de ACSD-63793-patch toe om het Adobe Commerce-probleem op te lossen waarbij importprocessen elkaar in verschillende browsertabbladen beïnvloeden.
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-63793: de processen van de invoer beïnvloeden elkaar in verschillende browser lusjes

De ACSD-63793-patch verhelpt het probleem waarbij importprocessen met elkaar interfereren op verschillende browsertabbladen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-63793. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het importeren van gegevens via de interface van Admin heeft invloed op een andere importbewerking, waardoor gegevens van de ene importbewerking in een andere importbewerking worden verwerkt.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** .
1. Plaats **[!UICONTROL Entity Type]** aan *[!UICONTROL Customers and Addresses] (enig dossier)*.
1. Stel **[!UICONTROL Import Behavior]** in op *[!UICONTROL Add/Update]* .
1. Selecteer een geldig bestand dat u wilt importeren.
1. Klik op **[!UICONTROL Check Data]** .
1. Zorg dat dit tabblad geopend blijft.
1. Open een nieuw tabblad en herhaal de stappen in een bestand met ongeldige gegevens (bijvoorbeeld twee identieke e-mails voor verschillende klanten).
1. Ga terug naar de eerste tab.
1. Klik op de knop **[!UICONTROL Import]** onderaan.

<u> Verwachte resultaten </u>:

Het importproces mag elkaar niet verstoren.

<u> Ware resultaten </u>:

Het importproces is voltooid en het rapportbestand is beschikbaar voor downloaden. De waarde geeft een fout in de tweede rij aan en gegevens uit een andere importbewerking worden verwerkt, ook al is de eerste validatie zonder fouten geslaagd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

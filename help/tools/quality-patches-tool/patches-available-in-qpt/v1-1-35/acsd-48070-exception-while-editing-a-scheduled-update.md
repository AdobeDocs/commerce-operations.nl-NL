---
title: 'ACSD-48070: uitzondering tijdens het bewerken van een geplande update'
description: Pas de ACSD-48070-patch toe om het Adobe Commerce-probleem op te lossen waarbij een uitzondering wordt geactiveerd tijdens het bewerken van een geplande update.
feature: Catalog Management, Categories
role: Admin
exl-id: cebed18d-d213-4a5e-bc3b-8abcb52d45d0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-48070: uitzondering tijdens het bewerken van een geplande update

De ACSD-48070-patch verhelpt het probleem waarbij een uitzondering wordt geactiveerd tijdens het bewerken van een geplande update. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-48070. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een uitzondering geactiveerd tijdens het bewerken van een geplande update.

<u> Stappen om </u> te reproduceren:

1. Open een categorie.
2. Maak een nieuwe **[!UICONTROL Scheduled Update]** en sla deze op.
3. Klik op **[!UICONTROL View/Edit]** in het gemaakte bestand **[!UICONTROL Scheduled Update]** .
4. Sla het bestand opnieuw op.

<u> Verwachte resultaten </u>

**[!UICONTROL Scheduled Update]** wordt opgeslagen.

<u> Ware resultaten </u>

Een fout komt voor: *fout: iets ging verkeerd terwijl het bewaren van Magento\Catalog\Api\Data\CategoryInterface.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

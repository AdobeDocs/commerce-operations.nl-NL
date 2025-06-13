---
title: 'ACSD-60632: adres opgeslagen bij elke poging tot bestelling'
description: Pas de ACSD-60632-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een nieuw adres wordt opgeslagen bij elke poging tot plaatsing van de bestelling, ongeacht of de bestelling is gemaakt of niet.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: adres opgeslagen bij elke poging tot bestelling

De ACSD-60632-patch verhelpt het probleem waarbij een nieuw adres wordt opgeslagen bij elke poging tot plaatsing van de bestelling, ongeacht of de bestelling is gemaakt of niet. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 wordt geïnstalleerd. De patch-id is ACSD-60632. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Telkens wanneer een orderplaatsing wordt geprobeerd, wordt een nieuw adresingang bewaard in het systeem, ongeacht of de orde met succes wordt gecreeerd.

<u> Stappen om </u> te reproduceren:

1. Betalingsmethode **[!DNL PayPal Payflow Link]** inschakelen:
   * Op een lokale computer kan het systeem geen API-aanroepen van [!DNL PayPal Payflow Link] ontvangen zonder een echte IP.
1. Maak een eenvoudig product.
1. Een geregistreerde klant zonder adres maken.
1. Voeg het product toe aan de kar.
1. Ga door naar Afhandeling.
1. Vul het adres in. Zorg ervoor dat het eerste adres bij deze stap wordt gecreeerd.
1. Selecteer op de pagina *[!UICONTROL Review and Payments]* het keuzerondje **[!UICONTROL Credit Card (Payflow Link)]** .
1. Klik op **[!UICONTROL Continue]** :
   * De uitcheckpagina keert terug naar de *[!UICONTROL Review and Payments]* -stap met het vooraf ingevulde adres en het verwachte foutbericht.
1. Selecteer nogmaals *[!UICONTROL Credit Card (Payflow Link)]* keuzerondje.
1. Klik op **[!UICONTROL Continue]** .

<u> Verwachte resultaten </u>:

Er wordt geen nieuw adres gemaakt bij de tweede poging tot plaatsing van de bestelling.

<u> Ware resultaten </u>:

Er wordt een nieuw adres gemaakt na elke poging tot plaatsing van de bestelling.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

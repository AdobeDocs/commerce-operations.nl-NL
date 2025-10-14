---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht'
description: Pas de ACSD-52736-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid bevat, niet werkt zoals u had verwacht.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht

De ACSD-52736-patch verhelpt het probleem dat een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid bevat, niet naar behoren functioneert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-52736. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid omvat, werkt niet zoals verwacht.

<u> Stappen om </u> te reproduceren:

1. Een winkelwagentregel maken:
   * [!UICONTROL Apply] = Percentage van korting op productprijs
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Pas de regel alleen toe op de winkelwagentjes die aan de volgende voorwaarden voldoen: hoeveelheid in winkelwagentje is 1
2. Voeg een product met [!UICONTROL Qty] = 2 toe aan het winkelwagentje.
3. Controleer de prijzen van winkelwagentjes.

<u> Verwachte resultaten </u>:

De regel wordt niet toegepast omdat de hoeveelheid producten in de kar *2* is.

<u> Ware resultaten </u>:

De korting wordt toegepast.

<u> Aanvullende stappen vereist na de patch-installatie </u> :

Na het toepassen van het flard, moeten de voorwaarden van de kartregel gebruikend het *attribuut van de Hoeveelheid* worden verwijderd en opnieuw toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

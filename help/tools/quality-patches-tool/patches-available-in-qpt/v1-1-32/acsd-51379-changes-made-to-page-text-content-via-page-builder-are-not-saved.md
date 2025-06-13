---
title: 'ACSD-51379: De veranderingen in de tekstinhoud van de pagina via  [!DNL Page Builder]  worden niet bewaard'
description: Pas ACSD-51379 flard toe om de kwestie van Adobe Commerce te bevestigen waar de veranderingen die aan de tekstinhoud van een pagina via  [!DNL Page Builder]  worden aangebracht niet worden bewaard.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: Wijzigingen in tekstinhoud van pagina via [!DNL Page Builder] worden niet opgeslagen

De ACSD-51379-patch verhelpt het probleem dat de wijzigingen die via [!DNL Page Builder] in de tekstinhoud van een pagina zijn aangebracht, niet worden opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51379. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De wijzigingen die via [!DNL Page Builder] in de tekstinhoud van een pagina zijn aangebracht, worden niet opgeslagen.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Beheer.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** .
1. Maak een testpagina met één rij en één tekstelement op het tabblad **[!UICONTROL Content]** .
1. Sla de pagina op en ga terug naar de tab **[!UICONTROL Content]** .
1. Bewerk de tekst door deze te selecteren en te wijzigen.

   **Nota:** de kwestie is slechts reproduceerbaar als de tekst wordt geselecteerd en veranderd zonder de redacteur te activeren.

1. Klik op de knop **[!UICONTROL Save and Close]** op de testpagina.
1. Open de testpagina opnieuw en controleer de tab **[!UICONTROL Content]** .

<u> Verwachte resultaten </u>:

De nieuwe tekst wordt opgeslagen voor originele en gedupliceerde tekstelementen.

<u> Ware resultaten </u>:

Het tekstelement is gedupliceerd, maar de nieuwe tekst wordt niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

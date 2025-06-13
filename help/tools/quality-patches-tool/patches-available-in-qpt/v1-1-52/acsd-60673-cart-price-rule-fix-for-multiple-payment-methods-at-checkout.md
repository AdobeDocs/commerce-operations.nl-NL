---
title: 'ACSD-60673: [!UICONTROL Cart Price Rule] probleem opgelost voor meerdere betalingsmethoden bij afhandeling'
description: Pas de ACSD-60673-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de kortingen van een [!UICONTROL Cart Price Rule] die een betalingsmethode gebruiken, niet altijd in de totalen worden vermeld.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: [!UICONTROL Cart Price Rule] probleem opgelost voor meerdere betalingsmethoden bij afhandeling

De ACSD-60673-patch verhelpt het probleem dat de kortingen van een [!UICONTROL Cart Price Rule] die een betalingsmethode gebruiken, niet altijd in de totalen worden vermeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-60673. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!UICONTROL Cart Price Rule] voor meerdere betalingsmethoden bij afhandeling is niet correct van toepassing op de specifieke betalingsmethode.

<u> Eerste vereisten </u>

Zorg ervoor dat **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** en **[!UICONTROL Bank Transfer]** is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Multiple Payment Methods]** in.
1. Maak een *[!UICONTROL Cart Price Rule]* .
   * Instellen **[!UICONTROL Conditions]** : betalingsmethode op **[!UICONTROL Money Order]** (of overschrijving)
   * Selecteer **[!UICONTROL Actions]** = *25%* korting op alle producten
1. Maak een virtueel product.
1. Als u een nieuw aanhalingsteken en een gast wilt kopiëren *[!UICONTROL Status]* , gaat u naar de winkel en wist u cookies.
1. Voeg het virtuele product toe aan het winkelwagentje.
1. Ga aan *controle* te werk.
1. Klik op de betalingsmethode die is gedefinieerd in de *[!UICONTROL Cart Price Rule]* .
1. Werk uw *[!UICONTROL Billing Address]* bij.
1. Zorg ervoor dat de korting zichtbaar is in het totale bedrag.
1. Klik op het selectievakje om de betalingsmethode te wijzigen.
1. Controleer of de korting zichtbaar is.

<u> Verwachte resultaten </u>:

De korting is zichtbaar in *Totalen* na het klikken op checkbox om op een toepasselijke betalingsmethode over te schakelen.

<u> Ware resultaten </u>:

De korting is niet zichtbaar in de *Totalen*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

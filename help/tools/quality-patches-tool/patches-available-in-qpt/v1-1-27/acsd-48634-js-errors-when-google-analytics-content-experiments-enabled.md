---
title: 'ACSD-48634: [!DNL JS]  fouten wanneer  [!DNL Google Analytics Content Experiments]  toegelaten'
description: Pas ACSD-48634 flard toe om  [!DNL JS]  fouten op a  [!DNL staging]  updatepagina te bevestigen wanneer  [!DNL Google Analytics Content Experiments]  wordt toegelaten.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] fouten als [!DNL Google Analytics Content Experiments] ingeschakeld is

De ACSD-48634-patch corrigeert [!DNL JS] -fouten op een [!DNL staging] updatepagina als [!DNL Google Analytics Content Experiments] is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48634. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treden [!DNL JS] fouten op op een [!DNL staging] updatepagina wanneer [!DNL Google Analytics Content Experiments] is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** een extra website, winkel en **[!UICONTROL Store View]** . Zorg ervoor dat **[!UICONTROL Store View]** *[!UICONTROL Enabled]* is.
1. Configureer **[!DNL Configure Google Analytics]** door naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** te gaan:
   * Voor **[!DNL Main]** en aanvullende websites [!DNL scope] :
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* voor andere velden, maar wijzig deze niet.
   * Voor **[!DNL Default Config]** [!DNL scope] :
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Schakel **[!DNL Configure Google Analytics]** aan **[!DNL Default Config]** [!DNL scope] uit door **[!UICONTROL Enable]** van *[!UICONTROL Yes]* in *[!UICONTROL No]* te wijzigen. Verander niets anders!
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** .
1. Maak en bewerk **[!UICONTROL category]** en voeg een geplande update voor deze toepassing toe:
   * Elke naam, begindatum in de toekomst, einddatum in de toekomst en elke wijziging in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Sla de update op en controleer de [!DNL browser developer console] op fouten.

<u> Verwachte resultaten </u>:

Er zijn geen [!DNL JS] fouten en de wijzigingen in de [!DNL staging] -update zijn opgeslagen.

<u> Ware resultaten </u>:

[!DNL JS] -fouten zijn zichtbaar in de console, het formulier is onjuist geformuleerd en [!DNL spinner] wordt nooit uitgeschakeld na het opslaan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

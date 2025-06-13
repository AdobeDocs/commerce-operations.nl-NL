---
title: 'ACSD-49370: Productkenmerk heeft het type ''FilterMatchTypeInput'' in het GraphQL-schema'
description: Pas de ACSD-49370-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het productkenmerk het type 'FilterMatchTypeInput' heeft in het GraphQL-schema.
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
exl-id: 05cc6db6-6ea6-4eb7-8dc0-fcb9f479fd89
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-49370: productkenmerk heeft `FilterMatchTypeInput` type in GraphQL-schema

De ACSD-49370-patch verhelpt het probleem waarbij het productkenmerk een `FilterMatchTypeInput` -type heeft in het GraphQL-schema. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49370. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het kenmerk product heeft een `FilterMatchTypeInput` -type in het GraphQL-schema.

<u> Stappen om </u> te reproduceren:

1. Creeer *Datum en Tijd* productattributen.

   * [!UICONTROL Type]: [!UICONTROL DateTime]
   * [!UICONTROL Default Label]: [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]: [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]: [!UICONTROL Yes]

1. Vraag de *GQL API* documentatie voor de `ProductAttributeFilterInput` typedefinitie.
1. Bekijk het invoertype voor het gemaakte kenmerk.

<u> Verwachte resultaten </u>:

Het *attribuut van de Tijd van de Datum* toont het type van filterinput `FilterRangeTypeInput`.

<u> Ware resultaten </u>:

Het *attribuut van de Tijd van de Datum* toont het type van filterinput `FilterMatchInputType`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

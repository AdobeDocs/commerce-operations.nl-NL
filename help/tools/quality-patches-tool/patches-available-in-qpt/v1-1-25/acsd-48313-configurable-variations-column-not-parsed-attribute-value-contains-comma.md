---
title: 'ACSD-48313: [!UICONTROL configurable_variations] kolom niet geparseerd als kenmerkwaarde een komma bevat'
description: Pas de ACSD-48313-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL configurable_variations] -kolom niet wordt geparseerd als de kenmerkwaarde een komma bevat.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** kolom niet geparseerd als kenmerkwaarde een komma bevat

De ACSD-48313-patch lost het probleem op waarbij de **[!UICONTROL configurable_variations]** -kolom niet wordt geparseerd als de kenmerkwaarde een komma bevat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48313. De versie waarin dit probleem wordt opgelost, is nog niet beschikbaar.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het exporteren van configureerbare producten kan het resulterende bestand niet opnieuw worden geïmporteerd vanwege een opmaakprobleem met het kenmerk **[!UICONTROL configurable_variations]** . Dit gebeurt wanneer er kenmerkopties zijn die een komma bevatten.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en creeer een nieuw attribuut _Grootte_:
1. Invoertype catalogus voor winkeleigenaar: **[!UICONTROL Dropdown]** .
1. Opties maken die een komma bevatten, bijvoorbeeld:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - werkingsgebied: _Globaal_.
1. Maak een nieuw configureerbaar product met de functie Configuraties maken.
1. Selecteer de bovengenoemde attributen _Grootte_ en de twee opties die de komma omvatten.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** en maak een nieuwe exportbewerking voor producten (voer de uitsnede uit om het genereren van het CSV-bestand te activeren).
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** en importeer hetzelfde CSV-bestand dat u hierboven hebt gemaakt opnieuw.

<u> Verwachte resultaten </u>:

De gebruiker moet het bestand kunnen importeren.

<u> Ware resultaten </u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-49835: selectievakje [!UICONTROL Use Default Value] wordt niet opgeslagen'
description: Pas de ACSD-49835-patch toe om het Adobe Commerce-probleem op te lossen waarbij het selectievakje [!UICONTROL Use Default Value] niet correct is opgeslagen op archiefniveau voor een multi-select kenmerk.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835: selectievakje [!UICONTROL Use Default Value] wordt niet opgeslagen

De ACSD-49835-patch verhelpt het probleem waarbij het selectievakje [!UICONTROL Use Default Value] niet correct wordt opgeslagen op archiefniveau voor een kenmerk voor meerdere selecties. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49835. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het selectievakje [!UICONTROL Use Default Value] wordt niet correct opgeslagen op archiefniveau voor een kenmerk voor meerdere selecties.

<u> Stappen om </u> te reproduceren:

1. Maak een **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en voeg deze toe aan een kenmerkset.
1. Ga naar een **[!UICONTROL Product]** -bestand en sla **[!UICONTROL Values]** op in **[!UICONTROL All Store Views (Default Scope)]** .
1. Ga naar een specifieke **[!UICONTROL Store View Scope]** en sla het product op.
1. Ga naar **[!UICONTROL Store View Scope]** en controleer het selectievakje **[!UICONTROL Use Default Value]** .

<u> Verwachte resultaten </u>:

Meerdere geselecteerde kenmerkwaarden worden correct opgeslagen wanneer u het selectievakje [!UICONTROL Use Default Value] in [!UICONTROL Store View Scope] inschakelt.

<u> Ware resultaten </u>:

Meerdere geselecteerde kenmerkwaarden worden niet correct opgeslagen wanneer u het selectievakje [!UICONTROL Use Default Value] in [!UICONTROL Store View Scope] inschakelt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

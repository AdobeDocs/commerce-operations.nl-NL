---
title: 'ACSD-51358: planningupdates ontbreken'
description: Pas de ACSD-51358-patch toe om het Adobe Commerce-probleem op te lossen waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates op dezelfde entiteit worden verwijderd.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: planningupdates ontbreken

De ACSD-51358-patch verhelpt het probleem waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates voor dezelfde entiteit worden verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51358. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De wijzigingen in de geplande update zonder einddatum leiden tot het verwijderen van andere geplande updates voor dezelfde entiteit.

<u> Stappen om </u> te reproduceren:

1. Creeer a **[!UICONTROL scheduled update]** zonder de einddatum (*update 1*).
1. Creeer nieuw **[!UICONTROL scheduled update]** met zelfde begindatum zoals eerste update, maar voeg de volgende dag, en de einddatum toe (*update 2*).
1. Bewerk **[!UICONTROL scheduled update]** gecreeerd op stap 1 (*update 1*) en sparen veranderingen.

<u> Verwachte resultaten </u>

(*update 2*) zou in de **[!UICONTROL schedule update]** lijst moeten blijven wanneer (*update 1*) wordt uitgegeven.

<u> Ware resultaten </u>

(*update 2*) werd verwijderd uit de **[!UICONTROL schedule update]** lijst wanneer (*update 1*) wordt uitgegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.

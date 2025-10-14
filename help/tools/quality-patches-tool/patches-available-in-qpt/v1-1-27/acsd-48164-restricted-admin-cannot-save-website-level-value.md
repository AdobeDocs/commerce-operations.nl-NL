---
title: 'ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan'
description: Pas de ACSD-48164-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan

De ACSD-48164-patch verhelpt het probleem waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen geen waarde op websiteniveau opslaan.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website, sla deze op en sla de weergave op in [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]** .
1. Maak een nieuwe beheerdersrol in [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]** .

   * Ga naar **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]** , selecteer de nieuwe website en wijs deze rol toe aan elke gebruiker van de beheerder.

1. Selecteer een willekeurig product en wijs alleen de nieuwe website toe. Selecteer de standaardwebsite niet.
1. Meld u aan als de beheerder die in stap twee is toegewezen en bewerk het product onder **[!UICONTROL All Store View]** scope door een kenmerk op websiteniveau zoals *[!UICONTROL Status]* , *[!UICONTROL Tax Class]* te wijzigen en het product als nieuw in te stellen.
1. Sla het product op.

<u> Verwachte resultaten </u>:

Admin-gebruiker die aan het rolbereik aan één website is gekoppeld, kan productkenmerken op websiteniveau opslaan met behulp van het bereik van *[!UICONTROL All Store View]* .

<u> Ware resultaten </u>:

Het succesbericht dat het product is opgeslagen, verschijnt, maar de waarden van de productkenmerken blijven ongewijzigd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

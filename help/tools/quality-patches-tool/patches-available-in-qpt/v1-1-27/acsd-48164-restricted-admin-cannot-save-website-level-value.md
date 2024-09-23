---
title: 'ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan'
description: Pas de ACSD-48164-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan.
feature: Admin Workspace
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan

De ACSD-48164-patch verhelpt het probleem waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

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

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

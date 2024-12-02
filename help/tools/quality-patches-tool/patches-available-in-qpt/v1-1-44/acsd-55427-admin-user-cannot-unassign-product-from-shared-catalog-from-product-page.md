---
title: 'ACSD-55427: een beheerder kan het toewijzen van een product niet ongedaan maken via **[!UICONTROL Product in Shared Catalogs]** op de productpagina'
description: Pas de ACSD-55427-patch toe om het Adobe Commerce-probleem op te lossen waarbij de toewijzing van een product niet ongedaan kan worden gemaakt vanaf **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427: een beheerder kan de toewijzing van het product aan **[!UICONTROL Product in Shared Catalogs]** op de productpagina niet ongedaan maken

De ACSD-55427-patch verhelpt het probleem dat u de toewijzing van een product uit **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin niet ongedaan kunt maken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-55427. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U kunt de toewijzing van een product uit **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin niet ongedaan maken.

<u> Stappen om </u> te reproduceren:

Vereisten: Adobe Commerce geïnstalleerd met zowel B2B als **[!UICONTROL Shared Catalogs]** ingeschakeld.
1. Maak een product.
1. Navigeer naar het gedeelde catalogusdashboard en open de standaard gedeelde catalogus.
1. Het product toewijzen aan de standaardcatalogus en een lagere prijs dan de productprijs instellen.
1. Sla de gedeelde catalogus op.
1. Voer de [!UICONTROL CRON] uit om de consumenten/indexen bij te werken.
1. Open het product en verwijder het product onder **[!UICONTROL Product in Shared Catalogs]** -sectie.

<u> Verwachte resultaten </u>:

Het product moet onder **[!UICONTROL Product in Shared Catalogs]** -sectie worden verwijderd.

<u> Ware resultaten </u>:

Het product wordt nog steeds weergegeven in de sectie **[!UICONTROL Product in Shared Catalogs]** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

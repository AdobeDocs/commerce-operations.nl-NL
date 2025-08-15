---
title: 'ACSD-66118: Als u een update uitvoert, worden de [!UICONTROL Store View Code] instellingen gewist als [!UICONTROL Design Configuration] niet wordt vernieuwd[!UICONTROL Configuration Cache]'
description: Pas de ACSD-66118-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij bij het bijwerken van [!UICONTROL Store View Code] de [!UICONTROL Design Configuration] -tag (thema en aangepaste instellingen) wordt gewist als de [!UICONTROL Configuration Cache] niet correct wordt vernieuwd.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 468c780f355c99cf06d557e530e81c414a01961e
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-66118: Als u een update uitvoert, worden de **[!UICONTROL Store View Code]** instellingen gewist als **[!UICONTROL Design Configuration]** niet wordt vernieuwd **[!UICONTROL Configuration Cache]**

De ACSD-66118-patch verhelpt het probleem dat bij het bijwerken van de **[!UICONTROL Store View Code]** instellingen voor **[!UICONTROL Design Configuration]** worden gewist als de **[!UICONTROL Configuration Cache]** niet wordt vernieuwd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66118. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**[!UICONTROL Design Configuration]** -instellingen (zoals thema en aangepaste instellingen) worden gewist tijdens het bijwerken van het veld **[!UICONTROL Store View Code]** , als **[!UICONTROL Configuration Cache]** niet is vernieuwd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster **[!UICONTROL Admin]** .
2. Navigeer naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]** .
3. Bewerk een winkelweergave waarin een aangepast thema is geconfigureerd in **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** .
4. Wijzig het veld **[!UICONTROL Code]** (bijvoorbeeld van `storeview_1` in `storeview_main` ).
5. Klik op **[!UICONTROL Save Store View]** om de wijzigingen op te slaan.
6. Vernieuw of open de pagina **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** voor de bijgewerkte **[!UICONTROL Store View]** en er wordt geen thema geselecteerd.

<u> Verwachte resultaten </u>:

Na het bijwerken van de **[!UICONTROL Store View Code]** , moeten de **[!UICONTROL Design Configuration]** (inclusief het thema en de aangepaste instellingen) intact blijven.

<u> Ware resultaten </u>:

De lus **[!UICONTROL Design Configuration]** wordt gewist. Het thema wordt teruggezet naar de standaardwaarden en er gaan aangepaste instellingen verloren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

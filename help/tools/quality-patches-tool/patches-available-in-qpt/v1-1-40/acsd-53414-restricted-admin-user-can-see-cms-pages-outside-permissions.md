---
title: 'ACSD-53414: gebruikers met beperkte beheerdersrechten kunnen CMS-pagina''s zien die buiten het bereik van hun machtigingen vallen'
description: Pas de ACSD-53414-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een gebruiker met beperkte bevoegdheden CMS-pagina's kan zien die buiten het bereik van zijn bevoegdheden vallen.
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: gebruikers met beperkte beheerdersrechten kunnen CMS-pagina&#39;s zien die buiten het bereik van hun machtigingen vallen

De ACSD-53414-patch verhelpt het probleem waarbij een gebruiker met beperkte beheerdersrechten CMS-pagina&#39;s kan zien die buiten het bereik van hun bevoegdheden vallen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-53414. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen CMS-pagina&#39;s buiten het bereik van hun machtigingen weergeven.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website (sub_website), store (sub_store) en storeview (sub_storeview).
1. Creeer een sub_expert rol, die het werkingsgebied van sub_website en sub_store toestaat. Alleen de volgende machtigingen toewijzen: [!UICONTROL Dashboard] en [!UICONTROL Pages] .
1. Creeer een nieuwe admin gebruiker en wijs het aan sub_expert rol toe.
1. Wijs de volgende CSM-pagina&#39;s toe aan sub_storeview en standaard storeview.

   * [!UICONTROL 404 Not Found] > Substoreview
   * [!UICONTROL 503 Service Unavailable] > Standaardstoreview

1. Meld u aan bij de beheerder met de beheerder die u in Stap 3 hebt gemaakt.
1. Controleer het CMS-paginaraster.

<u> Verwachte resultaten </u>:

De webbeheerder is de pagina *[!UICONTROL 503 Service Unavailable]* niet zichtbaar.

<u> Ware resultaten </u>:

*[!UICONTROL 503 Service Unavailable]* is zichtbaar voor de webbeheerder.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

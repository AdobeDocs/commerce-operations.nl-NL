---
title: 'ACSD-65127: De minificatie van JavaScript op productiemodus veroorzaakt  [!DNL TinyMCE]  6 fouten in browser'
description: Pas ACSD-65127 flard toe om de kwestie van Adobe Commerce te bevestigen waar het toelaten van de minificatie van JavaScript op productiemodus  [!DNL TinyMCE]  6 veroorzaakte om fouten in de browser console te produceren, die functionaliteit en gebruikerservaring beïnvloedt.
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: c5b27b79dd2dc7f9b39e629756d3d5d01e019710
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# ACSD-65127: JavaScript minification in production mode veroorzaakt [!DNL TinyMCE] 6 fouten in de browser

De ACSD-65127-patch verhelpt het probleem dat het inschakelen van JavaScript minification in productiemodus ertoe heeft geleid dat [!DNL TinyMCE] 6 fouten heeft gegenereerd in de browserconsole, wat van invloed is op de functionaliteit en gebruikerservaring. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65127. Dit probleem is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de pagina [[!DNL Quality Patches Tool] : zoek naar patches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u JavaScript-miniaturen inschakelt in de productiemodus, genereerde [!DNL TinyMCE] 6 fouten in de browserconsole die van invloed waren op de functionaliteit en gebruikerservaring.

<u> Stappen om </u> te reproduceren:

1. Stel de configuratie in door de onderstaande opdrachten uit te voeren:

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Productiemodus inschakelen.

```
bin/magento deploy:mode:set production
```

1. Ga op de zijbalk Beheerder naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** . Klik op **[!UICONTROL Edit]** op een product in de lijst en schuif omlaag naar **[!UICONTROL Content]** en selecteer **[!UICONTROL Show Editor]** .

<u> Verwachte resultaten </u>:

Geen JS-fouten in de browserconsole.

<u> Ware resultaten </u>:

*404* fouten in de browser console voor JS `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

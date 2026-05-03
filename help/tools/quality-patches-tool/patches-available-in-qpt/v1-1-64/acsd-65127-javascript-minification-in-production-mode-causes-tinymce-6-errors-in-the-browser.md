---
title: 'ACSD-65127: De miniatuur van JavaScript op productiemodus veroorzaakt  [!DNL TinyMCE]  6 fouten in browser'
description: Pas ACSD-65127 flard toe om de kwestie van Adobe Commerce te bevestigen waar het toelaten van de minificatie van JavaScript op productiemodus  [!DNL TinyMCE]  6 veroorzaakte om fouten in de browser console te produceren, die functionaliteit en gebruikerservaring beïnvloedt.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-65127: JavaScript minification in productiemodus veroorzaakt [!DNL TinyMCE] 6 fouten in de browser

De ACSD-65127-patch verhelpt het probleem dat het inschakelen van JavaScript minification in productiemodus ertoe heeft geleid dat [!DNL TinyMCE] 6 fouten heeft gegenereerd in de browserconsole, wat van invloed is op de functionaliteit en gebruikerservaring. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65127. Dit probleem is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) pagina. Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u JavaScript-miniaturen inschakelt in de productiemodus, genereerde [!DNL TinyMCE] 6 fouten in de browserconsole die van invloed waren op de functionaliteit en gebruikerservaring.

<u> Stappen om </u> te reproduceren:

1. Stel de configuratie in door de onderstaande opdrachten uit te voeren:

```shell
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

>[!NOTE]
>
>Adobe raadt u niet aan **[!UICONTROL Merge JavaScript Files]** in te schakelen. Zie [ JS- dossiers van de Fusie (niet geadviseerd) ](/help/implementation-playbook/best-practices/development/optimize-css-js-files.md#merge-js-files).

1. Productiemodus inschakelen.

```shell
bin/magento deploy:mode:set production
```

1. Ga op de zijbalk Beheerder naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** . Klik op **[!UICONTROL Edit]** op een product in de lijst en schuif omlaag naar **[!UICONTROL Content]** en selecteer **[!UICONTROL Show Editor]** .

<u> Verwachte resultaten </u>:

Geen JS-fouten in de browserconsole.

<u> Ware resultaten </u>:

*404* fouten in de browser console voor JS `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] hulplijn
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in de gids van de Infrastructuur van Commerce op de Wolk toe

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen

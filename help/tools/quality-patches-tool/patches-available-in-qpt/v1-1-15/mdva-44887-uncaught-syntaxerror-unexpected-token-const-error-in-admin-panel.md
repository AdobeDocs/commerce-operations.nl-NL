---
title: 'MDVA-44887: Fout ''Uncaught SyntaxError: Unexpected token const'' in deelvenster Beheer'
description: 'De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De fout *Uncaught SyntaxError: Unexpected token const* wordt weergegeven in het deelvenster Beheer. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.'
feature: Admin Workspace, Orders
role: Admin
exl-id: d8cc03c3-35a0-4f00-8ec3-1ba3e100f7ca
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887: Fout &#39;Uncaught SyntaxError: Unexpected token const&#39; in deelvenster Beheer

De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De *Uncaught SyntaxError: Onverwachte symbolische const* fout wordt getoond in het Admin paneel. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 geïnstalleerd is. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan niet op om het even welke menuoptie klikken. De *Uncaught SyntaxError: Onverwachte symbolische const* fout wordt getoond in het Admin paneel.

<u> Stappen om </u> te reproduceren:

1. JS-bundeling inschakelen.
1. U kunt de JS-bestanden miniateren.
1. Meld u aan bij het deelvenster Commerce Admin.

<u> Verwachte resultaten </u>:

De beheerder kan niet op om het even welke menuoptie klikken. Er is een fout in de browser console: *Uncaught SyntaxError: Unexpected token const*.

<u> Ware resultaten </u>:

Het deelvenster Beheer is toegankelijk voor een beheerder.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-49773: Exporteren van producten mislukt wanneer AWS S3 wordt gebruikt als externe opslag'
description: Pas de ACSD-49773-patch toe om het Adobe Commerce-probleem op te lossen waarbij het exporteren van het product mislukt wanneer AWS S3 wordt gebruikt als externe opslag.
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49773: Het exporteren van producten mislukt wanneer AWS S3 wordt gebruikt als externe opslag

De ACSD-49773-patch verhelpt het probleem waarbij het exporteren van een product mislukt wanneer AWS S3 wordt gebruikt als externe opslag. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49773. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van het product mislukt wanneer AWS S3 wordt gebruikt als externe opslag.

<u> Stappen om </u> te reproduceren:

1. Een groot gegevensprofiel installeren.
1. Maak een AWS-account en configureer een S3-emmertje en een IAM-gebruiker.
1. Werk `app/etc/env.php` bij met de configuraties.
1. Voer `bin/magento setup:upgrade` uit.
1. Ga naar back-end en voer een volledige productexport uit.
1. Controleer de status van het rijbericht van de `[queue_message_status]` lijst.
1. Controleer de systeemlogboeken.

<u> Verwachte resultaten </u>:

Het exporteren van het product wordt zonder fouten voltooid.

<u> Ware resultaten </u>:

Er is een fout opgetreden tijdens het aanmelden bij de systeemlogboeken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
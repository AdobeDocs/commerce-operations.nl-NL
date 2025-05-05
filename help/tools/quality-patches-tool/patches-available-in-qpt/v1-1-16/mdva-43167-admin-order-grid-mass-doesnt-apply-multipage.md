---
title: 'MDVA-43167: Massa van beheerdersraster is niet van toepassing op meerdere pagina''s'
description: De patch MDVA-43167 verhelpt het probleem waarbij de massaactie van het beheerderordaster niet van toepassing is op meerdere pagina's wanneer de beheerder alle bestellingen selecteert. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 is geïnstalleerd. De patch-id is MDVA-43167. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Admin Workspace, Orders
role: Admin
exl-id: 992f8a90-300e-41aa-b03d-b8a647dddd51
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-43167: Massa van beheerdersraster is niet van toepassing op meerdere pagina&#39;s

De patch MDVA-43167 verhelpt het probleem waarbij de massaactie van het beheerderordaster niet van toepassing is op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 geïnstalleerd is. De patch-id is MDVA-43167. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De handeling Rastermassa van beheerdervolgorde is niet van toepassing op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert.

<u> Stappen om </u> te reproduceren:

1. Schaf drie keer een product aan om drie bestellingen te maken.
1. Navigeer aan **Net van de Orde van de Verkoop**.
1. Wijzig de paginering in een aangepaste waarde 2.
1. Selecteer alles.
1. Selecteer **Actie van de Massa van de Greep**.

<u> Verwachte resultaten </u>:

Alle drie de orden worden geplaatst op greep.

<u> Ware resultaten </u>:

Slechts worden de twee zichtbare orden geplaatst op greep.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

---
title: 'MDVA-42269: Admin-gebruiker kan zich niet aanmelden bij Admin vanwege de fout TypeError'
description: De MDVA-42269-patch verhelpt het probleem waarbij Admin-gebruikers zich vanwege TypeError niet kunnen aanmelden bij Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 is geïnstalleerd.  De patch-id is MDVA-42269.  De meest recente patchupdate vindt u in QPT 1.1.15. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Admin Workspace
role: Admin
exl-id: 42ad4bb5-950f-476d-bf55-931b38bcb937
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-42269: Admin-gebruiker kan zich niet aanmelden bij Admin vanwege de fout TypeError

De MDVA-42269-patch verhelpt het probleem waarbij Admin-gebruikers zich vanwege TypeError niet kunnen aanmelden bij Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 geïnstalleerd is.  De patch-id is MDVA-42269.  De meest recente patchupdate vindt u in QPT 1.1.15. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1, 2.3.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruikers van Admin kunnen niet in Admin wegens de volgende fout registreren: *TypeError: strtotime () verwacht parameter 1 om koord te zijn, ongeldig gegeven.*

<u> Stappen om </u> te reproduceren:

Meld u aan bij de Commerce-beheerder.

<u> Verwachte resultaten </u>:

De beheerder kan zich aanmelden met de juiste gebruikersnaam en het juiste wachtwoord.

<u> Ware resultaten </u>:

De beheerder kan zich niet aanmelden. De volgende fout wordt geregistreerd: *TypeError: strtotime () verwacht parameter 1 om koord te zijn, ongeldig gegeven.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

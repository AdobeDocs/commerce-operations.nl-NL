---
title: 'MDVA-39305: Aanmeldingsprobleem met ingeschakelde Google reCAPTCHA'
description: Pas de MDVA-39305-patch toe om het Adobe Commerce-probleem op te lossen waarbij geregistreerde klanten zich niet kunnen aanmelden wanneer Google reCAPTCHA is ingeschakeld.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 007fcb1308ba2c5b42755ee4c4c2ca598eb0e62e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305: Aanmeldingsprobleem met ingeschakelde Google reCAPTCHA

>[!NOTE]
>
>Deze patch is bijgewerkt en de nieuwste patch-id is MDVA-39305-V3. De nieuwe patch wordt gemaakt voor Adobe Commerce-versies 2.4.4, 2.4.5-p2 en 2.4.7. Voor meer informatie, verwijs naar [ mDVA-39305-V3 ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha) flardartikel.

De MDVA-39305-patch verhelpt het probleem dat geregistreerde klanten zich niet kunnen aanmelden wanneer Google reCAPTCHA is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 wordt geïnstalleerd. De patch-id is MDVA-39305. Het probleem is opgelost in Adobe Commerce versie 2.4.4 en 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce on cloud Infrastructure 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geregistreerde klanten kunnen zich niet aanmelden met de ingeschakelde Google reCAPTCHA.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Veiligheid** > **Google reCAPTCHA Storefront** en laat **Google reCAPTCHA** toe.
1. Ga naar **Frontend**.
1. Open **Console van het Hulpmiddel van de Ontwikkelaar** in browser.

<u> Verwachte resultaten </u>:

Geen CSP waarschuwingen in de console.

<u> Ware resultaten </u>:

CSP waarschuwingen in de console.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

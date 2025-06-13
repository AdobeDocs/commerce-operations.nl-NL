---
title: 'ACSD-52277: Admin-gebruiker wordt onjuist omgeleid bij het selecteren van de winkelweergave bij het maken van een nieuwe bestelling'
description: Pas de ACSD-52277-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder niet correct wordt omgeleid nadat hij de winkelweergave heeft geselecteerd bij het maken van een nieuwe bestelling in Admin.
exl-id: 61ef59a9-7a31-441f-a763-2d8016498fa7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277: Admin-gebruiker wordt onjuist omgeleid bij het selecteren van de winkelweergave bij het maken van een nieuwe bestelling

De ACSD-52277-patch verhelpt het probleem dat een beheerder niet correct wordt omgeleid nadat hij de winkelweergave heeft geselecteerd bij het maken van een nieuwe bestelling in Admin. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 wordt geïnstalleerd. De patch-id is ACSD-52277. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder wordt niet correct omgeleid nadat hij tijdens het maken van een nieuwe bestelling de winkelweergave heeft geselecteerd.

<u> Stappen om te reproduceren </u>

1. Installeer een schone instantie.
1. Maak een product.
1. Maak een extra website, één winkel en twee winkelweergaven.
1. Creeer een orde van Admin door *opslagmening 1 te selecteren*.

<u> Verwachte resultaten </u>:

De gebruiker wordt omgeleid aan de ordepagina.

<u> Ware resultaten </u>:

Nadat u de winkelweergave hebt geselecteerd, wordt de gebruiker niet omgeleid naar de bestelpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

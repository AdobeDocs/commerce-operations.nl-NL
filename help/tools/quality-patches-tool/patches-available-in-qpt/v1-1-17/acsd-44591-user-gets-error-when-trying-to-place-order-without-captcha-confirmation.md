---
title: 'ACSD-44591: fouten bij bestelling zonder CAPTCHA-bevestiging'
description: De ACSD-44591-patch lost het probleem op waarbij de gebruiker fouten krijgt bij het plaatsen van een bestelling zonder CAPTCHA-bevestiging.
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591: fouten bij bestelling zonder CAPTCHA-bevestiging

De ACSD-44591-patch lost het probleem op waarbij de gebruiker fouten krijgt bij het plaatsen van een bestelling zonder CAPTCHA-bevestiging.
Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-44591. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker krijgt fouten wanneer hij of zij een bestelling probeert te plaatsen zonder CAPTCHA-bevestiging.

<u> Stappen om </u> te reproduceren:

1. Configureer Google ReCaptcha v2 (ik ben geen robot).
1. Enable ReCaptcha for checkout.
1. Probeer een bestelling te plaatsen zonder op de ReCaptcha te klikken.
1. Zodra u het foutenbericht voor het missen ReCaptcha (*ontbroken bevestiging ReCaptcha ontvangt, gelieve te proberen opnieuw*), op **ReCaptcha** te klikken en dan te proberen plaatsend een orde.

<u> Verwachte resultaten </u>:

De orde zal niet met onjuiste ReCaptcha worden geplaatst.

<u> Ware resultaten </u>:

U krijgt de volgende fouten:

* *Bevestiging ReCaptcha ontbrak, gelieve opnieuw te proberen*
* *Geen zulk karretje met identiteitskaart = 1*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

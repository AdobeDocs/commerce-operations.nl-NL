---
title: 'ACSD-60788: De manuscripten van de douane voor  [!DNL Google Tag Manager]  niet uitgevoerd toe te schrijven aan CSP fouten'
description: Pas ACSD-60788 flard toe om de kwestie van Adobe Commerce te bevestigen waar de douanemanuscripten voor  [!DNL Google Tag Manager]  niet wegens de fouten van het Beleid van de Veiligheid van de Inhoud (CSP) worden uitgevoerd.
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-60788: Aangepaste scripts voor [!DNL Google Tag Manager] worden niet uitgevoerd vanwege fouten in het inhoudsbeveiligingsbeleid

De ACSD-60788-patch verhelpt het probleem dat aangepaste scripts voor [!DNL Google Tag Manager] niet worden uitgevoerd vanwege fouten in het inhoudsbeveiligingsbeleid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-60788. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepaste scripts voor [!DNL Google Tag Manager] worden niet uitgevoerd vanwege CSP-fouten (Content Security Policy).

<u> Stappen om </u> te reproduceren:

1. Stel de variabele *[!DNL Google Tag Manager]* in.
1. Stel de aangepaste HTML-tag *[!DNL Google Tag Manager]* in.
1. Plaats de volgende JavaScript-code in de eerste tag:

   ```xml
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. De geheime voorgeheugens van de duw na vestiging *GTM*.
1. Open de ontwikkelaarsconsole in uw browser.
1. Open de startpagina.

<u> Verwachte resultaten </u>:

Browser ontwikkelt consolevertoningen *Nonce van eenvoudige JS (willekeurige karakters)*.

<u> Ware resultaten </u>:

Browser dev consolevertoningen *Nonce van eenvoudige JS niet gedefiniëerd*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'MDVA-40401: Veranderingen van de gebruikswaarde van coupon na mislukte orde'
description: De patch MDVA-40401 verhelpt de kwestie waar de waarde van het coupongebruik verandert, zelfs na een mislukte bestelling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40401. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: bc8eedd6-977f-4f21-bcd1-b5f6c4a6704f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40401: Veranderingen van de gebruikswaarde van coupon na mislukte orde

De patch MDVA-40401 verhelpt de kwestie waar de waarde van het coupongebruik verandert, zelfs na een mislukte bestelling. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-40401. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen de coupon niet opnieuw toepassen als ze deze in een mislukte volgorde hebben gebruikt.

<u> Stappen om </u> te reproduceren:

1. Maak een winkelwagentregel met automatisch gegenereerde coupons.
1. Voeg een product toe aan de winkelwagentje en pas de coupon toe.
1. Ga naar **Controle**.
1. Maak het toegevoegde product &quot;uit voorraad&quot; voordat u de bestelling plaatst.
1. U zou een *uit voorraad* fout moeten krijgen.
1. Uitsnijden uitvoeren.
1. Ga naar de kar en verwijder dat product.
1. Voeg nog een product toe en pas de coupon toe.

<u> Verwachte resultaten </u>:

De couponcode moet correct worden toegepast omdat de vorige volgorde niet is geplaatst.

<u> Ware resultaten </u>:

U krijgt de code van de a *coupon ongeldig* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.

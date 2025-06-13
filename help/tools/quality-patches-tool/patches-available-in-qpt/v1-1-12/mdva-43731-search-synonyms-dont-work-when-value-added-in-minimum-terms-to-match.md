---
title: 'MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in "Minimumtermijnen aan Gelijke"wordt toegevoegd'
description: De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in "Minimumvoorwaarden voor overeenkomst". Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in &quot;Minimumtermijnen aan Gelijke&quot;wordt toegevoegd

De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Zoeksynoniemen werken niet meer wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met voorbeeldgegevens.
1. Configureer Elasticsearch7 als zoekengine.
1. Zoek naar het woord &quot;Jasje&quot;. Er wordt een lijst met producten weergegeven.
1. Voeg de parameter [ 4&lt;60% ] in **Configuratie** toe > **Catalogus** > **het Onderzoek van de Catalogus** > **Minimale Termen om** aan te passen.
1. Wis het Geheime voorgeheugen Config en doe een herdex.
1. Zoek opnieuw naar het woord &quot;Jasje&quot;. U ziet dat er een lijst met producten wordt weergegeven.
1. Ga naar **Marketing** > **SEO &amp; Onderzoek** > **Synoniemen van het Onderzoek**.
1. Creeer de Synoniemen van het Onderzoek door de volgende synoniemen toe te voegen: jasje, bagtecs, express plus.
1. Voer een herindex uit.
1. Zoek een product met een van de synoniemen. Bijvoorbeeld jasje.

<u> Verwachte resultaten </u>:

Je krijgt dezelfde productlijst als voorheen in de zoekresultaten.

<u> Ware resultaten </u>:

Er wordt geen product weergegeven in de zoekresultaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

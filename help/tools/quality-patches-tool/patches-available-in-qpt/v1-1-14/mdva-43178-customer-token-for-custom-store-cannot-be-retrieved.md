---
title: 'MDVA-43178: Klanttoken voor aangepast archief kan niet worden opgehaald in GraphQL'
description: De patch MDVA-43178 verhelpt het probleem waarbij de token voor de klant van een aangepaste store niet kan worden opgehaald in GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43178. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178: Klanttoken voor aangepast archief kan niet worden opgehaald in GraphQL

De patch MDVA-43178 verhelpt het probleem waarbij de token voor de klant van een aangepaste store niet kan worden opgehaald in GraphQL. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43178. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanttoken voor een aangepaste winkel kan niet worden opgehaald in GraphQL.

<u> Stappen om </u> te reproduceren:

1. Maak twee winkelweergaven voor de standaardwinkel.
1. Maak een nieuwe website, één winkel en één winkelweergave. Geef deze winkelweergave de naam &#39;test3&#39;.
1. Maak een klant voor de nieuwe website.
1. API-beheertoken genereren:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    &lbrace;
      "username": "login",
      "password": "password"
    &rbrace;
    </code>
    </pre>

1. Verzend GraphQL om klantentoken als beheerder op te halen, gebruik de beheertoken voor verificatie, met &quot;store&quot; = &quot;test3&quot; in de header:

   <pre>
    <customer_email>
      </pre>

<u> Verwachte resultaten </u>:

Klanttoken wordt gegenereerd.

<u> Ware resultaten </u>:

Klanttoken wordt niet gegenereerd. De handelaars krijgen *verstrekte de e-mail van de Klant bestaat niet* in antwoord.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

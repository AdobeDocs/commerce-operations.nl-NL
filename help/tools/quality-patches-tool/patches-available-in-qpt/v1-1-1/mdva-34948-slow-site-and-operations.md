---
title: 'MDVA-34948: Verlichting website'
description: De MDVA-34948 Adobe Commerce patch verhelpt het probleem van de vertraging van de website. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 is geïnstalleerd. De patch-id is MDVA-34948. Het probleem is opgelost in Adobe Commerce versie 2.4.1.
feature: Observability, Configuration
role: Admin
exl-id: 3c2a2d44-7d60-42da-a0a3-785fb61d571e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# MDVA-34948: Verlichting website


## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op onze cloudinfrastructuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce op locatie en Adobe Commerce op onze cloud-infrastructuur 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De website wordt langzaam, wat bewerkingen belemmert.

<u> Stappen om </u> te reproduceren:

1. Voer `show processlist` uit in MySQL.
1. Controleer of er meerdere query&#39;s zijn zoals:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u> Verwachte resultaten </u>:

`GET_LOCK` moet onmiddellijk worden uitgevoerd.

<u> Ware resultaten </u>:

Meerdere `GET_LOCK` query&#39;s blijven maximaal 10 seconden vastzitten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.

---
title: 'MDVA-42689: Gebruikers krijgen een fout wegens schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren'
description: De MDVA-42689-patch lost het probleem op waarbij gebruikers een fout wegens schending van integriteitsbeperking krijgen tijdens het bijwerken van productcategorieën tijdens het importeren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689: Gebruikers krijgen een fout wegens schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren

De MDVA-42689-patch lost het probleem op waarbij gebruikers een fout wegens schending van integriteitsbeperking krijgen tijdens het bijwerken van productcategorieën tijdens het importeren. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-42689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Adobe Commerce genereert een fout met betrekking tot schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren.

<u> Stappen om </u> te reproduceren:

1. Stel twee websites in.
1. Maak subcategorieën onder de hoofdcategorie tot twee niveaus op de categoriepagina. Bijvoorbeeld, de Categorie van de Wortel > **Vliegen** > **horloges**.
1. Creeer twee eenvoudige producten en wijs zowel de producten aan zelfde **gear** toe > **Watches** categorie.
1. Wijs één eenvoudig product aan beide websites toe.
1. Sla het product op.
1. Een CSV-bestand voorbereiden voor importeren. Er moeten twee productrecords met verschillende winkelweergaven zijn. Een van de producten moet bij beide winkelweergaven horen.
1. Importeer nu het CSV-bestand door te navigeren naar **System** > **Import** > **Type entiteit** (Producten).

<u> Verwachte resultaten </u>:

CSV-bestand wordt zonder fout geïmporteerd.

<u> Ware resultaten </u>:

Adobe Commerce genereert de volgende fout:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-53583: De gedeeltelijke herindexprestaties voor [!UICONTROL Category Products] en [!UICONTROL Product Categories] indexers verbeteren'
description: Pas de ACSD-53585-patch toe om de gedeeltelijke herindexprestaties voor de indexen van de Categorieën van Producten en van de Categorieën te verbeteren.
feature: Products, Categories
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-53583: Verbeteren van de gedeeltelijke herindexeerprestaties voor de indexen van de Producten van de Categorie en van de Categorieën

ACSD-53583 flard verbetert de gedeeltelijke herindexprestaties van *Producten van de Categorie* en *Categorieën van het Product* indexeerders. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-53583. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3
* Niet compatibel met de module [!DNL Live Search] . Vraag een extra ACSD-55719-patch om deze patch op de installatie van [!DNL Live Search] toe te passen.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gedeeltelijke herdex vergt meer tijd dan volledige herdex.

<u> Stappen om </u> te reproduceren:

1. Draai alle indexen aan *Update door Programma*.
1. Genereer gegevens met [!DNL Performance Toolkit] (normaal profiel).
1. Breng wijzigingen aan in alle producten en categorieën, zodat deze zich in de indexachterstand bevinden en alle indexen inactief zijn.
1. Voer gedeeltelijke herindex voor *Producten van de Categorie* en *Categorieën van het Product* indexeerders uit.

<u> Verwachte resultaten </u>:

Gedeeltelijke herdex wordt één keer per product aangeroepen en neemt bijna dezelfde tijd in beslag als volledige herdex, omdat alle producten en categorieën zijn gewijzigd.

<u> Ware resultaten </u>:

Partiële redex wordt vele malen per product aangeroepen en neemt meer tijd in beslag dan volledige redex.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
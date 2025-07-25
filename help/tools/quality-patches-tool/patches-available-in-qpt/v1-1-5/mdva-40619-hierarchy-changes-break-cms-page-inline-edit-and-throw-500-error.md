---
title: 'MDVA-40619: Hiërarchiewijzigingen breken CMS pagina inline uit bewerken en genereren 500 fouten'
description: De MDVA-40619-patch lost het probleem op waarbij de wijzigingen in de CMS-paginahiërarchie inline bewerken van CMS-pagina's afbreken en "500 error" genereren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40619. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40619: Hiërarchiewijzigingen breken CMS pagina inline uit bewerken en genereren 500 fouten

De MDVA-40619-patch lost het probleem op waarbij de wijzigingen in de CMS-paginahiërarchie inline bewerken van CMS-pagina&#39;s afbreken en &quot;500 error&quot; genereren. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-40619. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wijzigingen in CMS-paginahiërarchie zorgen voor inline bewerking van CMS-pagina en genereren &quot;500 error&quot;.

<u> Stappen om </u> te reproduceren:

1. Ga naar het Comité Admin > **Inhoud** > **Hiërarchie**.
1. Selecteer Standaardwinkelweergave.
1. Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
1. Selecteer manueel pagina en klik **sparen**.
1. Dan ga naar **Inhoud** > **Pagina&#39;s**.
1. Probeer een CMS-pagina uit het raster te bewerken.
1. Klik **sparen**.

<u> Verwachte resultaten </u>:

Pagina is opgeslagen.

<u> Ware resultaten </u>:

De volgende fout treedt op:

*Een technisch probleem met de server leidde tot een fout. Probeer opnieuw om door te gaan wat u aan het doen was. Probeer het later opnieuw als het probleem zich blijft voordoen.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.

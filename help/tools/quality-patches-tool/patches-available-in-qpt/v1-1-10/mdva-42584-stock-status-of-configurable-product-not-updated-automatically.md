---
title: 'MDVA-42584: voorraadstatus van configureerbaar product niet automatisch bijgewerkt'
description: De MDVA-42584-patch lost het probleem op waarbij de voorraadstatus van het configureerbare product niet automatisch wordt bijgewerkt wanneer het eenvoudige product wordt bijgewerkt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 is geïnstalleerd. De patch-id is MDVA-42584. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584: voorraadstatus van configureerbaar product niet automatisch bijgewerkt

De MDVA-42584-patch lost het probleem op waarbij de voorraadstatus van het configureerbare product niet automatisch wordt bijgewerkt wanneer het eenvoudige product wordt bijgewerkt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 geïnstalleerd is. De patch-id is MDVA-42584. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de voorraad van het configureerbare product in het backend wordt niet automatisch bijgewerkt wanneer zijn eenvoudig product aan **in Voorraad** door API of de invoer wordt geplaatst.

<u> Eerste vereisten </u>:

MSI geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product, **InvCheck001**, met twee opties: **InvCheck001-M** en **InvCheck001-L**.
1. Zowel zouden de eenvoudige producten Hoeveelheid moeten hebben en zij zouden **in Voorraad** moeten zijn zodat het configureerbare product ook **in Voorraad** in het achterste eind is.
1. Nu, werk zowel eenvoudige producten bij en plaats Hoeveelheid aan **0** en de Status van de Voorraad aan **uit Voorraad**.
1. Vernieuw het configureerbare product en verifieer de voorraadstatus wordt bijgewerkt aan **uit Voorraad**.
1. Gebruik het volgende API eindpunt en plaats het eenvoudige product **InvCheck001-M** aan **In Voorraad** met Aantal > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Ga naar het achterste eind en verifieer de hoeveelheid en voorraadstatus van het eenvoudige product **InvCheck001-M**. Het wordt bijgewerkt aan **In voorraad**.
1. Vernieuw het configureerbare product en controleer de voorraadstatus.

<u> Verwachte resultaten </u>:

De voorraadstatus van het configureerbare product **InvCheck001** in het achterste wordt bijgewerkt automatisch aan **in Voorraad**.

<u> Ware resultaten </u>:

De voorraadstatus van het configureerbare product is nog **uit Voorraad**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

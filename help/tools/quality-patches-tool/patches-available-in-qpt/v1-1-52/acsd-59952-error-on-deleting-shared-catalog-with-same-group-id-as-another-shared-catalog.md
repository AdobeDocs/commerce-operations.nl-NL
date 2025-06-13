---
title: 'ACSD-59952: Fout bij verwijderen van gedeelde catalogus met dezelfde groep-id als een andere gedeelde catalogus'
description: Pas de ACSD-59952-patch toe om het Adobe Commerce-probleem op te lossen waarbij een fout optreedt bij het verwijderen van een gedeelde catalogus met dezelfde ` customer_group_id' als een andere gedeelde catalogus.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952: Fout bij verwijderen van gedeelde catalogus met dezelfde groep-id als een andere gedeelde catalogus

De ACSD-59952-patch corrigeert de fout die is opgetreden bij het verwijderen van gedeelde catalogi met dezelfde `customer_group_id` als een andere gedeelde catalogus. Bovendien wordt hiermee voorkomen dat gebruikers dergelijke gedeelde catalogi maken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-59952. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er kan geen nieuwe gedeelde catalogus met dezelfde `customer_group_id` als een andere gedeelde catalogus worden gemaakt. Als u echter tegelijkertijd probeert de gedeelde catalogus met dezelfde `customer_group_id` te verwijderen, treedt een fout op.

<u> Eerste vereisten </u>:

Installeer de Adobe Commerce B2B-modules.

<u> Stappen om </u> te reproduceren:

1. Maak meerdere gedeelde catalogi die aan dezelfde `customer_group_id` zijn toegewezen met behulp van de volgende REST API-aanroep:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Probeer om het even welke gedeelde catalogi te schrappen gebruikend de volgende REST API vraag:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u> Verwachte resultaten </u>:

* Het is niet mogelijk meerdere gedeelde catalogi te maken die aan dezelfde `customer_group_id` zijn toegewezen.
* De gedeelde catalogus in het bovenstaande geval wordt verwijderd.

<u> Ware resultaten </u>:

* Het is mogelijk meerdere gedeelde catalogi te maken die aan dezelfde `customer_group_id` zijn toegewezen.
* De volgende fout is teruggekeerd wanneer het proberen om de gedeelde catalogus met het zelfde `customer_group_id` te schrappen: *kan gedeelde catalogus* schrappen niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-63139: Exporteren van product mislukt als productkenmerken duizenden optiewaarden bevatten'
description: Pas de ACSD-63139-patch toe om het Adobe Commerce-probleem op te lossen waarbij het exporteren van producten mislukt wanneer productkenmerken duizenden optiewaarden bevatten.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-63139: Exporteren van product mislukt als productkenmerken duizenden optiewaarden bevatten

De ACSD-63139-patch verhelpt het probleem waarbij het exporteren van producten mislukt wanneer productkenmerken duizenden optiewaarden bevatten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-63139. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van het product mislukt wanneer productkenmerken duizenden optiewaarden bevatten.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met de B2B-module.
1. Importeer een grote databasedumpit met:
   - ~7.000 producten
   - ~450 productkenmerken
   - Sommige kenmerken hebben meer dan 100 opties
1. Voer de volgende opdracht uit om de installatie uit te voeren (als deze nog niet is geïnstalleerd):

   ```shell
   bin/magento cron:install
   ```

1. Vorm [!DNL RabbitMQ] door de instructies in [[!DNL RabbitMQ]  eerste vereisten ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/message-brokers/rabbitmq) te volgen.
1. Open het bestand `php.ini` , stel de geheugenlimiet in op 4G en start de PHP-service opnieuw.
1. Ga in het deelvenster Beheer naar **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]** .
1. In de *[!UICONTROL Export Settings]* sectie, plaats **[!UICONTROL Entity Type]** aan *Producten*, scrol aan de bodem en klik **[!UICONTROL Continue]**.
1. Voer de volgende opdracht uit om de exportprocessor te starten:

   ```shell
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u> Verwachte resultaten </u>:

Het exporteren van het product moet zijn voltooid.

<u> Ware resultaten </u>:

Het exportproces van het product mislukt en retourneert de volgende fatale fout:

```text
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

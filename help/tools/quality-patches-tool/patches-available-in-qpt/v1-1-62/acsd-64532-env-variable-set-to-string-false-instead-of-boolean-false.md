---
title: 'ACSD-64532: ENV-variabele ingesteld op *false* wordt behandeld als een tekenreeks *false* in plaats van een BOOLEAN *FALSE*'
description: Pas de ACSD-64532-patch toe om het Adobe Commerce-probleem op te lossen waarbij een 'ENV'-variabele ingesteld op *false* wordt behandeld als een tekenreeks *false* in plaats van een 'BOOLEAN&grave; *FALSE*.
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532: ENV-variabele ingesteld op &quot;false&quot; wordt behandeld als een tekenreeks &quot;false&quot; in plaats van een BOOLEAN FALSE

ACSD-64532 herstelt de flard de kwestie waar de `ENV` variabele die aan *wordt geplaatst vals* als koord *vals* in plaats van a `BOOLEAN` *VALS* wordt behandeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 wordt geïnstalleerd. De patch-id is ACSD-64532. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**
Adobe Commerce (alle implementatiemethoden) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`ENV` variabele die aan *wordt geplaatst vals* wordt behandeld als een koord *vals* in plaats van a `BOOLEAN` *VALS*.

<u> Stappen om </u> te reproduceren:
1. Voeg `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` met waarde *vals* aan milieuvariabelen op Adobe Commerce op wolkeninfrastructuur toe.
1. Wacht op herschikking.
1. Voer het script uit om de waarde te controleren:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u> Verwachte resultaten </u>:
`$configParsedValue` , dat het resultaat is van methode `isUseApplicationLock()` , moet een negatieve waarde retourneren om correct te worden geïnterpreteerd binnen methode `\Magento\Indexer\Model\Mview\View\State::getStatus()` .

<u> Ware resultaten </u>:
`$configParsedValue` heeft de waarde *`string(5) false`* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:
* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

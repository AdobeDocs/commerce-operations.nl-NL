---
title: Patch controleren voor Adobe Commerce-probleem met het gereedschap Kwaliteitspatches
description: In dit artikel vindt u een overzicht van het gereedschap Kwaliteitspatches (QPT) en koppelingen naar bronnen waarin wordt uitgelegd hoe u het gereedschap kunt gebruiken.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Patch controleren voor Adobe Commerce-probleem met het gereedschap Kwaliteitspatches

In dit artikel vindt u een overzicht van het gereedschap Kwaliteitspatches (QPT) en koppelingen naar bronnen waarin wordt uitgelegd hoe u het gereedschap kunt gebruiken.

## Betrokken producten en versies

* Adobe Commerce op-gebouw, alle [&#x200B; gesteunde versies &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce op wolkeninfrastructuur, alle [&#x200B; gesteunde versies &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Wat is het gereedschap Kwaliteitspatches

Het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit &#x200B;](https://github.com/magento/quality-patches) (QPT) zijn individuele die flarden door Adobe en de gemeenschap van Magento Open Source worden ontwikkeld.

Zo kunt u:

* past meegeleverde kwaliteitspatches toe op het pakket
* eerder toegepaste patches herstellen
* Bekijk de algemene informatie over kwaliteitspatches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce.

Hier is een voorbeeld van de statuslijst u kunt krijgen om de beschikbare flarden te bekijken:

![&#x200B; de statuslijst van het Hulpmiddel van Patches van de Kwaliteit die beschikbare flarden en hun installatiestatus tonen &#x200B;](/help/assets/tools/status_table.png)

Het gereedschap is bedoeld om u in staat te stellen zelf te dienen met patches voor problemen die u kunt ervaren met Adobe Commerce, of om eenvoudig patches toe te passen die worden voorgesteld door Adobe Commerce-ondersteuning.

>[!NOTE]
>
>QPT is alleen voor kwaliteitspatches. De flarden van de veiligheid zijn beschikbaar in het [&#x200B; Centrum van de Veiligheid van Magento &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/notes/overview).

## Patches beschikbaar in het gereedschap Kwaliteitspatches

Gelieve te verwijzen naar [&#x200B; Hulpmiddel van de Patches van de Kwaliteit &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie voor de lijst van beschikbare flarden.

## Het gereedschap Kwaliteitspatches installeren en gebruiken

De installatie- en gebruiksopdrachten verschillen voor Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur, omdat voor cloud het QPT-pakket is opgenomen in het ece-tools-pakket.

### QPT voor Adobe Commerce installeren en gebruiken op locatie

Gelieve te verwijzen naar [&#x200B; Gids van de Update van de Software > het Patching &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelaarsdocumentatie voor details op hoe te om QPT voor het toepassen van en het terugkeren van flarden te installeren en te gebruiken.

### QPT voor Adobe Commerce installeren en gebruiken op cloudinfrastructuur

Gelieve te verwijzen naar [&#x200B; Wolk voor Adobe Commerce > pas flarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie voor details op om QPT voor het toepassen en het terugkeren van flarden op Adobe Commerce op wolkeninfrastructuur te installeren en te gebruiken.

## Gerelateerde lezing

* [&#x200B; de versienota&#39;s van het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/release-notes) in onze ontwikkelaarsdocumentatie.
* [&#x200B; hoe te om componentenflarden toe te passen die door Adobe &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) in de steunkennisbasis worden verstrekt.

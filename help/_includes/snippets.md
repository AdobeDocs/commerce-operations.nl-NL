---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Fragmenten

## Alleen handel {#commerce-only}

>[!NOTE]
>
>De [!DNL Upgrade Compatibility Tool] is alleen beschikbaar voor Adobe Commerce-instanties.

<!-- Configuration guide snippets -->

## Eigenaar van bestandssysteem {#file-system-owner}

>[!WARNING]
>
>Alle bevelen van Magento CLI moeten door de [eigenaar van bestandssysteem](/help/configuration/cli/config-cli.md#prerequisites).

## Back-upopdrachten {#tip-backup-command}

>[!TIP]
>
>De `support:backup` command is _niet_ dezelfde codeback-up die door de `setup:backup` gebruiken. De `support:backup` is bedoeld als back-up van code die door Adobe Commerce Support kan worden gecontroleerd.

## Alleen Adobe Commerce {#ee-only}

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor Adobe Commerce-instanties.

## Gesplitste database afgekeurd {#deprecate-split-db}

>[!IMPORTANT]
>
>De functie voor gesplitste databases was [verouderd](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) in versie 2.4.2 van Adobe Commerce. Zie [Herstel van een gesplitste database naar één database](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Achteruit incompatibele wijzigingen {#bics}

>[!NOTE]
>
>Adobe Commerce- en Magento Open Source-releases kunnen achterwaartse incompatibele wijzigingen (BIC&#39;s) bevatten. Als u wijzigingen die niet compatibel zijn met oudere versies wilt bekijken, raadpleegt u [BIC-referentie](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Belangrijke problemen die niet compatibel zijn met oudere versies worden beschreven in [BIC-hooglichten](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Niet alle introducties introduceren grote BIC&#39;s.

## CVE-kennisgeving {#cve-notice}

>[!NOTE]
>
>Vanaf de versie 2.3.2 wijzen we geïndexeerde CVE-nummers (Common Vulnerabilities and Exposure) toe aan en publiceren we deze voor elke beveiligingsfout die door externe partijen aan ons wordt gemeld. Hierdoor kunnen gebruikers gemakkelijker niet-verholpen kwetsbaarheden in hun implementatie identificeren. Meer informatie over CVE-id&#39;s vindt u op [CVE](https://cve.mitre.org/).

---
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '273'
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
>Alle Magento CLI bevelen moeten door worden in werking gesteld [eigenaar van bestandssysteem](/help/configuration/cli/config-cli.md#prerequisites).

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

## Overige releasegegevens {#other-release-info}

>[!NOTE]
>
>Hoewel de code voor verhogingen en insectenmoeilijke situaties die in deze versienota&#39;s worden beschreven met Adobe Commerce worden gebundeld, worden verscheidene van deze projecten (bijvoorbeeld, B2B, de Bouwer van de Pagina, en de Studio van Progressive Webben Application (PWA) ook vrijgegeven onafhankelijk. De fixes van de insect voor deze projecten worden gedocumenteerd in de afzonderlijke, project-specifieke versieinformatie die in de documentatie voor elk project beschikbaar is. Zie [overzicht van productrelease](/help/release/release-notes/overview.md).

## PHP Process Control {#php-process-control}

Voordat u indexen kunt uitvoeren in parallelle modus, moet u ondersteuning voor procesbesturing inschakelen (`pcntl`) in PHP. Zie [Installatie](https://www.php.net/manual/en/pcntl.installation.php) in de PHP documentatie.

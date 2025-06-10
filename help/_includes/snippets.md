---
source-git-commit: 102fee9672c75c94c7d18d47562338f8eff97f11
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---
# Fragmenten

## Alleen Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] is alleen beschikbaar voor Adobe Commerce-instanties.

<!-- Configuration guide snippets -->

## Eigenaar van bestandssysteem {#file-system-owner}

>[!WARNING]
>
>Alle bevelen van Magento CLI moeten door de [ eigenaar van het dossiersysteem ](/help/configuration/cli/config-cli.md#prerequisites) worden in werking gesteld.

## Back-upopdrachten {#tip-backup-command}

>[!TIP]
>
>Het `support:backup` bevel is _niet_ de zelfde die codesteun door het `setup:backup` bevel wordt uitgevoerd. De opdracht `support:backup` is bedoeld om een back-up te maken van code voor onderzoek door Adobe Commerce Support.

## B2B-patches {#b2b-patches}

>[!NOTE]
>
>Nadat u deze beveiligingspatch hebt geïnstalleerd, moeten Adobe Commerce B2B-handelaren ook een update uitvoeren naar de nieuwste compatibele B2B-beveiligingspatchrelease. Zie [ B2B versienota&#39;s ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/release-notes).

## Alleen Adobe Commerce {#ee-only}

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor Adobe Commerce-instanties.

## Gesplitste database afgekeurd {#deprecate-split-db}

>[!IMPORTANT]
>
>De gespleten gegevensbestandeigenschap was [ afgekeurd ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) in versie 2.4.2 van Adobe Commerce. Zie [ terugkeren van een gespleten gegevensbestand aan één enkel gegevensbestand ](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Achteruit incompatibele wijzigingen {#bics}

>[!NOTE]
>
>Adobe Commerce-releases kunnen niet-compatibele wijzigingen (BIC&#39;s) bevatten. Om achteruit-onverenigbaar veranderingen te herzien, zie [ verwijzing BIC ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). De grote achteruit-onverenigbaar kwesties worden beschreven in [ hoogtepunten BIC ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Niet alle introducties introduceren grote BIC&#39;s.

## Alpha disclaimer {#alpha}

>[!IMPORTANT]
>
>[ de versies van Alpha ](/help/release/versioning-policy.md#alpha-patch-release) kunnen onvolledig zijn, en zullen waarschijnlijk gebreken bevatten. Ze worden geleverd &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om Alpha-releases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten mogen niet vertrouwen op de correcte werking of prestaties van Alpha-releases of begeleidende documentatie of materialen. Het gebruik van Alpha-releases is volledig op eigen risico van de klant.

## Beta disclaimer {#beta}

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (van Adobe Support Services of een andere service). Klanten moeten voorzichtig zijn en op geen enkele wijze vertrouwen op de correcte werking of prestaties van bètareleases en/of begeleidende documentatie of materialen. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## CVE-kennisgeving {#cve-notice}

>[!NOTE]
>
>Vanaf de versie 2.3.2 wijzen we geïndexeerde CVE-nummers (Common Vulnerabilities and Exposure) toe aan en publiceren we deze voor elke beveiligingsfout die door externe partijen aan ons wordt gemeld. Hierdoor kunnen gebruikers gemakkelijker niet-verholpen kwetsbaarheden in hun implementatie identificeren. U kunt meer over CVE herkenningstekens bij [ CVE ](https://cve.mitre.org/) leren.

## Overige releasegegevens {#other-release-info}

>[!NOTE]
>
>Hoewel de code voor verhogingen en insectenmoeilijke situaties die in deze versienota&#39;s worden beschreven met Adobe Commerce worden gebundeld, worden verscheidene van deze projecten (bijvoorbeeld, B2B, de Bouwer van de Pagina, en de Progressieve Studio van het Web (PWA)) ook vrijgegeven onafhankelijk. De fixes van de insect voor deze projecten worden gedocumenteerd in de afzonderlijke, project-specifieke versieinformatie die in de documentatie voor elk project beschikbaar is. Zie [ overzicht van de productversie ](/help/release/release-notes/overview.md).

## PHP Process Control {#php-process-control}

Voordat u indexeerders in parallelle modus kunt uitvoeren, moet u ondersteuning voor procesbesturing (`pcntl`) inschakelen in PHP. Zie [ Installatie ](https://www.php.net/manual/en/pcntl.installation.php) in de PHP documentatie.

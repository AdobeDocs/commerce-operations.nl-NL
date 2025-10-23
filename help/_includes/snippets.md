---
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '607'
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
>Alle bevelen van Magento CLI moeten door de [&#x200B; eigenaar van het dossiersysteem &#x200B;](/help/configuration/cli/config-cli.md#prerequisites) worden in werking gesteld.

## Back-upopdrachten {#tip-backup-command}

>[!TIP]
>
>Het `support:backup` bevel is _niet_ de zelfde die codesteun door het `setup:backup` bevel wordt uitgevoerd. De opdracht `support:backup` is bedoeld om een back-up te maken van code voor onderzoek door Adobe Commerce Support.

## B2B-patches {#b2b-patches}

>[!NOTE]
>
>Nadat u deze beveiligingspatch hebt geïnstalleerd, moeten Adobe Commerce B2B-handelaren ook een update uitvoeren naar de nieuwste compatibele B2B-beveiligingspatchrelease. Zie [&#x200B; B2B versienota&#39;s &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/release-notes).

## Alleen Adobe Commerce {#ee-only}

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor Adobe Commerce-instanties.

## Gesplitste database afgekeurd {#deprecate-split-db}

>[!IMPORTANT]
>
>De gespleten gegevensbestandeigenschap was [&#x200B; afgekeurd &#x200B;](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) in versie 2.4.2 van Adobe Commerce. Zie [&#x200B; terugkeren van een gespleten gegevensbestand aan één enkel gegevensbestand &#x200B;](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Achteruit incompatibele wijzigingen {#bics}

>[!NOTE]
>
>Adobe Commerce-releases kunnen niet-compatibele wijzigingen (BIC&#39;s) bevatten. Om achteruit-onverenigbaar veranderingen te herzien, zie [&#x200B; verwijzing BIC &#x200B;](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). De grote achteruit-onverenigbaar kwesties worden beschreven in [&#x200B; hoogtepunten BIC &#x200B;](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Niet alle introducties introduceren grote BIC&#39;s.

## Alpha disclaimer {#alpha}

>[!IMPORTANT]
>
>[&#x200B; de versies van Alpha &#x200B;](/help/release/versioning-policy.md#alpha-patch-release) kunnen onvolledig zijn, en zullen waarschijnlijk gebreken bevatten. Ze worden geleverd &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om Alpha-releases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten mogen niet vertrouwen op de correcte werking of prestaties van Alpha-releases of begeleidende documentatie of materialen. Het gebruik van Alpha-releases is volledig op eigen risico van de klant.

## Beta disclaimer {#beta}

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (van Adobe Support Services of een andere service). Klanten moeten voorzichtig zijn en op geen enkele wijze vertrouwen op de correcte werking of prestaties van bètareleases en/of begeleidende documentatie of materialen. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## CVE-kennisgeving {#cve-notice}

>[!NOTE]
>
>Vanaf de versie 2.3.2 wijzen we geïndexeerde CVE-nummers (Common Vulnerabilities and Exposure) toe aan en publiceren we deze voor elke beveiligingsfout die door externe partijen aan ons wordt gemeld. Hierdoor kunnen gebruikers gemakkelijker niet-verholpen kwetsbaarheden in hun implementatie identificeren. U kunt meer over CVE herkenningstekens bij [&#x200B; CVE &#x200B;](https://cve.mitre.org/) leren.

## Overige releasegegevens {#other-release-info}

>[!NOTE]
>
>Hoewel de code voor verhogingen en insectenmoeilijke situaties die in deze versienota&#39;s worden beschreven met Adobe Commerce worden gebundeld, worden verscheidene van deze projecten (bijvoorbeeld, B2B, de Bouwer van de Pagina, en de Progressieve Studio van het Web (PWA)) ook vrijgegeven onafhankelijk. De fixes van de insect voor deze projecten worden gedocumenteerd in de afzonderlijke, project-specifieke versieinformatie die in de documentatie voor elk project beschikbaar is. Zie [&#x200B; overzicht van de productversie &#x200B;](/help/release/release-notes/overview.md).

## PHP Process Control {#php-process-control}

Voordat u indexeerders in parallelle modus kunt uitvoeren, moet u ondersteuning voor procesbesturing (`pcntl`) inschakelen in PHP. Zie [&#x200B; Installatie &#x200B;](https://www.php.net/manual/en/pcntl.installation.php) in de PHP documentatie.

## Aangepaste patches {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe biedt geen ondersteuning voor het toepassen van officiële, door Adobe geleverde patches met deze methode. Gebruik de volgende methode voor eigen risico. Om officiële flarden toe te passen, gebruik [[!DNL Quality Patches Tool] &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}. Voer altijd uitgebreide tests uit voordat u een aangepaste patch implementeert.

## Oktober 2025 de flardhavens van de veiligheidsflard {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **Migreer van TinyMCE aan Hugerte.org**

  Wegens het eind van steun voor TinyMCE 5 en 6 en het verlenen van vergunningen onverenigbaarheden met TinyMCE 7, wordt de huidige implementatie van de redacteur van Adobe Commerce WYSIWYG gemigreerd van TinyMCE aan de open-bron [&#x200B; redacteur HugeRTE &#x200B;](https://hugerte.org/).

  Deze migratie zorgt ervoor dat Adobe Commerce compatibel blijft met open-sourcinglicenties, bekende TinyMCE 6-kwetsbaarheden voorkomt en een moderne, ondersteunde bewerkingservaring biedt voor handelaren en ontwikkelaars.

* **Toegevoegde steun voor Apache ActiveMQ het protocol van de STOMP van Artemis**

  Toegevoegde steun voor de open-bronberichtbroker van de Artemis van ActiveMQ Artemis door het Eenvoudige Text Oriented Messaging Protocol (STOMP). Het levert een betrouwbaar en scalable overseinensysteem, dat flexibiliteit voor op STOMP-Gebaseerde integratie biedt. Zie [&#x200B; Apache ActiveMQ Artemis &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) in de *Gids van de Configuratie van Commerce*.

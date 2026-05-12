---
title: Opmerkingen bij de release Adobe Commerce 2.4.8 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.8.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a61409b02e612295fb03a42e22dcfdf5c3eb0e57
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p5

De beveiligingsrelease van Adobe Commerce 2.4.8-p5 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.8.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB26-49 ](https://helpx.adobe.com/security/products/magento/apsb26-49.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

#### Compatibiliteit met MariaDB 11.8

Adobe Commerce 2.4.8 is gevalideerd voor compatibiliteit met MariaDB 11.8, terwijl ondersteuning voor MariaDB 11.4 behouden blijft. Deze update verhelpt SQL-gedragswijzigingen, standaardupdates en afgekeurde versies die zijn geïntroduceerd in MariaDB 11.8 om de stabiliteit van het platform te handhaven.

#### Ondersteuning voor OpenSearch 3 nieuwste secundaire versie

Adobe Commerce 2.4.8 biedt nu ondersteuning voor de nieuwste kleine versie van OpenSearch 3 op Adobe Commerce voor cloudinfrastructuur, Cloud Native en implementaties op locatie. Compatibiliteit met OpenSearch 2 blijft behouden.

#### Valkey 9.x LTS-ondersteuning

Adobe Commerce 2.4.8 is nu compatibel met Valkey 9.x LTS en biedt een back-end optie voor cache op lange termijn die op Adobe Commerce op cloudinfrastructuur wordt ondersteund.

#### Ondersteuning voor RabbitMQ 4.2

Adobe Commerce 2.4.8 is nu compatibel met RabbitMQ 4.2, die de voor februari 2026 geplande einddatum van de ondersteuning voor RabbitMQ 4.1 aanbiedt. De verenigbaarheid met Apache ActiveMQ Artemis wordt behouden, en ActiveMQ blijft de standaarddienst van de berichtrij voor deze veiligheid-slechts versielijn.

#### Ondersteuning voor REST API van USPS

De USPS-integratie voor verzending ondersteunt nu de gemoderniseerde RESTful USPS API&#39;s in aanvulling op de verouderde Web Tools API&#39;s. Beheerders kunnen in de beheerconfiguratie aangeven welke USPS-integratie-API u wilt gebruiken. Deze update bereidt de veroudering van de USPS Web Tools API voor.

#### Magento-eigenaar Laminas MVC-vork

Adobe Commerce gebruikt nu een vork in Magento van `laminas-mvc` (gepubliceerd als `magento/magento-zf-mvc` ) om de Laminas MVC-pensionering aan te pakken. Deze vork zorgt voor voortdurende patching en naleving van de langetermijnbeveiliging voor Adobe Commerce 2.4.8.

## 2.4.8-p4

De Adobe Commerce 2.4.8-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB26-05 ](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

#### Ondersteuning voor MyDHL REST API voor integratie van DHL-scheepvaart

De integratie van DHL voor scheepvaart ondersteunt nu MyDHL REST API&#39;s naast de bestaande integratie van DHL Express XML. Deze update wordt uitgelijnd op de huidige API-stapel van DHL en bereidt de veroudering van de oudere XML API&#39;s voor.

#### Compatibiliteit toevoegen met de nieuwste Composer-versie

Adobe Commerce 2.4.8 is bijgewerkt ter ondersteuning van Composer 2.9.x en blijft compatibel met Composer 2.2 LTS.

## 2.4.8-p3

De Adobe Commerce 2.4.8-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-94 ](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Oplossing voor ACP2E-3874: De REST API-reactie voor ordergegevens bevat nu de juiste waarden voor `base_row_total` - en `row_total` -kenmerken voor het geval meerdere items werden besteld.

* Oplossen voor AC-15446: Correctie van een fout in `Magento\Framework\Mail\EmailMessage` waarbij `getBodyText()` probeerde een niet-bestaande `getTextBody()` methode aan te roepen op `Symfony\Component\Mime\Message` . Dit zorgt voor compatibiliteit met Magento 2.4.8-p2 en `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

### Bekende problemen

#### De uitcheckpagina kan static.min.js en mixins.min.js niet laden.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

De Adobe Commerce 2.4.8-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-71 ](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

De Adobe Commerce 2.4.8-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-50 ](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

* **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

* **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

* **verrichtingen Async** - Beperkte async verrichtingen voor het met voeten treden van vorige klantenorden.<!-- AC-13917 -->

* **moeilijke situatie voor CVE-2025-47110** - lost een kwetsbaarheid van e-mailmalplaatjes op.<!-- AC-14695 -->

* **Repareren voor VULN-31547** - lost een categorie canonical verbindingskwetsbaarheid op.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

De correcties voor CVE-2025-47110 en VULN-31547 zijn ook beschikbaar als een geïsoleerde patch. Zie het [ artikel van de Kennisbank ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) voor details.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->

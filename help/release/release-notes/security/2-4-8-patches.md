---
title: Opmerkingen bij de release Adobe Commerce 2.4.8 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a1a8e9192dbdccbc758be972612f8a8828202299
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p4

De Adobe Commerce 2.4.8-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

#### Ondersteuning voor MyDHL REST API voor integratie van DHL-scheepvaart

De integratie van DHL voor scheepvaart ondersteunt nu MyDHL REST API&#39;s naast de bestaande integratie van DHL Express XML. Deze update wordt uitgelijnd op de huidige API-stapel van DHL en bereidt de veroudering van de oudere XML API&#39;s voor.

#### Compatibiliteit toevoegen met de nieuwste Composer-versie

Adobe Commerce 2.4.8 is bijgewerkt ter ondersteuning van Composer 2.9.x en blijft compatibel met Composer 2.2 LTS.

## 2.4.8-p3

De Adobe Commerce 2.4.8-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-94 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Correctie voor ACP2E-3874: De REST API-reactie voor orderdetails bevat nu correcte waarden voor `base_row_total` en `row_total` -kenmerken voor het geval dat meerdere, dezelfde items werden besteld.

* Oplossing voor AC-15446: Probleem verholpen waarbij `Magento\Framework\Mail\EmailMessage` probeerde een `getBodyText()` niet-bestaande `getTextBody()` methode aan te roepen op `Symfony\Component\Mime\Message` . Dit zorgt voor compatibiliteit met Magento 2.4.8-p2 en `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

### Bekende problemen

#### De uitcheckpagina kan static.min.js en mixins.min.js niet laden.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

De Adobe Commerce 2.4.8-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-71 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

De Adobe Commerce 2.4.8-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.8 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-50 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

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

De correcties voor CVE-2025-47110 en VULN-31547 zijn ook beschikbaar als een geïsoleerde patch. Zie het [&#x200B; artikel van de Kennisbank &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) voor details.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-02-20 15:30:03 -->

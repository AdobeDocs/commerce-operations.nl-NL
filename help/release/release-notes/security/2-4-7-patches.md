---
title: Opmerkingen bij de release Adobe Commerce 2.4.7 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: f731debd7e0734d1bb1b8c821149ffafea735337
workflow-type: tm+mt
source-wordcount: '1390'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0 bereikt het einde van de ondersteuning (EOS) vanaf 30 april 2026.
>
>Na deze datum biedt Adobe Commerce 2.4.7 geen compatibiliteit of>ondersteuning voor MySQL-versies die worden uitgebracht na MySQL 8.0. Adobe zal niet>valideer of verstrek ondersteuning voor nieuwere MySQL belangrijke versies op deze Adobe>Commerce releaselijn.
>
>Alle Adobe Commerce-klanten die versie 2.4.7 gebruiken zijn sterk>adviseerde om hun gegevensbestandservers aan een compatibele versie te migreren MariaDB.

## 2.4.7-p10

De beveiligingsrelease van Adobe Commerce 2.4.7-p10 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.7.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB26-49 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb26-49.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

#### Compatibiliteit met MariaDB 11.8

Adobe Commerce 2.4.7-p10 introduceert compatibiliteit met MariaDB versie 11.8. MariaDB 11.8 introduceert veranderingen in SQL gedrag, gebreken, veroudering, en prestatiesoptimalisering. Deze update verhelpt proactief potentiële problemen om de stabiliteit van het platform en de toekomstige gereedheid te behouden.

#### Ondersteuning voor OpenSearch 3 nieuwste secundaire versie

Adobe Commerce 2.4.7 biedt nu ondersteuning voor de nieuwste kleine versie van OpenSearch 3 op Adobe Commerce voor cloudinfrastructuur, Cloud Native en implementaties op locatie. Compatibiliteit met OpenSearch 2 blijft behouden.

#### Valkey 8.1 LTS-ondersteuning

Adobe Commerce 2.4.7 is nu compatibel met Valkey 8.1 LTS en biedt een back-end optie voor cache op lange termijn die door Adobe Commerce op cloudinfrastructuur wordt ondersteund.

#### Ondersteuning voor RabbitMQ 4.2

Adobe Commerce 2.4.7 is nu compatibel met RabbitMQ 4.2, die de voor februari 2026 geplande einddatum van de ondersteuning voor RabbitMQ 4.1 aanbiedt. De verenigbaarheid met Apache ActiveMQ Artemis wordt behouden, en ActiveMQ blijft de standaarddienst van de berichtrij voor deze veiligheid-slechts versielijn.

#### Ondersteuning voor REST API van USPS

De USPS-integratie voor verzending ondersteunt nu de gemoderniseerde RESTful USPS API&#39;s in aanvulling op de verouderde Web Tools API&#39;s. Beheerders kunnen in de beheerconfiguratie aangeven welke USPS-integratie-API u wilt gebruiken. Deze update bereidt de veroudering van de USPS Web Tools API voor.

#### Magento-eigenaar Laminas MVC-vork

Adobe Commerce gebruikt nu een vork in Magento van `laminas-mvc` (gepubliceerd als `magento/magento-zf-mvc` ) om de Laminas MVC-pensionering aan te pakken. Deze vork zorgt voor voortdurende patching en naleving van de langetermijnbeveiliging voor Adobe Commerce 2.4.7.

## 2.4.7-p9

De Adobe Commerce 2.4.7-p9 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB26-05 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

#### Ondersteuning voor MyDHL REST API voor integratie van DHL-scheepvaart

De integratie van DHL voor scheepvaart ondersteunt nu MyDHL REST API&#39;s naast de bestaande integratie van DHL Express XML. Deze update wordt uitgelijnd op de huidige API-stapel van DHL en bereidt de veroudering van de oudere XML API&#39;s voor.

#### Compatibiliteit toevoegen met de nieuwste Composer-versie

Adobe Commerce 2.4.7 is bijgewerkt ter ondersteuning van Composer 2.9.x en blijft compatibel met Composer 2.2 LTS.

## 2.4.7-p8

De beveiligingsrelease van Adobe Commerce 2.4.7-p8 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.7.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-94 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Deze release bevat de volgende hooglichten:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Bekende problemen

#### De uitcheckpagina kan static.min.js en mixins.min.js niet laden.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

De Adobe Commerce 2.4.7-p7 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-71 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

De beveiligingsrelease van Adobe Commerce 2.4.7-p6 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.7.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-50 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* **MariaDB steun** - Toegevoegde steun voor MariaDB 10.11.

* **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

* **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

* **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

* **verrichtingen Async** - Beperkte async verrichtingen voor het met voeten treden van vorige klantenorden.<!-- AC-13917 -->

## 2.4.7-p5

De Adobe Commerce 2.4.7-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.7.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-26 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Deze versie introduceert ook steun voor de Adobe Commerce [&#x200B; HIPAA-Klaar uitbreiding &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Bekende problemen

**Uitgave**: Wanneer u 2.4.7-p5 installeert met PHP 8.2 of hoger, installeert het systeem `paypal/module-braintree` versie 4.7.0, die bedoeld is voor versie 2.4.8 en hoger. Voor PHP 8.1 wordt de juiste Braintree versie 4.6.1-p5 gebruikt. Dit verschil komt door de losse afhankelijkheid van `adobe-commerce/extensions-metapackage: ~2.0` in het pakket metapakketten. Dit beïnvloedt de verenigbaarheid en de gesteunde eigenschap die voor PHP 8.2+ plaatsingen wordt geplaatst.<!-- ACPLTSRV-6276) -->

Daarnaast kan voor de versies 2.4.7-p3, 2.4.7-p4 en 2.4.7-p5 de Braintree-extensie versie 4.6.1-p5 worden geïnstalleerd, terwijl sommige gebruikers verwachten dat versie 4.6.1-p3 of p4 is, omdat eerdere, striktere afhankelijkheden zijn versoepeld om uitbreidingsupgrades binnen een releaselijn mogelijk te maken. <!-- AC-14430 -->

**Oplossing**: Voer `composer update` uit om de juiste Braintree-versie voor uw PHP-versie te installeren, afhankelijk van `adobe-commerce/extensions-metapackage:2.0.0` . Dit zorgt ervoor dat u de juiste-versie voor uw PHP-versie hebt.

## 2.4.7-p4

De Adobe Commerce 2.4.7-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-08 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

De Adobe Commerce 2.4.7-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-73 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

De Adobe Commerce 2.4.7-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-61 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

De Adobe Commerce 2.4.7-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-40 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* [&#x200B; eenmalig wachtwoord van de Update **(OTP) montages &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) voor de Authenticator van Google** - Deze update wordt vereist om een fout op te lossen die door a [&#x200B; achteruit-onverenigbaar verandering &#x200B;](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 werd geïntroduceerd. De beschrijving van het veld **[!UICONTROL OTP Window]** bevat nu een nauwkeurige uitleg van de instelling en de standaardwaarde is gewijzigd van `1` in `29` .

* **B2B versiecompatibiliteit** - voor verenigbaarheid met versie 2.4.7-p1 van Commerce, de verkopers die de uitbreiding hebben van Adobe Commerce B2B moeten aan [&#x200B; B2B versie 1.4.2-p1 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.7-p1 verhelpt een probleem dat is ontstaan in het bereik van de UPS-integratiemigratie van SOAP naar REST API. Dit probleem betrof klanten die buiten de VS verschepen en belette hen de Metric System/SI-metingen van kilo en centimeters voor pakketten te gebruiken om zendingen met UPS te maken. Zie [&#x200B; UPS die de migratie van de methodeintegratie van SOAP aan RESTful API &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) kennisbankartikel voor details verschepen.

<!-- Last updated from includes: 2026-04-08 15:01:38 -->

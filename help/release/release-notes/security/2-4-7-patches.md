---
title: Opmerkingen bij de release Adobe Commerce 2.4.7 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p7

De Adobe Commerce 2.4.7-p7 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-71 ](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

De beveiligingsrelease van Adobe Commerce 2.4.7-p6 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.7.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-50 ](https://helpx.adobe.com/nl/security/products/magento/apsb25-50.html).

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

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-26 ](https://helpx.adobe.com/nl/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Deze versie introduceert ook steun voor de Adobe Commerce [ HIPAA-Klaar uitbreiding ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Bekende problemen

**Uitgave**: Wanneer het installeren van 2.4.7-p5 met PHP 8.2 of hoger, installeert het systeem `paypal/module-braintree` versie 4.7.0, die voor 2.4.8 en nieuwer voorgenomen is. Voor PHP 8.1 wordt de juiste Braintree versie 4.6.1-p5 gebruikt. Dit verschil komt door de losse afhankelijkheid van `adobe-commerce/extensions-metapackage: ~2.0` in het pakket metapakketten. Dit beïnvloedt de verenigbaarheid en de gesteunde eigenschap die voor PHP 8.2+ plaatsingen wordt geplaatst.<!-- ACPLTSRV-6276) -->

Daarnaast kan voor de versies 2.4.7-p3, 2.4.7-p4 en 2.4.7-p5 de Braintree-extensie versie 4.6.1-p5 worden geïnstalleerd, terwijl sommige gebruikers verwachten dat versie 4.6.1-p3 of p4 is, omdat eerdere, striktere afhankelijkheden zijn versoepeld om uitbreidingsupgrades binnen een releaselijn mogelijk te maken. <!-- AC-14430 -->

**Oplossing**: Om ervoor te zorgen dat u de correcte versie van Braintree voor uw PHP versie hebt, looppas `composer update` om de aangewezen versie te installeren zoals die door `adobe-commerce/extensions-metapackage:2.0.0` gebiedsdeel wordt gedicteerd.

## 2.4.7-p4

De Adobe Commerce 2.4.7-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-08 ](https://helpx.adobe.com/nl/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

De Adobe Commerce 2.4.7-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-73 ](https://helpx.adobe.com/nl/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

De Adobe Commerce 2.4.7-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-61 ](https://helpx.adobe.com/nl/security/products/magento/apsb24-61.html).

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

De Adobe Commerce 2.4.7-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-40 ](https://helpx.adobe.com/nl/security/products/magento/apsb24-40.html).

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* **eenmalig wachtwoord van de Update [ (OTP) montages ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) voor de Authenticator van Google** - Deze update wordt vereist om een fout op te lossen die door a [ achteruit-onverenigbaar verandering ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 werd geïntroduceerd. De beschrijving van het veld **[!UICONTROL OTP Window]** bevat nu een nauwkeurige uitleg van de instelling en de standaardwaarde is gewijzigd van `1` in `29` .

* **B2B versiecompatibiliteit** - voor verenigbaarheid met versie 2.4.7-p1 van Commerce, de verkopers die de uitbreiding hebben van Adobe Commerce B2B moeten aan [ B2B versie 1.4.2-p1 ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.7-p1 verhelpt een probleem dat is ontstaan in het bereik van de UPS-integratiemigratie van SOAP naar REST API. Dit probleem betrof klanten die buiten de VS verschepen en belette hen de Metric System/SI-metingen van kilo en centimeters voor pakketten te gebruiken om zendingen met UPS te maken. Zie [ UPS die de migratie van de methodeintegratie van SOAP aan RESTful API ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) kennisbankartikel voor details verschepen.

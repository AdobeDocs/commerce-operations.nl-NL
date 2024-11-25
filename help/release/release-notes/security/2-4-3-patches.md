---
title: Opmerkingen bij de release van Adobe Commerce 2.4.3 Beveiligingspatches
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.3

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

Het beveiligingsrelease van Adobe Commerce 2.4.3-p3 biedt beveiligingsoplossingen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.3. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB22-38 ](https://helpx.adobe.com/security/products/magento/apsb22-38.html).[

### Toepassen op `AC-3022.patch` om DHL als scheepvaartmaatschappij te blijven aanbieden

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Handelaren die deze releases implementeren, moeten `AC-3022.patch` zo snel mogelijk toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden. Zie [ een flard toepassen om DHL als het verschepen drager ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) artikel van de Kennisbank voor informatie over het downloaden en het installeren van het flard te blijven aanbieden.

### Beveiligingsmarkeringen

* ACL de middelen zijn toegevoegd aan de Inventaris.
* De beveiliging van het voorraadsjabloon is verbeterd.

## Adobe Commerce 2.4.3-p2

De Adobe Commerce 2.4.3-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB22-13 ](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  [  De patchrelease verhelpt ook de kwetsbaarheid die `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` en `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch` verhelpen.


### Toepassen op `AC-3022.patch` om DHL als scheepvaartmaatschappij te blijven aanbieden

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Handelaren die deze releases implementeren, moeten `AC-3022.patch` zo snel mogelijk toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden. Zie [ een flard toepassen om DHL als het verschepen drager ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) artikel van de Kennisbank voor informatie over het downloaden en het installeren van het flard te blijven aanbieden.

### Beveiligingsmarkeringen

* Het gebruik van e-mailvariabelen is in 2.3.4 afgekeurd als onderdeel van een beperking van het beveiligingsrisico ten gunste van een striktere variabele syntaxis. Dit verouderde gedrag is volledig verwijderd in deze versie als voortzetting van die beperking van het veiligheidsrisico.

  Sjablonen voor e-mail- of nieuwsbrieven die in eerdere versies hebben gewerkt, werken dus mogelijk niet correct na de upgrade naar Adobe Commerce 2.4.3-p2. Betrokken sjablonen zijn onder andere overschrijvingen van beheer, thema&#39;s, onderliggende thema&#39;s en sjablonen van aangepaste modules of uitbreidingen van derden. Uw plaatsing kan nog worden beïnvloed zelfs na het gebruiken van het [ verenigbaarheidshulpmiddel van de Verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) om verouderde gebruik te bevestigen. Zie [ het Migreren van douane e-mailmalplaatjes ](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) voor informatie over potentiële gevolgen en richtlijnen voor het migreren van beïnvloede malplaatjes.

* De tokens van de de toegangstoegang en van het wachtwoord terugstellen worden nu gecodeerd wanneer opgeslagen in het gegevensbestand. <!-- AC-520 1323-->

* Validatie is versterkt om het uploaden van niet-alfanumerieke bestandsextensies te voorkomen. <!-- AC-479-->

* De wagen is nu standaard uitgeschakeld wanneer Adobe Commerce in de productiemodus staat. <!-- AC-1450-->

* De ontwikkelaars kunnen de groottegrens voor series nu vormen die door Adobe Commerce RESTful eindpunten op een per-eindpuntbasis worden goedgekeurd. Zie [ API veiligheid ](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Toegevoegde mechanismen voor het beperken van de grootte en het aantal bronnen dat een gebruiker via een web-API op systeembrede basis kan aanvragen, en voor het overschrijven van de standaardinstellingen voor afzonderlijke modules. Deze verbetering verhelpt het probleem dat wordt opgelost door `MC-43048__set_rate_limits__2.4.3.patch` . Zie [ API veiligheid ](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

De Adobe Commerce 2.4.3-p1-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in de vorige release (Adobe Commerce 2.4.3 en Magento Open Source 2.4.3). Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.


Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB21-86 ](https://helpx.adobe.com/security/products/magento/apsb21-86.html). [ De flardversie verstrekt ook insectenmoeilijke situaties voor de [ Braintree ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [ Klarna ](https://marketplace.magento.com/klarna-m2-klarna.html), en [ Vertex ](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) leverancier-ontwikkelde uitbreidingen.

### Toepassen op `AC-3022.patch` om DHL als scheepvaartmaatschappij te blijven aanbieden

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Handelaren die deze releases implementeren, moeten `AC-3022.patch` zo snel mogelijk toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden. Zie [ een flard toepassen om DHL als het verschepen drager ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) artikel van de Kennisbank voor informatie over het downloaden en het installeren van het flard te blijven aanbieden.

### Hotfixes

Deze release bevat de volgende hotfix en alle hotfixes die zijn vrijgegeven voor de vorige patchrelease.

* Reparatie `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Zie de [ verbetering 2.4.3 van Adobe Commerce, 2.3.7-p1 PHP Snelle fout Hotfix ](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) het artikel van de Kennisbank voor informatie over zowel flard als kwestie.

### Beveiligingsmarkeringen

**Identiteitskaart van de Zitting is verwijderd uit het gegevensbestand**. Deze codeverandering kan in het breken van veranderingen resulteren als de verkopers aanpassingen of geïnstalleerde uitbreidingen hebben die onbewerkte zitting IDs gebruiken die in het gegevensbestand worden opgeslagen. <!-- MC-40976-->

**Beperkte admin toegang tot de omslagen van de Galerij van Media**. De standaardbevoegdheden van de Medialerie staan nu alleen directorybewerkingen toe (weergeven, uploaden, verwijderen en maken) die expliciet zijn toegestaan door de configuratie. Admin-gebruikers hebben geen toegang meer tot media-elementen via de medialerie die buiten de mappen `catalog/category` of `wysiwyg` zijn geüpload. Beheerders die toegang willen krijgen tot media-elementen, moeten deze naar een expliciet toegestane map verplaatsen of hun configuratie-instellingen aanpassen. Zie [ de omslagtoestemmingen van Media Library wijzigen ](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Verlaagde grenzen aan de vraagingewikkeldheid van GraphQL**. De GraphQL maximum toegestane vraagingewikkeldheid is verminderd om ontkenning-van-Dienst (DOS) aanvallen te verhinderen. Zie [ de veiligheidsconfiguratie van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**de Recente kwetsbaarheid van de penetratietest** is bevestigd in deze versie. <!-- MC-42431-->

De niet-ondersteunde bronexpressie `unsafe-inline` is verwijderd uit de aanwijzing Content Security Policy `frame-ancestors` . [ GitHub-33101 ](https://github.com/magento/magento2/issues/33101) <!-- MC-42632-->

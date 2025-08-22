---
title: Opmerkingen bij de release Adobe Commerce 2.4.6 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p12

De veiligheidsversie van Adobe Commerce 2.4.6-p12 verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.6 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-71 ](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.6-p11

De veiligheidsversie van Adobe Commerce 2.4.6-p11 verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.6 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-50 ](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* **MariaDB steun** - Toegevoegde steun voor MariaDB 10.11.

* **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

* **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

* **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

* **verrichtingen Async** - Beperkte async verrichtingen voor het met voeten treden van vorige klantenorden.<!-- AC-13917 -->

## 2.4.6-p10

De Adobe Commerce 2.4.6-p10-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-26 ](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

De Adobe Commerce 2.4.6-p9 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.6 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB25-08 ](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

De beveiligingsrelease van Adobe Commerce 2.4.6-p8 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-73 ](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

De Adobe Commerce 2.4.6-p7 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.6 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-61 ](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

De beveiligingsrelease van Adobe Commerce 2.4.6-p6 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-40 ](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

Voor verenigbaarheid met versie 2.4.6-p6 van Commerce, moeten de handelaren die de uitbreiding hebben van Adobe Commerce B2B aan [ B2B versie 1.4.2-p1 ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Voor verenigbaarheid met versie 2.4.6-p6 van Commerce, moeten de handelaren die de uitbreiding hebben van Adobe Commerce B2B aan [ B2B versie 1.4.2-p1 ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Hooglichten

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

De Adobe Commerce 2.4.6-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over deze moeilijke situaties, zie [ Bulletin van de Veiligheid APSB24-18 van Adobe ](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.6-p4

De Adobe Commerce 2.4.6-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB24-03 ](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Hooglichten

Deze release introduceert twee belangrijke beveiligingsverbeteringen:

* **Veranderingen in het gedrag van niet-geproduceerde geheim voorgeheugensleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van sjablooninstructies of de methoden `setCacheKey` of `setData` .)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten. <!-- AC-9831 -->

* **Beperkingen op het aantal auto-geproduceerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaars kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) gebruiken om deze nieuwe grens te bepalen. <!-- AC-8753 -->

## 2.4.6-p3

De Adobe Commerce 2.4.6-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsmoeilijke situaties, zie [ Bulletin van de Veiligheid APSB23-50 van Adobe ](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Hooglichten

Deze versie introduceert een nieuwe instelling voor de configuratie van het volledige paginacachegeheugen die helpt de risico&#39;s te beperken die aan het `{BASE-URL}/page_cache/block/esi HTTP` -eindpunt zijn gekoppeld. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de lay-outhandvatten van Commerce en blokstructuren. Met de nieuwe configuratie-instelling **[!UICONTROL Handles Param]** wordt de waarde van de parameter `handles` van dit eindpunt ingesteld, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaars kunnen deze waarde wijzigen via Beheer (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]** ). <!-- AC-9113 -->

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p3 bevat de resolutie van de prestatievermindering die is vastgelegd door patch ACSD-51892. De handelaren worden niet beïnvloed door de kwestie die door dit flard wordt gericht, die in [ ACSD-51892 wordt beschreven: De kwestie van prestaties waar de configuratiedossiers veelvoudige tijden ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) het artikel van de Kennisbank laden.

### Bekende problemen

**Uitgave**: Adobe Commerce toont een `wrong checksum` fout tijdens download door Composer van `repo.magento.com`, en de pakketdownload wordt onderbroken. Dit probleem kan optreden tijdens het downloaden van releasepakketten die tijdens de prereleaseperiode beschikbaar zijn gesteld en wordt veroorzaakt door het opnieuw verpakken van het `magento/module-page-cache` -pakket.

**Oplossing**: De handelaren die deze fout tijdens download zien kunnen deze stappen nemen:

1) Verwijder de map `/vendor` in het project, als die bestaat.
2) Voer de opdracht `bin/magento composer update magento/module-page-cache` uit. Met deze opdracht wordt alleen het `page cache` -pakket bijgewerkt.

Als het probleem met de controlesom aanhoudt, verwijdert u het bestand `composer.lock` voordat u de opdracht `bin/magento composer update` opnieuw uitvoert om elk pakket bij te werken.

## 2.4.6-p2

De Adobe Commerce 2.4.6-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release biedt ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB23-42 ](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix toepassen voor CVE-2022-31160

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die op meerdere versies van Adobe Commerce en Magento Open Source van toepassing is. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [ wordt gespecificeerd jQuery UI veiligheidskwetsbaarheid CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) het artikel van de Kennisbank.

### Hooglichten

De waarde van `fastcgi_pass` in het `nginx.sample` -bestand is geretourneerd naar de vorige (pre-2.4.6-p1) waarde van `fastcgi_backend` . Deze waarde is per ongeluk gewijzigd in `php-fpm:9000` in Adobe Commerce 2.4.6-p1.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p2 bevat een resolutie van de verslechtering van de prestaties die werd aangepakt door patch ACSD-51892. De handelaren worden niet beïnvloed door de kwestie die door dit flard wordt gericht, die in [ ACSD-51892 wordt beschreven: De kwestie van prestaties waar de configuratiedossiers veelvoudige tijden ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) het artikel van de Kennisbank laden.

## 2.4.6-p1

De Adobe Commerce 2.4.6-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsupdates en platformupgrades om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [ Bulletin van de Veiligheid van Adobe APSB23-35 ](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix toepassen voor CVE-2022-31160

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die op meerdere versies van Adobe Commerce en Magento Open Source van toepassing is. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [ de veiligheidskwetsbaarheid van de Vraag UI CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) het artikel van de Kennisbank wordt gespecificeerd.

#### Markeren

Het standaardgedrag van de [`isEmailAvailable` ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) vraag van GraphQL en ([`V1/customers/isEmailAvailable` ](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST eindpunt is veranderd. De API retourneert nu standaard altijd `true` . Merchants kunnen het oorspronkelijke gedrag inschakelen, dat wil zeggen dat `true` wordt geretourneerd als het e-mailbericht niet in de database bestaat en `false` als het wel bestaat. <!-- AC-6695 -->

### Platformupgrades

Platformupgrades voor deze release verbeteren de naleving van de nieuwste best practices op het gebied van beveiliging.

* **Varnish geheime voorgeheugen 7.3 steun**. Deze release is compatibel met de nieuwste versie van Varnish Cache 7.3. De compatibiliteit met de 6.0.x- en 7.2.x-versies blijft behouden, maar Adobe raadt aan Adobe Commerce 2.4.6-p1 alleen te gebruiken met Varnish Cache versie 7.3 of versie 6.0 LTS.

* **RabbitMQ 3.11 steun**. Deze release is compatibel met de nieuwste versie van RabbitMQ 3.11. Compatibiliteit blijft behouden met RabbitMQ 3.9, dat tot augustus 2023 wordt ondersteund, maar Adobe raadt aan Adobe Commerce 2.4.6-p1 alleen te gebruiken met RabbitMQ 3.11.

* **bibliotheken van JavaScript**. Verouderde JavaScript-bibliotheken zijn bijgewerkt naar de nieuwste secundaire versies of patchversies, waaronder `moment.js` library (v2.29.4), `jQuery UI` library (v1.13.2) en `jQuery` validatie-insteekbibliotheek (v1.19.5).

### Bekende problemen

* Het bestand `nginx.sample` is per ongeluk bijgewerkt met een wijziging die de waarde van `fastcgi_pass` from `fastcgi_backend` in `php-fpm:9000` wijzigt. Deze wijziging kan veilig worden hersteld of genegeerd. <!-- AC-8992 -->

* Ontbrekende afhankelijkheden voor het B2B-beveiligingspakket veroorzaken de volgende installatiefout bij de installatie of upgrade van de B2B-extensie naar 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Dit probleem kan worden opgelost door handgebiedsdelen voor het B2B veiligheidspakket met a [ stabiliteitsmarkering ](https://getcomposer.org/doc/04-schema.md#package-links) toe te voegen. Voor details, zie de [ B2B versienota&#39;s ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).

<!-- Last updated from includes: 2025-07-24 10:48:00 -->

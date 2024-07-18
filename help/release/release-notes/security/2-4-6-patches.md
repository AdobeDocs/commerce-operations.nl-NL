---
title: Opmerkingen bij de release Adobe Commerce 2.4.6 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

De beveiligingsrelease van Adobe Commerce 2.4.6-p6 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB24-40 ](https://helpx.adobe.com/security/products/magento/apsb24-40.html).[

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Beveiligingsmarkering

Voor verenigbaarheid met versie 2.4.6-p6 van Commerce, moeten de handelaren die de uitbreiding hebben van Adobe Commerce B2B aan [ B2B versie 1.4.2-p1 ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Aanvullende beveiligingsverbeteringen

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

De Adobe Commerce 2.4.6-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.6.

Voor de recentste informatie over deze moeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB24-18 ](https://helpx.adobe.com/security/products/magento/apsb24-18.html).[

## Adobe Commerce 2.4.6-p4

De Adobe Commerce 2.4.6-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB24-03 ](https://helpx.adobe.com/security/products/magento/apsb24-03.html).[

### Beveiligingsmarkeringen

Deze release introduceert twee belangrijke beveiligingsverbeteringen:

* **Veranderingen in het gedrag van niet-geproduceerde geheim voorgeheugensleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van sjablooninstructies of de methoden `setCacheKey` of `setData` .)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten. <!-- AC-9831 -->

* **Beperkingen op het aantal auto-geproduceerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaars kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) gebruiken om deze nieuwe grens te bepalen. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

De Adobe Commerce 2.4.6-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB23-50 ](https://helpx.adobe.com/security/products/magento/apsb23-50.html).[

### Beveiligingsmarkeringen

Deze versie introduceert een nieuwe instelling voor de configuratie van het volledige paginacachegeheugen die helpt de risico&#39;s te beperken die aan het `{BASE-URL}/page_cache/block/esi HTTP` -eindpunt zijn gekoppeld. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de lay-outhandvatten van Commerce en blokstructuren. Met de nieuwe configuratie-instelling **[!UICONTROL Handles Param]** wordt de waarde van de parameter `handles` van dit eindpunt ingesteld, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaars kunnen deze waarde wijzigen via Beheer (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]** ). <!-- AC-9113 -->

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p3 bevat de resolutie van de prestatievermindering die is vastgelegd door patch ACSD-51892. De handelaren worden niet beïnvloed door de kwestie die door dit flard wordt gericht, die in [ ACSD-51892 wordt beschreven: De kwestie van prestaties waar de configuratiedossiers veelvoudige tijden ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) het artikel van de Kennisbank laden.

### Bekend probleem

**Uitgave**: Adobe Commerce toont een `wrong checksum` fout tijdens download door Composer van `repo.magento.com`, en de pakketdownload wordt onderbroken. Dit probleem kan optreden tijdens het downloaden van releasepakketten die tijdens de prereleaseperiode beschikbaar zijn gesteld en wordt veroorzaakt door het opnieuw verpakken van het `magento/module-page-cache` -pakket.

**Oplossing**: De handelaren die deze fout tijdens download zien kunnen deze stappen nemen:

1) Verwijder de map `/vendor` in het project, als die bestaat.
2) Voer de opdracht `bin/magento composer update magento/module-page-cache` uit. Met deze opdracht wordt alleen het `page cache` -pakket bijgewerkt.

Als het probleem met de controlesom aanhoudt, verwijdert u het bestand `composer.lock` voordat u de opdracht `bin/magento composer update` opnieuw uitvoert om elk pakket bij te werken.

## 2.4.6-p2

De Adobe Commerce 2.4.6-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release biedt ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB23-42 ](https://helpx.adobe.com/security/products/magento/apsb23-42.html).[

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die van invloed is op meerdere versies van Adobe Commerce en Magento Open Source. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [ wordt gespecificeerd jQuery UI veiligheidskwetsbaarheid CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) het artikel van de Kennisbank.

### Beveiligingsmarkering

De waarde van `fastcgi_pass` in het `nginx.sample` -bestand is geretourneerd naar de vorige (pre-2.4.6-p1) waarde van `fastcgi_backend` . Deze waarde is per ongeluk gewijzigd in `php-fpm:9000` in Adobe Commerce 2.4.6-p1.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p2 bevat een resolutie van de verslechtering van de prestaties die werd aangepakt door patch ACSD-51892. De handelaren worden niet beïnvloed door de kwestie die door dit flard wordt gericht, die in [ ACSD-51892 wordt beschreven: De kwestie van prestaties waar de configuratiedossiers veelvoudige tijden ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) het artikel van de Kennisbank laden.

## Adobe Commerce 2.4.6-p1

De Adobe Commerce 2.4.6-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsupdates en platformupgrades om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB23-35 ](https://helpx.adobe.com/security/products/magento/apsb23-35.html).[

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die van invloed is op meerdere versies van Adobe Commerce en Magento Open Source. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [ de veiligheidskwetsbaarheid van de Vraag UI CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) het artikel van de Kennisbank wordt gespecificeerd.

#### Beveiligingsmarkering

Het standaardgedrag van de [`isEmailAvailable` ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) vraag van GraphQL en ([`V1/customers/isEmailAvailable` ](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST eindpunt is veranderd. De API retourneert nu standaard altijd `true` . Merchants kunnen het oorspronkelijke gedrag inschakelen, dat wil zeggen dat `true` wordt geretourneerd als het e-mailbericht niet in de database bestaat en `false` als het wel bestaat. <!-- AC-6695 -->

### Platformupgrades

Platformupgrades voor deze release verbeteren de naleving van de nieuwste best practices op het gebied van beveiliging.

* **Varnish geheime voorgeheugen 7.3 steun**. Deze release is compatibel met de nieuwste versie van Varnish Cache 7.3. Compatibiliteit blijft behouden met de 6.0.x- en 7.2.x-versies, maar Adobe wordt aanbevolen Adobe Commerce 2.4.6-p1 alleen te gebruiken met Varnish Cache versie 7.3 of versie 6.0 LTS.

* **RabbitMQ 3.11 steun**. Deze release is compatibel met de nieuwste versie van RabbitMQ 3.11. Compatibiliteit blijft behouden met RabbitMQ 3.9, dat tot augustus 2023 wordt ondersteund, maar Adobe wordt alleen aanbevolen om Adobe Commerce 2.4.6-p1 te gebruiken met RabbitMQ 3.11.

* **bibliotheken van JavaScript**. Verouderde JavaScript-bibliotheken zijn bijgewerkt naar de nieuwste secundaire versies of patchversies, waaronder `moment.js` library (v2.29.4), `jQuery UI` library (v1.13.2) en `jQuery` validatie-insteekbibliotheek (v1.19.5).

### Bekende problemen

* Het bestand `nginx.sample` is per ongeluk bijgewerkt met een wijziging die de waarde van `fastcgi_pass` from `fastcgi_backend` in `php-fpm:9000` wijzigt. Deze wijziging kan veilig worden hersteld of genegeerd. <!-- AC-8992 -->

* Ontbrekende afhankelijkheden voor het B2B-beveiligingspakket veroorzaken de volgende installatiefout bij de installatie of upgrade van de B2B-extensie naar 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Dit probleem kan worden opgelost door handgebiedsdelen voor het B2B veiligheidspakket met a [ stabiliteitsmarkering ](https://getcomposer.org/doc/04-schema.md#package-links) toe te voegen. Voor details, zie de [ B2B versienota&#39;s ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).

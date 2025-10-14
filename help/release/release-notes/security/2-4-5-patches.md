---
title: Opmerkingen bij de release Adobe Commerce 2.4.5 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: c73eafcf52cf2ba0ea539bf61191db5fff952d7a
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.5

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p15

De beveiligingsrelease van Adobe Commerce 2.4.5-p15 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-94 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>Uitgebreide beveiligingspatches voor 2.4.5 zijn alleen beschikbaar voor Adobe Commerce-klanten. Deze patches zijn niet beschikbaar voor de Magento Open Source-codebasis. Zie [&#x200B; Uitgebreide Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).


## 2.4.5-p14

De beveiligingsrelease van Adobe Commerce 2.4.5-p14 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-71 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.5-p13

De veiligheidsversie van Adobe Commerce 2.4.5-p13 verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.5 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-50 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

* **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

* **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

* **verrichtingen Async** - Beperkte async verrichtingen voor het met voeten treden van vorige klantenorden.<!-- AC-13917 -->

## 2.4.5-p12

De beveiligingsrelease van Adobe Commerce 2.4.5-p12 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-26 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-p11

De Adobe Commerce 2.4.5-p11-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-08 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

De Adobe Commerce 2.4.5-p10-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-73 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5-p9

De Adobe Commerce 2.4.5-p9 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.5 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-61 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb24-61.html).

### Hooglichten

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

De beveiligingsrelease van Adobe Commerce 2.4.5 en p8 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-40 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb24-40.html).

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Platformupgrades

* **MariaDB 10.5 steun**. Deze patchrelease introduceert compatibiliteit met MariaDB versie 10.5. Adobe Commerce is nog steeds compatibel met MariaDB-versie 10.4, maar Adobe raadt aan Adobe Commerce 2.4.5-p8 te gebruiken en alle aanstaande patchreleases (alleen voor de beveiliging van 2.4.5) alleen met MariaDB-versie 10.5, omdat het onderhoud van MariaDB 10.4 eindigt op 18 juni 2024. <!--AC-11530-->

### Hooglichten

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

De Adobe Commerce 2.4.5-p7 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.5 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-18 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb24-18.html).

## 2.4.5-p6

De beveiligingsrelease van Adobe Commerce 2.4.5-p6 biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB24-03 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb24-03.html).

### Hooglichten

Deze release introduceert twee belangrijke beveiligingsverbeteringen:

* **Veranderingen in het gedrag van niet-geproduceerde geheim voorgeheugensleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van sjablooninstructies of de methoden `setCacheKey` of `setData` .)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten. <!-- AC-9831 -->

* **Beperkingen op het aantal auto-geproduceerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaars kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) gebruiken om deze nieuwe grens te bepalen. <!-- AC-8753 -->

## 2.4.5-p5

De Adobe Commerce 2.4.5-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB23-50 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb23-50.html).

### Hooglichten

Deze versie introduceert een nieuwe instelling voor de configuratie van het volledige paginacachegeheugen die helpt de risico&#39;s te beperken die aan het `{BASE-URL}/page_cache/block/esi HTTP` -eindpunt zijn gekoppeld. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de lay-outhandvatten van Commerce en blokstructuren. Met de nieuwe configuratie-instelling **[!UICONTROL Handles Param]** wordt de waarde van de parameter `handles` van dit eindpunt ingesteld, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaars kunnen deze waarde wijzigen via Beheer (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]** ). <!-- AC-9113 -->

### Bekende problemen

**Uitgave**: Adobe Commerce toont a **verkeerde controlesom** fout tijdens download door Composer van `repo.magento.com`, en de pakketdownload wordt onderbroken. Dit probleem kan optreden tijdens het downloaden van releasepakketten die tijdens de evaluatieversie beschikbaar zijn gemaakt en die worden veroorzaakt door een herverpakking van het `magento/module-page-cache` -pakket.

**Oplossing**: De handelaren die deze fout tijdens download zien kunnen deze stappen nemen:

1) Verwijder de map `/vendor` in het project, als die bestaat.
2) Voer de opdracht `bin/magento composer update magento/module-page-cache` uit. Met deze opdracht wordt alleen het `page cache` -pakket bijgewerkt.

Als het probleem met de controlesom aanhoudt, verwijdert u het bestand `composer.lock` voordat u de opdracht `bin/magento composer update` opnieuw uitvoert om elk pakket bij te werken.

## 2.4.5-p4

De Adobe Commerce 2.4.5-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.5 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB23-42 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb23-42.html).

### Hotfix toepassen voor CVE-2022-31160

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die op meerdere versies van Adobe Commerce en Magento Open Source van toepassing is. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [&#x200B; wordt gespecificeerd jQuery UI veiligheidskwetsbaarheid CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) het artikel van de Kennisbank.

## 2.4.5-p3

Het beveiligingsrelease van Adobe Commerce 2.4.5-p3 biedt beveiligingsoplossingen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb23-35.html).

### Hotfix toepassen voor CVE-2022-31160

`jQuery-UI` versie 1.13.1 van de bibliotheek heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die op meerdere versies van Adobe Commerce en Magento Open Source van toepassing is. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die beïnvloede plaatsingen in werking stellen zouden de flard moeten toepassen die in de [&#x200B; de veiligheidskwetsbaarheid van de Vraag UI CVE-2022-31160 moeilijke situatie voor 2.4.4, 2.4.5, en 2.4.6 versies &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) het artikel van de Kennisbank wordt gespecificeerd.

### Hooglichten

Het standaardgedrag van de [`isEmailAvailable` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) vraag van GraphQL en ([`V1/customers/isEmailAvailable` &#x200B;](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST eindpunt is veranderd. De API retourneert nu standaard altijd `true` . Merchants kunnen het oorspronkelijke gedrag inschakelen, dat wil zeggen dat `true` wordt geretourneerd als het e-mailbericht niet in de database bestaat en `false` als het wel bestaat. <!-- AC-6695 -->

### Platformupgrades

Platformupgrades voor deze release verbeteren de naleving van de nieuwste best practices op het gebied van beveiliging.

* **Varnish geheime voorgeheugen 7.3 steun**. Deze release is compatibel met de nieuwste versie van Varnish Cache 7.3. De compatibiliteit blijft behouden met de 6.0.x- en 7.2.x-versies, maar we raden u aan Adobe Commerce 2.4.5-p3 alleen te gebruiken met Varnish Cache versie 7.3 of versie 6.0 LTS.

* **RabbitMQ 3.11 steun**. Deze release is compatibel met de nieuwste versie van RabbitMQ 3.11. Compatibiliteit blijft behouden met RabbitMQ 3.9, dat tot augustus 2023 wordt ondersteund, maar we raden aan Adobe Commerce 2.4.5-p3 alleen te gebruiken met RabbitMQ 3.11.

* **bibliotheken van JavaScript**. Verouderde JavaScript-bibliotheken zijn bijgewerkt naar de nieuwste secundaire versies of patchversies, waaronder `moment.js` library (v2.29.4), `jQuery UI` library (v1.13.2) en `jQuery` validatie-insteekbibliotheek (v1.19.5).

## 2.4.5-p2

Het beveiligingsrelease van Adobe Commerce 2.4.5-p2 biedt drie beveiligingsoplossingen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.5.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB23-17 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb23-17.html).

## 2.4.5-p1

De Adobe Commerce 2.4.5-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.5 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB22-48 &#x200B;](https://helpx.adobe.com/nl/security/products/magento/apsb22-48.html).

Één van de veiligheidsinsectenmoeilijke situaties omvatte de verwezenlijking van een nieuwe configuratie het plaatsen. [!UICONTROL **vereist e-mailbevestiging als e-mail**] configuratie het plaatsen is veranderd laat beheerders e-mailbevestiging vereisen wanneer een gebruiker Admin hun e-mailadres verandert. <!-- AC-6292-->

<!-- Last updated from includes: 2025-10-06 13:12:34 -->

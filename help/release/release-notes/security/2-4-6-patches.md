---
title: Opmerkingen bij de release Adobe Commerce 2.4.6 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# Opmerkingen bij de release van Adobe Commerce 2.4.6 Beveiligingspatches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p5

De Adobe Commerce 2.4.6-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die in eerdere releases zijn geïdentificeerd.

Voor de meest recente informatie over deze oplossingen raadpleegt u [Beveiligingsbulletin APSB24-18 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

De Adobe Commerce 2.4.6-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-03 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Beveiligingsmarkeringen

Deze release introduceert twee belangrijke beveiligingsverbeteringen:

* **Wijzigingen in het gedrag van niet-gegenereerde cachesleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van de sjablooninstructie of de `setCacheKey` of `setData` methoden.)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten.  <!-- AC-9831 -->

* **Beperkingen op het aantal automatisch gegenereerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaren kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) om deze nieuwe limiet in te stellen. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

De Adobe Commerce 2.4.6-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsmoeilijke situaties, zie [Beveiligingsbulletin APSB23-50 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Beveiligingsmarkeringen

Deze versie introduceert een nieuwe instelling voor de volledige paginacacheconfiguratie die helpt de risico&#39;s te beperken die aan de `{BASE-URL}/page_cache/block/esi HTTP` eindpunt. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de de lay-outhandvatten van de Handel en blokstructuren. De nieuwe **[!UICONTROL Handles Param]** configuratie het plaatsen plaatst de waarde van dit eindpunt `handles` parameter, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaren kunnen deze waarde wijzigen via de beheerfunctie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p3 bevat de resolutie van de prestatievermindering die is vastgelegd door patch ACSD-51892. Merchants worden niet beïnvloed door het probleem dat wordt opgelost door deze patch, die wordt beschreven in het dialoogvenster [ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Kennisbank, artikel.

### Bekend probleem

**Probleem**: Adobe Commerce geeft een `wrong checksum` fout tijdens downloaden door Composer van `repo.magento.com`en wordt het downloaden van het pakket onderbroken. Dit probleem kan optreden tijdens het downloaden van releasepakketten die tijdens de prereleaseperiode beschikbaar zijn gesteld en wordt veroorzaakt door het opnieuw verpakken van de `magento/module-page-cache` pakket.

**Workaround**: Merchants die deze fout tijdens het downloaden zien, kunnen de volgende stappen uitvoeren:

1) Verwijder de `/vendor` directory binnen het project, als er een bestaat.
2) Voer de `bin/magento composer update magento/module-page-cache` gebruiken. Met deze opdracht werkt u alleen de `page cache` pakket.

Als het probleem met de controlesom zich blijft voordoen, verwijdert u het gereedschap `composer.lock` bestand voordat het opnieuw wordt uitgevoerd `bin/magento composer update` gebruiken om elk pakket bij te werken.

## 2.4.6-p2

De Adobe Commerce 2.4.6-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release biedt ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-42 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` Bibliotheekversie 1.13.1 heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die meerdere versies van Adobe Commerce en Magento Open Source beïnvloedt. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die betrokken implementaties uitvoeren, moeten de patch toepassen die in de [jQuery UI-beveiligingskwetsbaarheid CVE-2022-31160-oplossing voor 2.4.4-, 2.4.5- en 2.4.6-releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kennisbank, artikel.

### Beveiligingsmarkering

De waarde van `fastcgi_pass` in de `nginx.sample` bestand is geretourneerd naar de vorige (pre-2.4.6-p1) waarde van `fastcgi_backend`. Deze waarde is per ongeluk gewijzigd in `php-fpm:9000` in Adobe Commerce 2.4.6-p1.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.6-p2 bevat een resolutie van de verslechtering van de prestaties die werd aangepakt door patch ACSD-51892. Merchants worden niet beïnvloed door het probleem dat wordt opgelost door deze patch, die wordt beschreven in het dialoogvenster [ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Kennisbank, artikel.

## Adobe Commerce 2.4.6-p1

De Adobe Commerce 2.4.6-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsupdates en platformupgrades om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-35 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` Bibliotheekversie 1.13.1 heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die meerdere versies van Adobe Commerce en Magento Open Source beïnvloedt. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die betrokken implementaties uitvoeren, moeten de patch toepassen die in de [Security vulnerability CVE-2022-31160 fix van query-interface voor 2.4.4-, 2.4.5- en 2.4.6-releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kennisbank, artikel.

#### Beveiligingsmarkering

Het standaardgedrag van de [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-query en ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Het REST-eindpunt is gewijzigd. De API retourneert nu standaard altijd `true`. Handelaren kunnen het oorspronkelijke gedrag inschakelen, dat wil zeggen terugsturen `true` als de e-mail niet bestaat in de database en `false` als het bestaat. <!-- AC-6695 -->

### Platformupgrades

Platformupgrades voor deze release verbeteren de naleving van de nieuwste best practices op het gebied van beveiliging.

* **Varnish cache 7.3-ondersteuning**. Deze release is compatibel met de nieuwste versie van Varnish Cache 7.3. Compatibiliteit blijft behouden met de 6.0.x- en 7.2.x-versies, maar Adobe wordt aanbevolen Adobe Commerce 2.4.6-p1 alleen te gebruiken met Varnish Cache versie 7.3 of versie 6.0 LTS.

* **RabbitMQ 3.11-ondersteuning**. Deze release is compatibel met de nieuwste versie van RabbitMQ 3.11. Compatibiliteit blijft behouden met RabbitMQ 3.9, dat tot augustus 2023 wordt ondersteund, maar Adobe wordt alleen aanbevolen om Adobe Commerce 2.4.6-p1 te gebruiken met RabbitMQ 3.11.

* **JavaScript-bibliotheken**. Verouderde JavaScript-bibliotheken zijn bijgewerkt naar de nieuwste kleine versies of patchversies, waaronder `moment.js` bibliotheek (v2.29.4), `jQuery UI` bibliotheek (v1.13.2), en `jQuery` validatie-insteekbibliotheek (v1.19.5).

### Bekende problemen

* De `nginx.sample` bestand is per ongeluk bijgewerkt met een wijziging die de waarde van `fastcgi_pass` van `fastcgi_backend` tot `php-fpm:9000`. Deze wijziging kan veilig worden hersteld of genegeerd. <!-- AC-8992 -->

* Ontbrekende afhankelijkheden voor het B2B-beveiligingspakket veroorzaken de volgende installatiefout bij de installatie of upgrade van de B2B-extensie naar 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Dit probleem kan worden opgelost door handmatige afhankelijkheden voor het B2B-beveiligingspakket toe te voegen met een [stabiliteitstag](https://getcomposer.org/doc/04-schema.md#package-links). Zie voor meer informatie de [Opmerkingen bij de release B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).

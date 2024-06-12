---
title: Opmerkingen bij de release van Adobe Commerce 2.4.4 Beveiligingspatches
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.4

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.4-p9

De Adobe Commerce 2.4.4-p9 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.4 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-40 Adobe](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Platformupgrades

* **Ondersteuning voor MariaDB 10.5**. Deze patchrelease introduceert compatibiliteit met MariaDB versie 10.5. Adobe Commerce is nog steeds compatibel met MariaDB-versie 10.4, maar de Adobe raadt u aan Adobe Commerce 2.4.4-p9 te gebruiken en alle aanstaande patchreleases (alleen voor de beveiliging van 2.4.4) alleen met MariaDB-versie 10.5, omdat het onderhoud van MariaDB 10.4 eindigt op 18 juni 2024. <!--AC-11530-->

### Aanvullende beveiligingsverbeteringen

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4-p8

De Adobe Commerce 2.4.4-p8-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor uw Adobe Commerce 2.4.4-implementatie. Deze updates verhelpen kwetsbaarheden die zijn geïdentificeerd in vorige releases.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-18 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

De Adobe Commerce 2.4.4-p7 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-03 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Beveiligingsmarkeringen

Deze release introduceert twee belangrijke beveiligingsverbeteringen:

* **Wijzigingen in het gedrag van niet-gegenereerde cachesleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van de sjablooninstructie of de `setCacheKey` of `setData` methoden.)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten. <!-- AC-9831 -->

* **Beperkingen op het aantal automatisch gegenereerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaren kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) om deze nieuwe limiet in te stellen. <!-- AC-8753 -->

## 2.4.4-p6

De Adobe Commerce 2.4.4-p6-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die in eerdere releases zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-50 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

### Beveiligingsmarkering

Deze versie introduceert een nieuwe instelling voor de volledige paginacacheconfiguratie die helpt de risico&#39;s te beperken die aan de `{BASE-URL}/page_cache/block/esi HTTP` eindpunt. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de de lay-outhandvatten van de Handel en blokstructuren. De nieuwe **[!UICONTROL Handles Param]** configuratie het plaatsen plaatst de waarde van dit eindpunt `handles` parameter, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaren kunnen deze waarde wijzigen via de beheerfunctie (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Bekend probleem

**Probleem**: Adobe Commerce geeft een **verkeerde controlesom** fout tijdens downloaden door Composer van `repo.magento.com`en wordt het downloaden van het pakket onderbroken. Dit probleem kan optreden tijdens het downloaden van releasepakketten die tijdens de prerelease beschikbaar zijn gesteld en die worden veroorzaakt door een herverpakking van de `magento/module-page-cache` pakket.

**Workaround**: Merchants die deze fout tijdens het downloaden zien, kunnen de volgende stappen uitvoeren:

1) Verwijder de `/vendor` directory binnen het project, als er een bestaat.
2) Voer de `bin/magento composer update magento/module-page-cache` gebruiken. Met deze opdracht werkt u alleen de `page cache` pakket.

Als het probleem met de controlesom zich blijft voordoen, verwijdert u het gereedschap `composer.lock` bestand voordat het opnieuw wordt uitgevoerd `bin/magento composer update` gebruiken om elk pakket bij te werken.

## 2.4.4-p5

De Adobe Commerce 2.4.4-p5-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die in eerdere releases zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-42 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` Bibliotheekversie 1.13.1 heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die meerdere versies van Adobe Commerce en Magento Open Source beïnvloedt. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die betrokken implementaties uitvoeren, moeten de patch toepassen die in de [jQuery UI-beveiligingskwetsbaarheid CVE-2022-31160-oplossing voor 2.4.4-, 2.4.5- en 2.4.6-releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kennisbank, artikel.

## 2.4.4-p4

De Adobe Commerce 2.4.4-p4 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsupdates en platformupgrades om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-35 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### patch toepassen om beveiligingskwetsbaarheid CVE-2022-31160 te verhelpen in jQuery-UI-bibliotheek

`jQuery-UI` Bibliotheekversie 1.13.1 heeft een bekende kwetsbaarheid op het gebied van beveiliging (CVE-2022-31160) die meerdere versies van Adobe Commerce en Magento Open Source beïnvloedt. Deze bibliotheek is afhankelijk van Adobe Commerce en Magento Open Source 2.4.4, 2.4.5 en 2.4.6. Merchants die betrokken implementaties uitvoeren, moeten de patch toepassen die in de [jQuery UI-beveiligingskwetsbaarheid CVE-2022-31160-oplossing voor 2.4.4-, 2.4.5- en 2.4.6-releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kennisbank, artikel.

### Beveiligingsmarkering

Het standaardgedrag van de [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-query en ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Het REST-eindpunt is gewijzigd. De API retourneert nu standaard altijd `true`. Handelaren kunnen het oorspronkelijke gedrag inschakelen, dat wil zeggen terugsturen `true` als de e-mail niet bestaat in de database en `false` als het bestaat. <!-- AC-6695 -->

### Platformupgrades

Platformupgrades voor deze release verbeteren de naleving van de nieuwste best practices op het gebied van beveiliging.

* **Varnish cache 7.3-ondersteuning**. Deze release is compatibel met de nieuwste versie van Varnish Cache 7.3. De compatibiliteit blijft behouden met de 6.0.x- en 7u.2.x-versies, maar de Adobe raadt aan Adobe Commerce 2.4.4-p4 alleen te gebruiken met Varnish Cache versie 7.3 of versie 6.0 LTS.

* **RabbitMQ 3.11-ondersteuning**. Deze release is compatibel met de nieuwste versie van RabbitMQ 3.11. De compatibiliteit blijft behouden met RabbitMQ 3.9, dat tot augustus 2023 wordt ondersteund, maar Adobe beveelt aan om Adobe Commerce 2.4.4-p4 alleen te gebruiken met RabbitMQ 3.11.

* **JavaScript-bibliotheken**. Verouderde JavaScript-bibliotheken zijn bijgewerkt naar de nieuwste kleine versies of patchversies, waaronder `moment.js` bibliotheek (v2.29.4), `jQuery UI` bibliotheek (v1.13.2), en `jQuery` validatie-insteekbibliotheek (v1.19.5).

## 2.4.4-p3

De Adobe Commerce 2.4.4-p3 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB23-17 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

De Adobe Commerce 2.4.4-p2-beveiligingsrelease biedt oplossingen voor kwetsbaarheden die in eerdere releases zijn geïdentificeerd. Één moeilijke situatie omvat de verwezenlijking van een nieuwe configuratie het plaatsen. De **E-mailbevestiging vereisen als e-mail is gewijzigd** Met configuratie-instelling kunnen beheerders een e-mailbevestiging vereisen wanneer een beheerder zijn e-mailadres wijzigt. <!-- AC-6292-->

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB22-48 Adobe](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### AC-3022.patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Merchants die deze versies opstellen zouden moeten toepassen `AC-3022.patch` zo snel mogelijk DHL als scheepvaartmaatschappij aan te bieden. Zie de [Een patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Het artikel van de Kennisbank voor informatie over het downloaden en het installeren van de flard.

## 2.4.4-p1

De Adobe Commerce 2.4.4-p1-beveiligingsrelease biedt oplossingen voor kwetsbaarheden die in eerdere releases zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen om de naleving van de nieuwste best practices op het gebied van beveiliging te verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin Adobe](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Toepassen `AC-3022.patch` DHL blijft aanbieden als scheepvaartmaatschappij

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Merchants die deze versies opstellen zouden moeten toepassen `AC-3022.patch` zo snel mogelijk DHL als scheepvaartmaatschappij aan te bieden. Zie de [Een patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Het artikel van de Kennisbank voor informatie over het downloaden en het installeren van de flard.

### Beveiligingsmarkeringen

De verbeteringen van de veiligheid voor deze versie verbeteren naleving van recentste veiligheids beste praktijken, die omvatten:

* ACL de middelen zijn toegevoegd aan de Inventaris.
* De beveiliging van het voorraadsjabloon is verbeterd.

### Bekende problemen

**Probleem**: Web API- en integratietests tonen deze fout wanneer deze wordt uitgevoerd op het 2.4.4-p1-pakket: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Workaround**: Installeer de vorige versie van Monolog door het dialoogvenster `require monolog/monolog:2.6.0` gebruiken. <!-- AC-3651-->

**Probleem**: Merchants kunnen berichten over de downgradeprocedure voor de pakketversie opmerken tijdens een upgrade van Adobe Commerce 2.4.4 naar Adobe Commerce 2.4.4-p1. Deze berichten kunnen worden genegeerd. De discrepantie in pakketversies is het gevolg van anomalieën tijdens het genereren van pakketten. Dit heeft geen invloed op de productfunctionaliteit. Zie de [Pakketten die na een upgrade zijn gedowngraded van 2.4.4 naar 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Het artikel van de Kennisbank voor een bespreking van beïnvloede scenario&#39;s en alternerende actie.

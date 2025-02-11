---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 Verbeterde beveiliging

* **toegevoegde Steun van de Integriteit Subresource (SRI)** om aan PCI 4.0 vereisten voor controle van manuscriptintegriteit op betalingspagina&#39;s te voldoen. De ondersteuning van Subresource Integrity (SRI) biedt integriteitshashes voor alle JavaScript-elementen die zich in het lokale bestandssysteem bevinden. De standaardSRI eigenschap wordt uitgevoerd slechts op de betalingspagina&#39;s voor Admin en storefront gebieden. Handelaars kunnen de standaardconfiguratie echter uitbreiden naar andere pagina&#39;s. Zie [ Integriteit Subresource ](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) in de _Gids van de Ontwikkelaar van Commerce PHP_.<!--AC-1153-->

* **Veranderingen in het Beleid van de Veiligheid van de Inhoud (CSP)** - de updates en de verhogingen van de Configuratie aan het Beleid van de Veiligheid van de Veiligheid van de Inhoud van Adobe Commerce (CSPs) om aan PCI 4.0 vereisten te voldoen. Voor details, zie [ Beleid van de Veiligheid van de Inhoud ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _Gids van de Ontwikkelaar van Commerce PHP_. <!--AC-11513-->

   * De standaard CSP-configuratie voor betalingspagina&#39;s voor Commerce Admin- en storefront-gebieden is nu `restrict` -modus. Voor alle andere pagina&#39;s is de standaardconfiguratie de modus `report-only` .  In versies vóór 2.4.7, werd CSP gevormd op `report-only` wijze voor alle pagina&#39;s.

   * Een Nonce-provider toegevoegd om uitvoering van inline scripts in een CSP toe te staan. De nonce-provider vereenvoudigt het genereren van unieke nonce-tekenreeksen voor elke aanvraag. De tekenreeksen worden vervolgens aan de CSP-header gekoppeld.

   * Toegevoegde opties voor het configureren van aangepaste URI&#39;s voor het rapporteren van CSP-overtredingen voor de pagina Volgorde maken in Beheer en de pagina Uitchecken in de winkel. U kunt de configuratie toevoegen vanuit de beheerfunctie of door de URI toe te voegen aan het `config.xml` -bestand.

     >[!NOTE]
     >
     >Als u de CSP-configuratie bijwerkt naar de modus `restrict` , kunnen bestaande inlinescripts op betaalpagina&#39;s in de beheerdersinterface en de opslagront worden geblokkeerd. Dit leidt tot de volgende browserfout wanneer een pagina wordt geladen: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src` . Verbeter deze fouten door de whitelistconfiguratie bij te werken om vereiste manuscripten toe te staan. Zie [ het Oplossen van problemen ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) in de _Gids van de Ontwikkelaar van Commerce PHP_.

---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 Verbeterde beveiliging

* **Extra ondersteuning voor Integriteit subresource (SRI)** voldoen aan de vereisten van PCI 4.0 voor de verificatie van scriptintegriteit op betaalpagina&#39;s. De ondersteuning van Subresource Integrity (SRI) biedt integriteitshashes voor alle JavaScript-elementen die zich in het lokale bestandssysteem bevinden. De standaardSRI eigenschap wordt uitgevoerd slechts op de betalingspagina&#39;s voor Admin en storefront gebieden. Handelaars kunnen de standaardconfiguratie echter uitbreiden naar andere pagina&#39;s. Zie [Integriteit subresource](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) in de _Commerce PHP Developer Guide_.<!--AC-1153-->

* **Wijzigingen in inhoudsbeveiligingsbeleid (CSP)**—De updates van de configuratie en verhogingen van het Beleid van de Veiligheid van de Inhoud van Adobe Commerce (CSPs) om aan PCI 4.0 vereisten te voldoen. Zie voor meer informatie [Beveiligingsbeleid voor inhoud](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _Commerce PHP Developer Guide_. <!--AC-11513-->

   * De standaard CSP-configuratie voor betalingspagina&#39;s voor Commerce Admin- en storefrongebieden is nu `restrict` -modus. Voor alle andere pagina&#39;s is de standaardconfiguratie `report-only` -modus.  In versies voorafgaand aan 2.4.7, werd CSP gevormd binnen `report-only` voor alle pagina&#39;s.

   * Een Nonce-provider toegevoegd om uitvoering van inline scripts in een CSP toe te staan. De nonce-provider vereenvoudigt het genereren van unieke nonce-tekenreeksen voor elke aanvraag. De tekenreeksen worden vervolgens aan de CSP-header gekoppeld.

   * Toegevoegde opties voor het configureren van aangepaste URI&#39;s voor het rapporteren van CSP-overtredingen voor de pagina Volgorde maken in Beheer en de pagina Uitchecken in de winkel. U kunt de configuratie toevoegen vanuit de beheerdersinterface of door de URI toe te voegen aan de `config.xml` bestand.

     >[!NOTE]
     >
     >De CSP-configuratie bijwerken naar `restrict` De modus kan bestaande inlinescripts op betaalpagina&#39;s in Admin en storefront blokkeren, wat de volgende browserfout veroorzaakt wanneer een pagina wordt geladen: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Verbeter deze fouten door de whitelistconfiguratie bij te werken om vereiste manuscripten toe te staan. Zie [Problemen oplossen](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) in de _Commerce PHP Developer Guide_.

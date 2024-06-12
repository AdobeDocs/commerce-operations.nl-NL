---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 Verbeterde beveiliging

Er zijn tot op heden geen bevestigde aanvallen met betrekking tot deze problemen geweest. Bepaalde kwetsbaarheden kunnen echter potentieel worden benut om toegang te krijgen tot klantgegevens of om beheerderssessies over te nemen. De meeste van deze problemen vereisen dat een aanvaller eerst toegang verkrijgt tot de beheerder. Daarom herinneren we u eraan alle noodzakelijke stappen te nemen om uw beheerder te beschermen, inclusief, maar niet beperkt tot:

* IP-voegende op lijst van gewenste personen
* [Twee-factor authentificatie](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Gebruik van VPN
* Gebruik van een unieke locatie in plaats van `/admin`
* Goede wachtwoordhygiëne

De verbeteringen van de veiligheid voor deze versie verbeteren naleving van de recentste beste praktijken van de veiligheid.

* **Wijzigingen in het gedrag van niet-gegenereerde cachesleutels**:

   * Niet-gegenereerde cachesleutels voor blokken bevatten nu voorvoegsels die afwijken van voorvoegsels voor toetsen die automatisch worden gegenereerd. (Niet-gegenereerde cachesleutels zijn sleutels die zijn ingesteld via de syntaxis van de sjablooninstructie of de `setCacheKey` of `setData` methoden.)
   * Niet-gegenereerde cachesleutels voor blokken mogen nu alleen letters, cijfers, afbreekstreepjes (-) en onderstrepingstekens (_) bevatten.  <!-- AC-9831 -->

* **Beperkingen op het aantal automatisch gegenereerde couponcodes**. Commerce beperkt nu het aantal couponcodes dat automatisch wordt gegenereerd. Het standaardmaximum is 250.000. Handelaren kunnen de nieuwe **[!UICONTROL Code Quantity Limit]** configuratieoptie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) om te voorkomen dat het systeem met veel coupons wordt overweldigd. <!-- AC-8753 -->

* **Optimalisatie van het standaard URL-generatieproces van Admin**. Het genereren van de standaard Admin URL is geoptimaliseerd voor meer willekeur, waardoor gegenereerde URL&#39;s minder voorspelbaar worden. <!-- AC-9028 -->

* **Extra ondersteuning voor Integriteit subresource (SRI)** voldoen aan de vereisten van PCI 4.0 voor de verificatie van scriptintegriteit op betaalpagina&#39;s. De ondersteuning van Subresource Integrity (SRI) biedt integriteitshashes voor alle JavaScript-elementen die zich in het lokale bestandssysteem bevinden. De standaardSRI eigenschap wordt uitgevoerd slechts op de betalingspagina&#39;s voor Admin en storefront gebieden. Handelaars kunnen de standaardconfiguratie echter uitbreiden naar andere pagina&#39;s. Zie [Integriteit subresource](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) in de _Commerce PHP Developer Guide_.<!--AC-1153-->

* **Wijzigingen in inhoudsbeveiligingsbeleid (CSP)**—De updates van de configuratie en verhogingen van het Beleid van de Veiligheid van de Inhoud van Adobe Commerce (CSPs) om aan PCI 4.0 vereisten te voldoen. Zie voor meer informatie [Beveiligingsbeleid voor inhoud](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _Commerce PHP Developer Guide_. <!--AC-11513-->

   * De standaard CSP-configuratie voor betalingspagina&#39;s voor Commerce Admin- en storefrongebieden is nu `restrict` -modus. Voor alle andere pagina&#39;s is de standaardconfiguratie `report-only` -modus.  In versies voorafgaand aan 2.4.7, werd CSP gevormd binnen `report-only` voor alle pagina&#39;s.

   * Een Nonce-provider toegevoegd om uitvoering van inline scripts in een CSP toe te staan. De nonce-provider vereenvoudigt het genereren van unieke nonce-tekenreeksen voor elke aanvraag. De tekenreeksen worden vervolgens aan de CSP-header gekoppeld.

   * Toegevoegde opties voor het configureren van aangepaste URI&#39;s voor het rapporteren van CSP-overtredingen voor de pagina Volgorde maken in Beheer en de pagina Uitchecken in de winkel. U kunt de configuratie toevoegen vanuit de beheerdersinterface of door de URI toe te voegen aan de `config.xml` bestand.

     >[!NOTE]
     >
     >De CSP-configuratie bijwerken naar `restrict` De modus kan bestaande inlinescripts op betaalpagina&#39;s in Admin en storefront blokkeren, wat de volgende browserfout veroorzaakt wanneer een pagina wordt geladen: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Verbeter deze fouten door de whitelistconfiguratie bij te werken om vereiste manuscripten toe te staan. Zie [Problemen oplossen](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) in de _Commerce PHP Developer Guide_.

* Een nieuwe instelling voor de configuratie van de cache van volledige pagina&#39;s kan de risico&#39;s beperken die aan HTTP zijn gekoppeld `{BASE-URL}/page_cache/block/esi` eindpunt. Dit eindpunt steunt onbeperkte, dynamisch geladen inhoudsfragmenten van de de lay-outhandvatten van de Handel en blokstructuren. De nieuwe **[!UICONTROL Handles params size]** configuratie het plaatsen plaatst de waarde van dit eindpunt `handles` parameter, die het maximaal toegestane aantal handgrepen per API bepaalt. De standaardwaarde van deze eigenschap is 100. Handelaren kunnen deze waarde wijzigen via de beheerfunctie (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Zie [De Commerce-toepassing configureren voor het gebruik van Varnish](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Native tariefbeperking voor via REST en GraphQL API&#39;s verzonden betalingsinformatie**. Handelaren kunnen nu [snelheidsbeperking configureren](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) voor de betalingsgegevens die via REST en GraphQL worden verstrekt. Deze extra laag van bescherming steunt preventie van het behandelen van aanvallen en vermindert potentieel het volume van het behandelen aanvallen die vele creditcardaantallen in één keer testen. Dit is een verandering in het standaardgedrag van een bestaand REST eindpunt. Zie [Snelheidbeperking](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* Het standaardgedrag van de [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-query en de ([V1/customer/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Het REST-eindpunt is gewijzigd. Standaard retourneren de API&#39;s nu altijd `true`. Handelaren kunnen het oorspronkelijke gedrag inschakelen door het instellen van de *[Aanmelden voor uitchecken van gasten inschakelen](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* in de beheerdersruimte `yes`, maar als u dit doet, kunnen de klantgegevens beschikbaar worden gemaakt voor niet-geverifieerde gebruikers.

---
title: 'Beheerde alarm voor Adobe Commerce: [!DNL Apdex]  kritiek alarm'
description: Dit artikel verstrekt het oplossen van problemenstappen wanneer u een  [!DNL Apdex]  kritieke alarm voor Adobe Commerce in  [!DNL New Relic]. The [!DNL Apdex]  ontvangt score gebruikers' tevredenheid aan de reactietijd van Webtoepassingen en de diensten. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 028e9b3ba60c10c7c09672888a058ca34faeb365
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: [!DNL Apdex] kritieke waarschuwing

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een [!DNL Apdex] kritieke waarschuwing voor Adobe Commerce ontvangt in [!DNL New Relic] . De [!DNL Apdex] score meet de tevredenheid van gebruikers over de responstijd van webtoepassingen en -services. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ toepassing kritieke alarm ](../../assets/managed-alerts/apdex-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur
* Adobe Commerce on cloud Infrastructure Starter-planarchitectuur

## Probleem

U zult een beheerde alarm in [!DNL New Relic] ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om handelaren een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, verwijs naar [ toelaten of onbruikbaar maken onderhoudswijze ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) in de Gids van de Installatie van Commerce.

<u>**niet!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexeerders of extra kranen uit die extra druk op CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (zoals de Commerce Admin, gegevensimport/export).
* Wis uw cache.

Als u een kritische waarschuwing hebt ontvangen voordat u de oorzaak van de waarschuwing hebt opgelost, reageert uw site mogelijk niet meer als u nog geen probleem hebt met de site.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u **Stap 1** voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar [ Spoor uw steunkaartjes ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) in de Kennisbank van de Steun van Commerce. Ondersteuning kan een drempelwaardewaarschuwing van [!DNL New Relic] hebben ontvangen, een ticket hebben gemaakt en aan het probleem hebben gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer **[!UICONTROL New Relic CRITICAL alert received]**.
   * Beschrijving van de signalering.
   * [[!DNL New Relic]  verbinding van het Ongeval ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md).
1. Om de bron van het probleem te identificeren, gebruik {de pagina van de Transactie van 0} APM [&#128279;](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieskwesties te identificeren:[!DNL New Relic] 
   * Transacties sorteren door oplopende [!DNL Apdex] scores. [[!DNL Apdex] ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar gebruikerstevredenheid aan de reactietijd van uw Webtoepassingen en de diensten. Een lage [!DNL Apdex] score kan op een knelpunt wijzen (een transactie met een hogere reactietijd). Meestal is dit de database, [!DNL Redis] of PHP. Voor stappen, verwijs naar [[!DNL New Relic]  transacties van de Mening met de hoogste ontevredenheid van de Index ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Voor stappen, verwijs naar [[!DNL New Relic]  Vondst specifieke prestatiesproblemen ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u nog worstelt om de kwestie te identificeren gebruikt [[!DNL New Relic]  APM&#39;s pagina van de Infrastructuur van de IPM ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. De pagina van de Infrastructuur van APM van het gebruik [&#128279;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) om middel intensieve processen te identificeren. [!DNL New Relic]  Voor stappen, verwijs naar [[!DNL New Relic]  de pagina van de Gastheren van de Controle van de Infrastructuur: [!UICONTROL Processes tab] ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als services als [!DNL Redis] of MySQL de belangrijkste bron van geheugenverbruik zijn, kunt u het volgende proberen:
   * Controleer of u de meest recente versie hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Voor stappen, verwijs naar [ Diensten van de Verandering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=nl-NL) in Commerce op de Gids van de Wolk.
   * Controleer of er MySQL-problemen zijn, zoals query&#39;s die lang worden uitgevoerd, primaire sleutels die niet zijn gedefinieerd en dubbele indexen. Voor stappen, verwijs naar [ Veelvoorkomende gegevensbestandKwesties in Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=nl-NL) in het Playbook van de Implementatie van Commerce.
   * Controleren op PHP-problemen. Herzie lopende processen door `ps aufx` in CLI/Terminal in werking te stellen. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, verwijs naar [ Trage prestaties, langzame en lange lopende kronnen ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) en [ baan van het Gewas geplakt in &quot;lopende&quot;status ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) in de Kennisbank van de Steun van Commerce.

1. Zodra de bron is geïdentificeerd, bevindt SSH zich in het milieu om verder te onderzoeken. Voor stappen, verwijs naar [ SSH in uw milieu ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) in Commerce op de Gids van de Wolk.
1. Als u nog worstelt om de bron te identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als u niet binnen een redelijke termijn een oplossing kunt vinden, verzoek om een vergrote of plaats in onderhoudswijze als u nog niet hebt gedaan. Voor stappen, verwijs naar [ hoe te om tijdelijke resize ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) in onze Kennisbank van de Steun van Commerce te verzoeken, en [ laat of maak onderhoudswijze ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce toe onbruikbaar.
1. Als de upsize de plaats aan normale verrichtingen terugkeert, overweeg om permanent te verzoeken (uw Team van de Rekening van Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Verwijs naar [ Lading en stress het testen ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in Commerce op de Gids van de Wolk.

---
title: 'Beheerde waarschuwingen over Adobe Commerce: kritieke geheugenwaarschuwing'
description: Dit artikel verstrekt het oplossen van problemenstappen wanneer u een geheugen kritieke alarm voor Adobe Commerce in  [!DNL New Relic] ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90047f6e-d90a-4980-9700-84c44f2b8494
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Beheerde waarschuwingen over Adobe Commerce: kritieke geheugenwaarschuwing

Dit artikel bevat stappen voor het oplossen van problemen wanneer u in [!DNL New Relic] een kritieke waarschuwing over het geheugen voor Adobe Commerce ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen.

![ schijf kritiek alarm ](../../assets/managed-alerts/memory-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

Alle versies van Adobe Commerce op cloudinfrastructuur Pro plannen.

## Probleem

U zult een beheerde alarm in [!DNL New Relic] ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, zie [ toelaten of onbruikbaar maken onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, zie [ de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) in de Gids van de Installatie van Commerce handhaven.

<u>**niet!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexeerders of extra kranen uit die extra druk op CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

Uw site reageert mogelijk niet meer (als er nog geen site-uitval optreedt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u **Stap 1** voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, zie [ Spoor uw steunkaartjes ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) in de Kennisbank van de Steun van Commerce. Ondersteuning heeft mogelijk al een drempelwaardewaarschuwing van [!DNL New Relic] ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer **[!UICONTROL New Relic]** KRITIEKE waarschuwing ontvangen
   * Beschrijving van de signalering
   * [[!DNL New Relic]  verbinding van het Ongeval ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md).

1. De pagina van de Infrastructuur van APM van het gebruik [[!DNL New Relic]  om hoogste geheugen intensieve processen te identificeren. ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) Voor stappen, verwijs naar [[!DNL New Relic]  de pagina van de Gastheren van de Infrastructuur controleren: Het lusje van Processen ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Als services zoals [!DNL Redis], MySQL of PHP de belangrijkste bronnen van geheugenverbruik zijn, probeert u het volgende:
1. Controleer of u de meest recente versies hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Voor stappen, verwijs naar [ Diensten van de Verandering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in Commerce op de Gids van de Wolk.
1. Als het probleem met de service geen versiegerelateerd probleem is, probeert u het volgende:
1. **MySQL**: Controle voor kwesties zoals lange lopende vragen, Primaire sleutels bepaald niet, en dubbele indexen. Voor stappen, verwijs naar [ Veelvoorkomende gegevensbestandKwesties in Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in het Playbook van de Implementatie van Commerce.
1. **[!DNL Redis]**: Als [!DNL Redis] een hoogste bron van geheugenconsumptie is, [ voorlegt een steunkaartje ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
1. **PHP**: Als PHP een hoogste bron van geheugenconsumptie is, herzie lopende processen door `ps aufx` in CLI/Terminal in werking te stellen. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, zie [ Trage prestaties, langzame en lange lopende kronen ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) en [ baan van het Gewas die in &quot;lopende&quot;status ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) in de Kennisbank van de Steun van Commerce wordt geplakt.
1. Als u nog worstelt om de bron van het probleem te identificeren, gebruik {de pagina van de Transactie van 0} APM [[!DNL New Relic]  om transacties met prestatieskwesties te identificeren:](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)
   * Transacties sorteren door oplopende [!DNL Apdex] scores. [[!DNL Apdex] ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar gebruikerstevredenheid aan de reactietijd van uw Webtoepassingen en de diensten. Een [[!DNL Apdex score]](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, [!DNL  Redis] of PHP. Voor stappen, verwijs naar [[!DNL New Relic]  transacties van de Mening met hoogste  [!DNL Apdex]  ontevredenheid ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Voor stappen, verwijs naar [[!DNL New Relic]  [vind specifieke prestatiesproblemen] ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u nog worstelt om de kwestie te identificeren, gebruik [[!DNL New Relic]  APM&#39;s pagina van de Infrastructuur van de APM ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Als u niet de oorzaak van verhoogde geheugenconsumptie kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen 7 dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als de bovenstaande methoden u niet helpen de oorzaak en/of oplossing binnen een redelijke tijd te vinden, kunt u een upgrade aanvragen of de site in de onderhoudsmodus plaatsen als u dat nog niet hebt gedaan. Voor stappen, zie [ hoe te om temp te verzoeken resize ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) in de Kennisbank van de Steun van Commerce, en [ laat of maakt onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce toe onbruikbaar.
1. Als de upsize de plaats aan normale verrichtingen terugkeert, overweeg om permanent te verzoeken (uw Team van de Rekening van Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Zie [ Lading en stress het testen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in Commerce op de Gids van de Wolk.

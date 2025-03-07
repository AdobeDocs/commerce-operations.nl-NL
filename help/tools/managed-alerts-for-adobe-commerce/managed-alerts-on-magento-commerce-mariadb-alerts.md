---
title: 'Beheerde waarschuwingen over Adobe Commerce: MariaDB-waarschuwingen'
description: Dit artikel verstrekt het oplossen van problemenstappen wanneer u waarschuwingen MariaDB voor Adobe Commerce in  [!DNL New Relic] ontvangt. Het MariaDB- alarm controleert hoge vraaglading evenals bovenmatige vragen van de Manipulatie van Gegevens van de Taal (DML). Beide kunnen leiden tot een verminderde gebruikerservaring of zelfs downtime. U kunt twee soorten waarschuwingen ontvangen.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: ccf8b7c5ad1fbef2cfba05f65f05ab8af0375b4c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Beheerde waarschuwingen over Adobe Commerce: MariaDB-waarschuwingen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u MariaDB-waarschuwingen voor Adobe Commerce ontvangt in [!DNL New Relic] . Het MariaDB- alarm controleert hoge vraaglading evenals bovenmatige vragen van de Manipulatie van Gegevens van de Taal (DML). Beide kunnen leiden tot een verminderde gebruikerservaring of zelfs downtime. U kunt twee soorten waarschuwingen ontvangen:

* Waarschuwing DML-query&#39;s
* DML vraagt kritiek

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

U zult een beheerde alarm in [!DNL New Relic] ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

**doe!**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, verwijs naar [ toelaten of onbruikbaar maken onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Beëindig alle scripts, zoals import die de oorzaak van de waarschuwing kunnen zijn als de prestaties van de site worden beïnvloed.

**niet!**

* Voer indexeerders of extra kranen uit die extra druk op MariaDB kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

## Oplossing

**Vragen DML (vragen die het gegevensbestand gebruikend UPDATE, INSERT, en DELETE) wijzigen**

Als u een Kritieke alarm van Vragen DML ontvangt, begin bij stap één. Als u een waarschuwing van de Vragen DML ontvangt, begin bij stap twee.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar onze kennisbasis [ Spoor uw steunkaartjes ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). Ondersteuning kan een drempelwaardewaarschuwing van [!DNL New Relic] hebben ontvangen, een ticket hebben gemaakt en aan het probleem hebben gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer **[!UICONTROL New Relic MariaDB alert received]**.
   * Beschrijving van de signalering.
   * [[!DNL New Relic]  verbinding van het Ongeval ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md).
1. Om de bron van de kwestie te identificeren, probeer om de vragen te identificeren DML:
   1. Herzie uw gegevensbestandverrichtingen door stappen van New Relic [ pagina van Gegevensbestanden te gebruiken ](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
   1. Sorteer op **[!UICONTROL CALL COUNT]** en vervolgens op **[!UICONTROL OPERATION]** . Reviseer `INSERT` -, `DELETE` - en `UPDATE` -bewerkingen.
   1. Kies voor een hoge AVG.
   1. Klik door om de bezoekers van de gegevensbestandverrichting te vinden. Dit zal transacties identificeren die die vraag tegen tijd gebruiken.
   1. Zoek uit of code optimaliseert, of operationele optimalisaties:
      * Codeoptimalisaties: kijk hoe u query&#39;s kunt optimaliseren met bulkinvoegingen / updates, het indexgebruik kunt minimaliseren of code kunt vertragen.
      * Operationele optimalisaties: Verplaats de hulpmiddelintensieve gegevenswijzigingen aan lagere verkeerstijden.
      * Aanvullende optimalisaties: zorg dat u de nieuwste versie van ECE-Tools gebruikt. Voor stappen, verwijs naar [ update van de knoop-hulpmiddelen versie ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) in Commerce op de Gids van de Wolk.

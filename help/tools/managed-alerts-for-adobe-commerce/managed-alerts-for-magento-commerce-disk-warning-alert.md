---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor een schijf'
description: Dit artikel verstrekt het oplossen van problemenstappen wanneer u een waarschuwingsschijfalarm voor Adobe Commerce in  [!DNL New Relic] ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3ad22e3a113b52da6d6095103376fee6e36dc804
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor een schijf

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing voor een Adobe Commerce ontvangt in [!DNL New Relic] . Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ waarschuwing van de schijfwaarschuwing ](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, Pro-planarchitectuur.

## Probleem

U zult een alarm in [!DNL New Relic] ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen verwijzen naar [ toelaten of onbruikbaar maken onderhoudswijze ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) in de Gids van de Installatie van Commerce.

<u> **niet!** </u>

* Start aanvullende marketingcampagnes die mogelijk extra paginaweergaven naar uw site brengen.
* Voer indexeerders of extra kranen uit die extra druk op CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache. Uw site reageert mogelijk niet meer (als er nog geen site-uitval optreedt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen:

1. Controleer in [!DNL New Relic] de schijven voor optimaal gebruik. Voor stappen verwijzen naar **[!UICONTROL Storage]** lusje op [[!DNL New Relic]  de pagina van de Gastheren van de Controle van de Infrastructuur: [!UICONTROL Storage] lusje ](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Als u in [!DNL New Relic] een trage toename van het schijfgebruik ziet, probeert u de volgende opties:
      * Schijfruimte optimaliseren door ruimtetoewijzing aan te passen. Voor stappen, verwijs naar [ beheer de ruimte van de Schijf ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) in Commerce op de Gids van de Wolk. Mogelijk moet u ook meer schijfruimte aanvragen (neem contact op met uw Adobe-accountteam).
      * Maak schijfruimte vrij voor MySQL. Verwijs naar [ MySQL schijfruimte is laag ](http://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) voor stappen.
      * Als [!DNL New Relic] een snel toenemend schijfgebruik weergeeft, kan dit erop wijzen dat er een probleem is dat ertoe heeft geleid dat een bestand in een map zeer snel is toegenomen. Voer de volgende controles uit:
         1. Controleer algemene schijfruimte om het probleem te identificeren door het volgende bevel in CLI/Terminal in werking te stellen: `df -h`
         1. Nadat u een folder met onverwacht groot en toenemend schijfgebruik identificeert, moet u het beïnvloede dossiersysteem controleren. In het volgende voorbeeld wordt getoond hoe u de bestandsmap `pub/media/` kunt controleren. Dit is de map die Adobe Commerce gebruikt voor het opslaan van logbestanden en grote mediabestanden. U moet deze opdracht echter uitvoeren voor elke map waarin onverwacht schijfgebruik wordt getoond: `du -sch ~/pub/media/*` .

Als in de uitvoer van de terminal een bestand in een van deze mappen wordt weergegeven, neemt het schijfgebruik snel toe en weet u dat de inhoud van het bestand niet nodig is, kunt u het bestand verwijderen. Als u niet comfortabel het nemen van deze actie bent, [ voorleggen een de steunkaartje van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

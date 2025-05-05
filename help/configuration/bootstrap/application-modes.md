---
title: Toepassingsmodi
description: De Commerce-toepassing kan naar wens in verschillende modi worden uitgevoerd. Bekijk een gedetailleerde lijst met de beschikbare toepassingsmodi.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Toepassingsmodi

U kunt de toepassing van Commerce op om het even welke volgende _wijzen_ in werking stellen:

| Naam van modus | Beschrijving | Ondersteuning voor cloud |
| ------------------------ | ------------------- | ------------- |
| [ gebrek ](#default-mode) | Implementeer en voer de Commerce-toepassing uit op één server zonder de instellingen te wijzigen. _niet_ geoptimaliseerd voor productie. | nee |
| [ ontwikkelaar ](#developer-mode) | Ideaal voor ontwikkeling wanneer u de Commerce-toepassing uitbreidt of aanpast. | nee |
| [ productie ](#production-mode) | Implementeer en voer de Commerce-toepassing uit op een productiesysteem. | Ja |
| [ onderhoud ](#maintenance-mode) | Toegang tot een site verhinderen tijdens het uitvoeren van updates en configuraties. | Ja |

Zie [ plaats de verrichtingswijze ](../cli/set-mode.md) om te leren hoe te om de de verrichtingswijzen van Adobe Commerce manueel te veranderen.

## Ondersteuning voor cloud

Vanwege het alleen-lezen bestandssysteem is er een strikte beperking voor het wijzigen van de modi in externe cloudomgevingen en kan dit systeem niet worden overschreven door Adobe Commerce Support. Probeer niet om modi te wijzigen door het bestand `app/etc/env.php` te wijzigen, omdat het bestand met het pakket `ece-tools` wordt overschreven op basis van meerdere configuratiebronnen.

Adobe Commerce op wolkeninfrastructuur stelt automatisch de toepassing op _onderhoud_ wijze tijdens een plaatsing in werking, die uw plaats offline neemt tot de plaatsing volledig is. Anders, blijft de toepassing op _productie_ wijze. Zie [ proces van de Plaatsing ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=nl-NL#deploy-phase) in _Commerce op de gids van de Infrastructuur van de Wolk_.

Als u het Dok van de Wolk voor Commerce als ontwikkelingshulpmiddel gebruikt, kunt u uw project van de wolkeninfrastructuur in een milieu van het Dok in _wijze van de ontwikkelaar {opstellen 0}, maar de prestaties zijn langzamer wegens extra verrichtingen van de dossiersynchronisatie._ Zie [ het milieu van de Dokker ](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) in het _Dok van de Wolk voor de gids van Commerce_ opstellen.


## Standaardmodus

De _standaard_ wijze laat u toe om de toepassing van Commerce op één enkele server op te stellen zonder enige montages te veranderen. De standaardmodus is echter niet geoptimaliseerd voor productie vanwege het negatieve effect van statische bestanden op de prestaties. Het maken van statische bestanden en het in cache plaatsen ervan heeft meer invloed op de prestaties dan het genereren van bestanden met het gereedschap voor het maken van statische bestanden.

In de standaardmodus:

- Uitzonderingen worden naar logbestanden geschreven in plaats van weer te geven
- Statische weergavebestanden worden in cache geplaatst
- Verbergt aangepaste `X-Magento-*` HTTP-aanvraag- en antwoordheaders

Commerce werkt in de standaardmodus als er geen andere modus is opgegeven.

## Modus Ontwikkelaar

De _ontwikkelaar_ wijze wordt geadviseerd voor het uitbreiden van en het aanpassen van de toepassing van Commerce. Statische weergavebestanden worden niet in de cache opgeslagen, maar worden op verzoek naar de map `pub/static` geschreven.

In de modus Ontwikkelaar:

- Laat [ automatische codecompilatie ](../cli/code-compiler.md) en verbeterde het zuiveren toe
- Niet-afgevangen uitzonderingen worden in de browser weergegeven
- Systeemaanmelding `var/report` is verbose
- Er wordt een uitzondering gegenereerd in de fouthandler, in plaats van dat deze wordt geregistreerd
- Een uitzondering wordt gegenereerd wanneer een gebeurtenisabonnee niet kan worden aangeroepen
- Aangepaste HTTP-aanvraag- en antwoordheaders `X-Magento-*` weergeven

>[!NOTE]
>
>Deze modus wordt niet ondersteund in de Adobe Commerce Cloud-omgeving en Adobe Commerce Support kan het wijzigen van de toepassingsmodus niet vergemakkelijken.

## Productiemodus

De _productie_ wijze is best om de toepassing van Commerce op een productiesysteem op te stellen. Na het optimaliseren van het servermilieu, zoals het gegevensbestand en de Webserver, zou u het [ statische hulpmiddel van de plaatsing van meningsdossiers ](../cli/static-view-file-deployment.md) in werking moeten stellen om statische meningsdossiers aan de `pub/static` folder te schrijven. Dit verbetert de prestaties door alle noodzakelijke statische bestanden tijdens de implementatie te bieden in plaats van de Commerce-toepassing te dwingen om tijdens de runtime dynamisch statische bestanden op aanvraag te zoeken en te kopiëren (materialiseren).

Sommige gebieden, zoals de Geavanceerde en secties van de de systeemconfiguratie van de Ontwikkelaar in Admin, zijn niet beschikbaar op productiemodus. Bijvoorbeeld, kunt u _niet_ toelaten of geheim voorgeheugentypes onbruikbaar maken gebruikend Admin. U kunt geheim voorgeheugentypes _toelaten en onbruikbaar maken slechts_ gebruikend de [ bevellijn ](../cli/manage-cache.md#config-cli-subcommands-cache-en).

In de productiemodus:

- Statische weergavebestanden worden alleen via de cache verzonden
- Fouten en uitzonderingen worden geregistreerd bij het bestandssysteem en worden nooit weergegeven bij de gebruiker
- Sommige configuratievelden in de beheerder zijn niet beschikbaar

## Onderhoudsmodus

De _wijze van het 0&rbrace; onderhoud &lbrace;beperkt of verhindert toegang tot een plaats tijdens verbeteringen, updates, en configuratietaken._ Standaard leidt de site bezoekers om naar een standaardpagina van `Service Temporarily Unavailable` .

U kunt a [ pagina van het douaneonderhoud ](../../upgrade/troubleshooting/maintenance-mode-options.md) tot stand brengen, manueel toelaten en onderhoudswijze onbruikbaar maken, en onderhoudswijze vormen om bezoekers van erkende IP adressen toe te staan om de opslag normaal te bekijken. Zie [ toelaten en onderhoudswijze ](../../installation/tutorials/maintenance-mode.md) in onbruikbaar maken in de _Gids van de Installatie_.

Als u Commerce gebruikt op cloudinfrastructuur, wordt de Commerce-toepassing tijdens de implementatiefase uitgevoerd in de onderhoudsmodus. Wanneer de implementatie met succes is voltooid, keert de Commerce-toepassing terug naar de productiemodus. Zie [ de haken van de Plaatsing ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=nl-NL#phase-5%3A-deployment-hooks) in _Commerce op de gids van de Infrastructuur van de Wolk_.

In de onderhoudsmodus:

- Site-bezoekers worden omgeleid naar een standaardpagina van `Service Temporarily Unavailable`
- De map `var/` bevat het `.maintenance.flag` -bestand
- U kunt bezoekerstoegang beperken die op IP adressen wordt gebaseerd

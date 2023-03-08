---
title: Toepassingsmodi
description: De toepassing van de Handel kan op verschillende wijzen afhankelijk van uw behoeften werken. Bekijk een gedetailleerde lijst met de beschikbare toepassingsmodi.
source-git-commit: e7c325aef90d4135218b984cc57df2c8d1d921d2
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---


# Toepassingsmodi

U kunt de toepassing van de Handel in om het even welk volgend in werking stellen _modi_:

| Naam van modus | Beschrijving | Ondersteuning voor cloud |
| ------------------------ | ------------------- | ------------- |
| [default](#default-mode) | Implementeer en voer de toepassing Commerce op één server uit zonder instellingen te wijzigen. _Niet_ geoptimaliseerd voor productie. | nee |
| [ontwikkelaar](#developer-mode) | Ideaal voor ontwikkeling wanneer u de toepassing Commerce uitbreidt of aanpast. | nee |
| [productie](#production-mode) | Stel en stel de toepassing van de Handel in werking op een productiesysteem. | Ja |
| [onderhoud](#maintenance-mode) | Toegang tot een site verhinderen tijdens het uitvoeren van updates en configuraties. | Ja |

Zie [De bewerkingsmodus instellen](../cli/set-mode.md) voor informatie over het handmatig wijzigen van de Adobe Commerce-bewerkingsmodi.

## Ondersteuning voor cloud

Het is niet nodig om de toepassingsmodi voor een project van de wolkeninfrastructuur te beheren. Vanwege het alleen-lezen bestandssysteem kunt u geen modi wijzigen in externe cloudomgevingen. Adobe Commerce on cloud Infrastructure voert de toepassing automatisch uit in _onderhoud_ wijze tijdens een plaatsing, die uw plaats offline neemt tot de plaatsing volledig is. Anders blijft de toepassing in _productie_ in. Zie [Implementatieproces](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) in de _Handleiding Handel in Cloud-infrastructuur_.

Als u Cloud Docker voor Handel als ontwikkelingsinstrument gebruikt, kunt u uw cloudinfrastructuurproject in een Docker-omgeving implementeren in _ontwikkelaar_ , maar de prestaties zijn trager als gevolg van extra bewerkingen voor bestandssynchronisatie. Zie [De Docker-omgeving implementeren](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) in de _Handleiding Cloud Docker voor handel_.

## Standaardmodus

De _default_ De wijze laat u toe om de toepassing van de Handel op één enkele server op te stellen zonder enige montages te veranderen. De standaardmodus is echter niet geoptimaliseerd voor productie vanwege het negatieve effect van statische bestanden op de prestaties. Het maken van statische bestanden en het in cache plaatsen ervan heeft meer invloed op de prestaties dan het genereren van bestanden met het gereedschap voor het maken van statische bestanden.

In de standaardmodus:

- Uitzonderingen worden naar logbestanden geschreven in plaats van weer te geven
- Statische weergavebestanden worden in cache geplaatst
- Verbergt aangepaste `X-Magento-*` HTTP-aanvraag- en antwoordheaders

De handel werkt op standaardwijze als geen andere wijze wordt gespecificeerd.

## Modus Ontwikkelaar

De _ontwikkelaar_ wordt aanbevolen voor het uitbreiden en aanpassen van de toepassing Commerce. Statische weergavebestanden worden niet in de cache opgeslagen, maar naar de `pub/static` directory on demand.

In de modus Ontwikkelaar:

- Inschakelen [automatische codecompilatie](../cli/code-compiler.md) en verbeterde foutopsporing
- Niet-afgevangen uitzonderingen worden in de browser weergegeven
- Systeemaanmelding `var/report` is uitgebreid
- Er wordt een uitzondering gegenereerd in de fouthandler, in plaats van dat deze wordt geregistreerd
- Een uitzondering wordt gegenereerd wanneer een gebeurtenisabonnee niet kan worden aangeroepen
- Aangepaste tonen `X-Magento-*` HTTP-aanvraag- en antwoordheaders

## Productiemodus

De _productie_ De wijze is best voor het opstellen van de toepassing van de Handel op een productiesysteem. Nadat u de serveromgeving, zoals de database en de webserver, hebt geoptimaliseerd, moet u de opdracht [hulpmiddel voor het implementeren van statische weergavebestanden](../cli/static-view-file-deployment.md) om statische weergavebestanden naar de `pub/static` directory. Dit verbetert prestaties door alle noodzakelijke statische dossiers bij plaatsing te verstrekken in plaats van de toepassing van de Handel te dwingen om dynamisch van statische dossiers de plaats te bepalen en te kopiëren (materialiseren) tijdens runtime.

Sommige gebieden, zoals de Geavanceerde en secties van de de systeemconfiguratie van de Ontwikkelaar in Admin, zijn niet beschikbaar op productiemodus. U kunt bijvoorbeeld _kan_ Schakel cachetypen in of uit met behulp van Admin. U kunt cachetypen in- en uitschakelen _alleen_ met de [opdrachtregel](../cli/manage-cache.md#config-cli-subcommands-cache-en).

In de productiemodus:

- Statische weergavebestanden worden alleen via de cache verzonden
- Fouten en uitzonderingen worden geregistreerd bij het bestandssysteem en worden nooit weergegeven bij de gebruiker
- Sommige configuratievelden in de beheerder zijn niet beschikbaar

## Onderhoudsmodus

De _onderhoud_ de wijze beperkt of verhindert toegang tot een plaats tijdens verbeteringen, updates, en configuratietaken. Standaard leidt de site bezoekers om naar de standaardmap `Service Temporarily Unavailable` pagina.

U kunt een [aangepaste onderhoudspagina](../../upgrade/troubleshooting/maintenance-mode-options.md), laat manueel en maakt onderhoudswijze onbruikbaar, en vormt onderhoudswijze om bezoekers van erkende IP adressen toe te staan om de opslag normaal te bekijken. Zie [de onderhoudsmodus in- en uitschakelen](../../installation/tutorials/maintenance-mode.md) in de _Installatiehandleiding_.

Als u Handel op wolkeninfrastructuur gebruikt, loopt de toepassing van de Handel op onderhoudswijze tijdens de opstellen fase. Wanneer de plaatsing met succes voltooit, keert de toepassing van de Handel aan lopende op productiemodus terug. Zie [Implementatiehaken](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) in de _Handleiding Handel in Cloud-infrastructuur_.

In de onderhoudsmodus:

- Sitebezoekers worden omgeleid naar de standaardversie `Service Temporarily Unavailable` page
- De `var/` bevat de map `.maintenance.flag` file
- U kunt bezoekerstoegang beperken die op IP adressen wordt gebaseerd

---
title: Toepassingsmodi
description: De toepassing van de Handel kan op verschillende wijzen afhankelijk van uw behoeften werken. Bekijk een gedetailleerde lijst met de beschikbare toepassingsmodi.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Toepassingsmodi

U kunt de toepassing van de Handel in om het even welk volgend in werking stellen _modi_:

| Modulenaam | Beschrijving |
| ----------- | ----------- |
| default | Laat u toe om de toepassing van de Handel op één enkele server op te stellen zonder enige montages te veranderen. De standaardmodus is echter niet geoptimaliseerd voor productie.<br>Om de toepassing van de Handel op meer dan één server op te stellen of het voor productie te optimaliseren, verander in één van de andere wijzen.<ul><li>Statische weergave van bestanden in cache plaatsen ingeschakeld</li><li>De uitzonderingen worden niet getoond aan de gebruiker; in plaats daarvan worden uitzonderingen naar logbestanden geschreven .</li><li>Verbergt aangepaste `X-Magento-*` HTTP-aanvraag- en antwoordheaders</li></ul> |
| ontwikkelaar | Deze modus is alleen bedoeld voor ontwikkeling:<ul><li>Schakelt het in cache plaatsen van statische weergavebestanden uit</li><li>Biedt uitgebreide logboekregistratie</li><li>Inschakelen [automatische codecompilatie](../cli/code-compiler.md)</li><li>Maakt verbeterde foutopsporing mogelijk</li><li>Aangepaste tonen `X-Magento-*` HTTP-aanvraag- en antwoordheaders</li><li>Resultaten in de langzaamste prestaties</li><li>Hiermee worden fouten op de voorzijde weergegeven</li></ul> |
| productie | Bedoeld voor plaatsing op een productiesysteem, deze wijze:<ul><li>Geeft geen uitzonderingen aan de gebruiker (uitzonderingen worden alleen naar logboeken geschreven).</li><li>Serveert statische weergavebestanden alleen uit cache.</li><li>Voorkomt automatische compilatie van codebestanden. Nieuwe of bijgewerkte bestanden worden niet naar het bestandssysteem geschreven.</li><li>**Hiermee kunt u cachetypen in de beheerfunctie niet in- of uitschakelen.** Zie [de cache in- en uitschakelen](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Sommige gebieden, zoals de Geavanceerde en secties van de de systeemconfiguratie van de Ontwikkelaar in Admin, zijn niet beschikbaar op productiemodus.</li></ul> |
| onderhoud | Bedoeld om toegang tot een plaats te verhinderen terwijl het wordt bijgewerkt of opnieuw gevormd, deze wijze:<ul><li>Sitebezoekers omleiden naar de standaardmap `Service Temporarily Unavailable` pagina.</li><li>Als de onderhoudsmodus van de site is geactiveerd, `var/` bevat de map `.maintenance.flag` bestand.</li><li>U kunt onderhoudswijze vormen om bezoekerstoegang van een gespecificeerde lijst van IP adressen toe te staan.</li></ul> |

>[!INFO]
>
>[Adobe Commerce over cloudinfrastructuur](https://devdocs.magento.com/cloud/bk-cloud.html) ondersteunt alleen de productie- en onderhoudsmodi.

## Standaardmodus

Zoals zijn naam impliceert, is de standaardwijze hoe de Handel werkt als geen andere wijze wordt gespecificeerd. De standaardwijze laat u toe om de toepassing van de Handel op één enkele server op te stellen zonder enige montages te veranderen. De standaardmodus is echter niet zo geoptimaliseerd voor productie als de productiemodus.

Om de toepassing van de Handel op meer dan één server op te stellen of het voor productie te optimaliseren, verander in één van de andere wijzen.

In de standaardmodus:

- Fouten worden geregistreerd bij de bestandsrapporten op de server en worden nooit weergegeven bij een gebruiker
- Statische weergavebestanden worden in cache geplaatst
- De standaardmodus is niet geoptimaliseerd voor een productieomgeving, voornamelijk vanwege het negatieve effect op de prestaties van [statische bestanden](https://glossary.magento.com/static-files) dynamisch worden gegenereerd in plaats van tot stand te brengen. Met andere woorden, het maken van statische bestanden en het in cache plaatsen ervan heeft een groter effect op de prestaties dan het genereren ervan met het gereedschap voor het maken van statische bestanden.

Zie [De bewerkingsmodus instellen](../cli/set-mode.md).

## Modus Ontwikkelaar

Voer de toepassing van de Handel op ontwikkelaarwijze in werking wanneer u het uitbreidt of aanpast.

In de modus Ontwikkelaar:

- Statische weergavebestanden worden niet in cache geplaatst. zij worden naar de `pub/static` directory elke keer dat ze worden aangeroepen
- Niet-afgevangen uitzonderingen worden in de browser weergegeven
- Systeemaanmelding `var/report` is uitgebreid
- An [uitzondering](https://glossary.magento.com/exception) wordt gegenereerd in de fouthandler en niet vastgelegd
- Een uitzondering wordt gegenereerd wanneer een [event](https://glossary.magento.com/event) abonnee kan niet worden aangeroepen

Zie [De bewerkingsmodus instellen](../cli/set-mode.md).

## Productiemodus

De Handel van de looppas op productiemodus wanneer het aan een productieserver wordt opgesteld. Nadat u de serveromgeving, zoals de database en de webserver, hebt geoptimaliseerd, moet u de opdracht [hulpmiddel voor het implementeren van statische weergavebestanden](../cli/static-view-file-deployment.md) om statische weergavebestanden naar de `pub/static` directory.

Dit verbetert prestaties door alle noodzakelijke statische dossiers bij plaatsing te verstrekken in plaats van de Handel te dwingen om dynamisch van statische dossiers op bestelling tijdens runtime de plaats te bepalen en te kopiëren (materialiseren).

In de productiemodus:

- Statische weergavebestanden worden niet geconcretiseerd en URL&#39;s voor deze bestanden worden direct samengesteld. De statische meningsdossiers worden gediend van [cachegeheugen](https://glossary.magento.com/cache) alleen.
- Fouten worden bij het bestandssysteem geregistreerd en worden nooit aan de gebruiker weergegeven.
- U kunt cachetypen in- en uitschakelen _alleen_ met de [opdrachtregel](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- U _kan_ Schakel cachetypen in of uit met behulp van Admin.

## Onderhoudsmodus

Voer de toepassing Commerce in onderhoudsmodus uit om uw site offline te zetten terwijl u onderhouds-, upgrade- of configuratietaken uitvoert. In de onderhoudsmodus leidt de site de bezoekers om naar de standaardinstelling `Service Temporarily Unavailable` pagina.

U kunt een [aangepaste onderhoudspagina](../../upgrade/troubleshooting/maintenance-mode-options.md), laat manueel en maakt onderhoudswijze onbruikbaar, en vormt onderhoudswijze om bezoekers van erkende IP adressen toe te staan om de opslag normaal te bekijken. Zie [de onderhoudsmodus in- en uitschakelen](../../installation/tutorials/maintenance-mode.md).

Als u Handel op wolkeninfrastructuur gebruikt, loopt de toepassing van de Handel op onderhoudswijze tijdens de opstellen fase. Wanneer de plaatsing met succes voltooit, keert de toepassing van de Handel aan lopende op productiemodus terug. Zie [Implementatiehaken](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) in de _Commerce Cloud-hulplijn_.

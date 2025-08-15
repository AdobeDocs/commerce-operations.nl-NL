---
title: Aangepaste logboekregistratie
description: Leer hoe u fouten kunt onderzoeken met behulp van aangepaste logboekregistratie.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Overzicht van aangepaste logboekregistratie

Logs verstrekken zicht in systeemprocessen; bijvoorbeeld, het zuiveren informatie die u met begrip helpt wanneer een fout voorkwam of wat tot de fout leidt.

Dit onderwerp concentreert zich op dossier-gebaseerd registreren, hoewel Commerce de flexibiliteit verstrekt om logboeken in het gegevensbestand eveneens op te slaan.

Adobe raadt u aan om gecentraliseerde registratie van toepassingen te gebruiken om de volgende redenen:

- Hierdoor kunnen logbestanden worden opgeslagen op een andere server dan de toepassingsserver en worden I/O-bewerkingen op de schijf verminderd, waardoor de ondersteuning van de toepassingsserver wordt vereenvoudigd.

- Het maakt de verwerking van logboekgegevens effectiever door speciale hulpmiddelen-zulke als [ Logstash ], [ Logplex ], of [ fluentd ] te gebruiken - zonder effect aan een productieserver.

  >[!INFO]
  >
  >Adobe adviseert of onderschrijft geen bepaalde registrerenoplossing.

## Compatibiliteit met PSR-3

De [ norm PSR-3 ][laminas] bepaalt een gemeenschappelijke PHP interface voor registrerenbibliotheken. Het hoofddoel van PSR-3 is bibliotheken toe te staan om een `Psr\Log\LoggerInterface` voorwerp te ontvangen en logboeken aan het te schrijven op een eenvoudige en universele manier.

Hierdoor kan de implementatie gemakkelijk worden vervangen zonder dat er zorgen zijn dat deze vervanging de toepassingscode kan doorbreken. Het waarborgt ook een douanecomponent zal werken zelfs wanneer de logboekimplementatie in een toekomstige versie van het systeem wordt veranderd.

## Monolog

Commerce 2 voldoet aan de norm PSR-3. Door gebrek, gebruikt Commerce [ Monolog ]. Monolog is geïmplementeerd als een voorkeur voor `Psr\Log\LoggerInterface` in de Commerce-toepassing [`di.xml`][di] .

Monolog is een populaire PHP-logboekoplossing met een groot aantal handlers waarmee u geavanceerde logboekstrategieën kunt ontwikkelen. Hieronder volgt een overzicht van de werking van Monolog.

Een Logboek van de Monolog _registreerder_ is een kanaal dat zijn eigen reeks _managers_ heeft. Monolog bevat veel handlers, waaronder:

- Log naar bestanden en syslog
- Waarschuwingen en e-mails verzenden
- Logspecifieke servers en netwerklogboekregistratie
- Aanmelden bij ontwikkeling (integratie met FireBug en Chrome Logger, enz.)
- Log naar de database

Elke manager kan of het inputbericht verwerken en propagatie tegenhouden of de controle tot de volgende manager in een ketting overgaan.

Logberichten kunnen op verschillende manieren worden verwerkt. Bijvoorbeeld, kunt u alle zuivert informatie in een dossier op schijf opslaan, de berichten met hogere logboekniveaus in een gegevensbestand zetten, en tenslotte berichten met logboekniveau &quot;kritiek&quot;door e-mail verzenden.

Andere kanalen kunnen een verschillende reeks managers en logica hebben.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[vloeiend]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog

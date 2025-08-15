---
title: Oplossing voor gesplitste databaseprestaties
description: Lees over de gesplitste databaseoplossing voor Adobe Commerce.
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Overzicht van de gesplitste databaseoplossing

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce biedt verschillende schaalbaarheidsvoordelen, waaronder de mogelijkheid om drie aparte hoofddatabases te gebruiken voor verschillende functionele gebieden van de Commerce-toepassing.

De controle, de orden, en de productgegevens kunnen elk een afzonderlijk hoofdgegevensbestand gebruiken dat u naar keuze kunt herhalen. Afhankelijk van uw behoeften worden taken onafhankelijk van websitecontroles, activiteiten voor orderbeheer, surfen op websites en het winkelen geschaald. Deze veranderingen verstrekken aanzienlijke flexibiliteit in hoe de gegevensbestandrij kan worden geschraapt.

>[!INFO]
>
>Adobe Commerce op wolkeninfrastructuur steunt _niet_ deze eigenschap.

De `ResourceConnections` -klasse biedt de uniforme MySQL-databaseverbinding met de Commerce-toepassing. Voor vragen aan de hoofdgegevensbestanden, voeren wij het het gegevensbestandpatroon van de Segregatie van de Verantwoordelijkheid van de Vraag van het Bevel (CQRS) uit. Dit patroon behandelt de logica voor het verpletteren van gelezen en schrijft vragen aan de aangewezen gegevensbestanden. De ontwikkelaars te hoeven niet om te weten welke configuratie wordt gebruikt en er zijn geen afzonderlijke lees en schrijf gegevensbestandverbindingen.

Als u opstellings facultatieve gegevensbestandreplicatie, krijgt u de volgende voordelen:

- Gegevensback-up
- Gegevensanalyse zonder dat dit van invloed is op de hoofddatabase
- Schaalbaarheid

MySQL-databases worden asynchroon gerepliceerd. Dit betekent dat slaven niet permanent hoeven te zijn verbonden om updates van de master te ontvangen.

In de volgende afbeelding ziet u hoe deze functie werkt.

![ Adobe Commerce gebruikt verschillende gegevensbestanden om lijsten op te slaan ](../../assets/configuration/split-db-diagram-ee.png)

In Magento Open Source wordt slechts één hoofddatabase gebruikt.

Adobe Commerce gebruikt drie hoofddatabases en een configureerbaar aantal slave-databases voor replicatie. Adobe Commerce heeft één interface voor databaseverbindingen, wat resulteert in snellere prestaties en betere schaalbaarheid.

## Configuratieopties

Wegens de manier wordt de gespleten oplossing van de gegevensbestandprestaties ontworpen, kunnen uw douanecode en geïnstalleerde componenten _niet_ om het even welke volgend doen:

- Rechtstreeks naar de database schrijven (in plaats daarvan moet u de Adobe Commerce-databaseinterface gebruiken)
- JOINs van het gebruik die de verkoop of citaatgegevensbestanden beïnvloeden
- Gebruik externe sleutels aan lijsten in checkout, verkoop, of belangrijkste gegevensbestanden

>[!WARNING]
>
>De componentenontwikkelaars van het contact om te verifiëren of hun componenten om het even welk van het voorafgaande doen. In dat geval moet u slechts een van de volgende opties kiezen:
>
>- Vraag de componentontwikkelaars om hun componenten bij te werken.
>- Gebruik de componenten zoals-is _zonder_ de gespleten gegevensbestandoplossing.
>- Verwijder de componenten zodat kunt u de gesplitste gegevensbestandoplossing gebruiken.

Dit betekent ook dat u:

- Vorm de gespleten gegevensbestandoplossing _alvorens_ Commerce in productie te zetten.

  Adobe raadt aan zo snel mogelijk gesplitste databases te configureren nadat u de Commerce-software hebt geïnstalleerd.

- [ vormt manueel ](multi-master-manual.md) de gespleten gegevensbestandoplossing.

  U moet deze taak uitvoeren als u reeds componenten hebt geïnstalleerd of als Commerce reeds in productie is. (_werk_ geen productiesysteem bij; maak de updates in een ontwikkelingssysteem en synchroniseer de veranderingen nadat u hen hebt getest.)

  >[!WARNING]
  >
  >U moet de twee extra gegevensbestandinstanties manueel file. Commerce maakt alleen een back-up van de hoofddatabase-instantie. De opdrachten [`magento setup:backup --db`](../../installation/tutorials/backup.md) en Admin maken geen back-up van de extra tabellen.

## Vereisten

De gesplitste database vereist dat u drie MySQL-hoofddatabases instelt op elke host (alle drie op de Commerce-server, elke database op een aparte server enzovoort). Dit zijn de _hoofd_ gegevensbestanden en zij worden gebruikt als volgt:

- Eén hoofddatabase voor uitchecktabellen
- Één hoofdgegevensbestand voor verkooplijsten (ook bedoeld als _Systeem van Order Management_, of _OMS_, lijsten)
- Eén hoofddatabase voor de rest van de Commerce 2-toepassingstabellen

Bovendien kunt u naar keuze opstelling om het even welk aantal _slave_ gegevensbestanden die als ladingsverdelers en steunen dienen.

Deze gids bespreekt hoe te opstelling de hoofdgegevensbestanden slechts. Wij verstrekken steekproefconfiguraties en verwijzingen voor u aan opstellingsslave gegevensbestanden als u wenst.

In deze handleiding worden de drie hoofddatabases genoemd:

- `magento_quote`
- `magento_sales`
- `magento`

(U kunt uw databases een naam geven die u maar wilt.)

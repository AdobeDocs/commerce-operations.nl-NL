---
title: Oplossing voor gesplitste databaseprestaties
description: Lees over de gesplitste databaseoplossing voor Adobe Commerce en Magento Open Source.
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Overzicht van de gesplitste databaseoplossing

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce biedt verschillende schaalbaarheidsvoordelen, waaronder de mogelijkheid om drie aparte hoofddatabases te gebruiken voor verschillende functionele gebieden van de toepassing Commerce.

De controle, de orden, en de productgegevens kunnen elk een afzonderlijk hoofdgegevensbestand gebruiken dat u naar keuze kunt herhalen. Afhankelijk van uw behoeften worden taken onafhankelijk van websitecontroles, activiteiten voor orderbeheer, surfen op websites en het winkelen geschaald. Deze veranderingen verstrekken aanzienlijke flexibiliteit in hoe de gegevensbestandrij kan worden geschraapt.

>[!INFO]
>
>Adobe Commerce op cloud-infrastructuur doet _niet_ deze functie ondersteunen.

De `ResourceConnections` klasse verstrekt de verenigde MySQL gegevensbestandverbinding aan de toepassing van de Handel. Voor vragen aan de hoofdgegevensbestanden, voeren wij het het gegevensbestandpatroon van de Segregatie van de Verantwoordelijkheid van de Vraag van het Bevel (CQRS) uit. Dit patroon behandelt de logica voor het verpletteren van gelezen en schrijft vragen aan de aangewezen gegevensbestanden. De ontwikkelaars te hoeven niet om te weten welke configuratie wordt gebruikt en er zijn geen afzonderlijke lees en schrijf gegevensbestandverbindingen.

Als u opstellings facultatieve gegevensbestandreplicatie, krijgt u de volgende voordelen:

- Gegevensback-up
- Gegevensanalyse zonder dat dit van invloed is op de hoofddatabase
- Schaalbaarheid

MySQL-databases worden asynchroon gerepliceerd. Dit betekent dat slaven niet permanent hoeven te zijn verbonden om updates van de master te ontvangen.

In de volgende afbeelding ziet u hoe deze functie werkt.

![Adobe Commerce gebruikt verschillende databases om tabellen op te slaan](../../assets/configuration/split-db-diagram-ee.png)

In Magento Open Source wordt slechts één hoofddatabase gebruikt.

Adobe Commerce gebruikt drie hoofddatabases en een configureerbaar aantal slave-databases voor replicatie. Adobe Commerce heeft één interface voor databaseverbindingen, wat resulteert in snellere prestaties en betere schaalbaarheid.

## Configuratieopties

Vanwege de manier waarop de gesplitste oplossing voor databaseprestaties is ontworpen, zijn uw aangepaste code en geïnstalleerde componenten _kan_ Voer een van de volgende handelingen uit:

- Rechtstreeks naar de database schrijven (in plaats daarvan moet u de Adobe Commerce-databaseinterface gebruiken)
- JOINs van het gebruik die de verkoop of citaatgegevensbestanden beïnvloeden
- Gebruik externe sleutels aan lijsten in checkout, verkoop, of belangrijkste gegevensbestanden

>[!WARNING]
>
>De componentenontwikkelaars van het contact om te verifiëren of hun componenten om het even welk van het voorafgaande doen. In dat geval moet u slechts een van de volgende opties kiezen:
>
>- Vraag de componentontwikkelaars om hun componenten bij te werken.
>- De componenten ongewijzigd gebruiken _zonder_ de gesplitste databaseoplossing.
>- Verwijder de componenten zodat kunt u de gesplitste gegevensbestandoplossing gebruiken.

Dit betekent ook dat u:

- Vorm de gespleten gegevensbestandoplossing _voor_ de handel in productie te nemen.

  Adobe raadt aan om gesplitste databases zo snel mogelijk te configureren nadat u de Commerce-software hebt geïnstalleerd.

- [Handmatig configureren](multi-master-manual.md) de gesplitste databaseoplossing.

  U moet deze taak uitvoeren als u reeds componenten hebt geïnstalleerd of als de Handel reeds in productie is. (_Niet gebruiken_ een productiesysteem bijwerken, de updates uitvoeren in een ontwikkelingssysteem en de wijzigingen synchroniseren nadat u deze hebt getest.)

  >[!WARNING]
  >
  >U moet de twee extra gegevensbestandinstanties manueel file. De handel steunt slechts de belangrijkste gegevensbestandinstantie. De [`magento setup:backup --db`](../../installation/tutorials/backup.md) geen back-up maken van de extra tabellen.

## Vereisten

De gespleten gegevensbestand vereist u aan opstelling drie MySQL hoofdgegevensbestanden op om het even welke gastheer (alle drie op de server van de Handel, elk gegevensbestand op een afzonderlijke server, etc.). Dit zijn de _meester_ databanken en worden als volgt gebruikt:

- Eén hoofddatabase voor uitchecktabellen
- Eén hoofddatabase voor verkooptabellen (ook wel _Orderbeheersysteem_, of _OMS_, tabellen)
- Één hoofdgegevensbestand voor de rest van Commerce 2 toepassingslijsten

Bovendien kunt u optioneel een willekeurig aantal _slaven_ databases die fungeren als taakverdelingsmechanisme en back-ups.

Deze gids bespreekt hoe te opstelling de hoofdgegevensbestanden slechts. Wij verstrekken steekproefconfiguraties en verwijzingen voor u aan opstellingsslave gegevensbestanden als u wenst.

In deze handleiding worden de drie hoofddatabases genoemd:

- `magento_quote`
- `magento_sales`
- `magento`

(U kunt uw databases een naam geven die u maar wilt.)

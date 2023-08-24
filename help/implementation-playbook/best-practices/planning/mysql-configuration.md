---
title: Best practices voor MySQL-configuratie
description: Leer hoe MySQL triggers en slave verbindingen de plaatsprestaties van de Handel en hoe te om hen effectief te gebruiken beïnvloeden.
role: Developer
feature: Best Practices
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Best practices voor MySQL-configuratie

>[!NOTE]
>
>Dit onderwerp bevat industriestandaard softwaretermen die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen kwetsen, getraumatiseerd of onwelkom maken. Adobe werkt eraan deze termen te verwijderen uit code, documentatie en gebruikerservaring.

## Triggers

In dit artikel wordt uitgelegd hoe u prestatieproblemen kunt voorkomen bij het gebruik van MySQL-triggers. De trekkers worden gebruikt om veranderingen in controletabellen te registreren.

### Betrokken producten en versies

- Adobe Commerce ter plaatse
- Adobe Commerce over cloudinfrastructuur

>[!WARNING]
>
>Voor Adobe Commerce op wolkenprojecten, test altijd configuratieveranderingen in het Staging milieu alvorens de configuratie voor het milieu van de Productie te veranderen.

### Prestatieeffecten

Triggers worden geïnterpreteerd als code die betekent dat MySQL ze niet vooraf compileert.

Het houden van in de de transactieruimte van de vraag, de trekkers voegen overheadkosten aan een parser en een interpreter voor elke vraag toe die met de lijst wordt uitgevoerd. De trekkers delen de zelfde transactieruimte zoals de originele vragen, en terwijl die vragen voor sloten op de lijst concurreren, concurreren de trekkers onafhankelijk voor sloten op een andere lijst.

Deze extra overhead kan de siteprestaties op de site negatief beïnvloeden als er veel triggers worden gebruikt.

>[!WARNING]
>
>Adobe Commerce ondersteunt geen aangepaste triggers in de Adobe Commerce-database omdat aangepaste triggers incompatibiliteiten met toekomstige Adobe Commerce-versies kunnen introduceren. Voor beste praktijken, zie [Algemene MySQL-richtlijnen](../../../installation/prerequisites/database/mysql.md) in de documentatie van Adobe Commerce.

### Effectief gebruik

Volg deze richtlijnen om prestatieproblemen te voorkomen bij het gebruik van triggers:

- Als u douanetriggers hebt die sommige gegevens schrijven wanneer de trekker wordt uitgevoerd, beweeg deze logica om rechtstreeks aan de controletabellen in plaats daarvan te schrijven. Bijvoorbeeld, door een extra vraag in de toepassingscode toe te voegen, na de vraag u was bedoeld om de trekker voor tot stand te brengen.
- Bekijk bestaande aangepaste triggers en overweeg deze te verwijderen en rechtstreeks vanuit de toepassingszijde naar de tabellen te schrijven. Controleren op bestaande triggers in uw database met de opdracht [`SHOW TRIGGERS` SQL-instructie](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Voor extra hulp, vragen, of zorgen, [een Adobe Commerce-ondersteuningsticket verzenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Slave-verbindingen

Adobe Commerce kan meerdere databases asynchroon lezen. Als u een hoge lading voor het gegevensbestand MySQL van een plaats van de Handel verwacht die op de architectuur van de wolkeninfrastructuur Pro wordt opgesteld, adviseert de Adobe toelatend de slave MYSQL verbinding.

Wanneer u de MYSQL slave verbinding toelaat, gebruikt Adobe Commerce een read-only verbinding aan het gegevensbestand om read-only verkeer op een niet hoofdknoop te ontvangen. De prestaties verbeteren door lading het in evenwicht brengen wanneer slechts één knoop lees-schrijf verkeer behandelt.

### Betrokken versies

Adobe Commerce op cloudinfrastructuur, alleen Pro-architectuur

### Configuratie

In de Adobe Commerce op cloudinfrastructuur kunt u de standaardconfiguratie voor de MYSQL-slave-verbinding overschrijven door de instelling van de [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabele. Deze variabele instellen op `true` om automatisch een alleen-lezen verbinding met de database te gebruiken.

**De MySQL-slave-verbinding inschakelen**:

1. Wijzig op uw lokale werkstation de projectmap.

1. In de `.magento.env.yaml` bestand instellen `MYSQL_USE_SLAVE_CONNECTION` naar waar.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. De `.magento.env.yaml` bestand verandert en naar de externe omgeving duwen.

   Nadat de implementatie is voltooid, wordt de MySQL-slave-verbinding ingeschakeld voor de cloudomgeving.

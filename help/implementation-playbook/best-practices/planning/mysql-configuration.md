---
title: Best practices voor MySQL-configuratie
description: Leer hoe MySQL triggers and slave connections de siteprestaties van Commerce beïnvloeden en hoe u deze effectief kunt gebruiken.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
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
>Adobe Commerce ondersteunt geen aangepaste triggers in de Adobe Commerce-database omdat aangepaste triggers incompatibiliteiten met toekomstige Adobe Commerce-versies kunnen introduceren. Voor beste praktijken, zie [ Algemene Richtlijnen MySQL ](../../../installation/prerequisites/database/mysql.md) in de documentatie van Adobe Commerce.

### Effectief gebruik

Volg deze richtlijnen om prestatieproblemen te voorkomen bij het gebruik van triggers:

- Als u douanetriggers hebt die sommige gegevens schrijven wanneer de trekker wordt uitgevoerd, beweeg deze logica om rechtstreeks aan de controletabellen in plaats daarvan te schrijven. Bijvoorbeeld, door een extra vraag in de toepassingscode toe te voegen, na de vraag u was bedoeld om de trekker voor tot stand te brengen.
- Bekijk bestaande aangepaste triggers en overweeg deze te verwijderen en rechtstreeks vanuit de toepassingszijde naar de tabellen te schrijven. Controle voor bestaande trekkers in uw gegevensbestand door de [`SHOW TRIGGERS` SQL Verklaring ](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html) te gebruiken.
- Voor extra hulp, vragen, of zorgen, [ voorleggen een kaartje van de Steun van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Slave-verbindingen

Adobe Commerce kan meerdere databases asynchroon lezen. Als u een hoge belasting verwacht voor de MySQL-database van een Commerce-site die wordt geïmplementeerd op de Pro-architectuur van de cloudinfrastructuur, wordt u aangeraden de MYSQL-slave-verbinding in te schakelen.

Wanneer u de MYSQL slave verbinding toelaat, gebruikt Adobe Commerce een read-only verbinding aan het gegevensbestand om read-only verkeer op een niet hoofdknoop te ontvangen. De prestaties verbeteren door lading het in evenwicht brengen wanneer slechts één knoop lees-schrijf verkeer behandelt.

### Betrokken versies

Adobe Commerce op cloudinfrastructuur, alleen Pro-architectuur

### Configuratie

In Adobe Commerce op wolkeninfrastructuur, kunt u de standaardconfiguratie voor de MYSQL slave verbinding met voeten treden door [ MYSQL_USE_SLAVE_CONNECTION ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabele te plaatsen. Stel deze variabele in op `true` als u automatisch een alleen-lezen verbinding met de database wilt gebruiken.

**om de MySQL slave verbinding** toe te laten:

1. Wijzig op uw lokale werkstation de projectmap.

1. Stel in het bestand `.magento.env.yaml` de waarde `MYSQL_USE_SLAVE_CONNECTION` in op true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Leg de wijzigingen in het `.magento.env.yaml` -bestand vast en druk op de externe omgeving.

   Nadat de implementatie is voltooid, wordt de MySQL-slave-verbinding ingeschakeld voor de cloudomgeving.

---
title: Beste praktijken om de MySQL slave verbinding te vormen
description: Leer hoe u de MySQL-slave-verbinding configureert voor Adobe Commerce-sites die worden geïmplementeerd in de cloud-infrastructuur.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: a5a6e25e3fd303e07a07110b85aa1d460f53cd54
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Beste praktijken om de MySQL slave verbinding te vormen

>[!NOTE]
>
>We zijn ons ervan bewust dat dit artikel nog steeds industriestandaard softwaretermen bevat die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen doen voelen gekwetst, getraumatiseerd of onwelkom. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.

Voor Adobe Commerce-sites die zijn geïmplementeerd op de Pro-architectuur van de cloud, raadt Adobe aan de MYSQL-slave-verbinding standaard in te schakelen voor de database.

Adobe Commerce kan meerdere databases asynchroon lezen.  Wanneer u de MYSQL slave verbinding toelaat, gebruikt Adobe Commerce een read-only verbinding aan het gegevensbestand om read-only verkeer op een niet-master knoop te ontvangen. Dit verbetert prestaties door lading het in evenwicht brengen, omdat slechts één knoop read-write verkeer moet behandelen.

## Betrokken versies

Adobe Commerce op cloudinfrastructuur, Pro-architectuur

## MySQL-slave-verbinding configureren

De configuratie voor de MYSQL-slave-verbinding wordt ingesteld door de [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabele in de Adobe Commerce implementeren in het configuratiebestand van de cloud-infrastructuur; `.magento.env.yaml`. Deze variabele instellen op `true` om de verbinding in te schakelen.

De MySQL-slave-verbinding inschakelen:

1. Bewerk uw `.magento.env.yaml` bestand en controleer of `MYSQL_USE_SLAVE_CONNECTION` is ingeschakeld.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Leg alle wijzigingen vast en duw deze vervolgens naar de omgevingsvertakking om de update te implementeren.

   Nadat de implementatie met succes is voltooid, wordt de MySQL-slave-verbinding ingeschakeld in uw cloudinfrastructuur.

## Aanvullende informatie

- [Omgevingsvariabelen](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](database-on-cloud.md)

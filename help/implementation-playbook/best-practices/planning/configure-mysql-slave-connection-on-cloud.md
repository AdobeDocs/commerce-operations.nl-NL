---
title: Beste praktijken om de MySQL slave verbinding te vormen
description: Leer hoe u de MySQL-slave-verbinding configureert voor Adobe Commerce-sites die worden geïmplementeerd in de cloud-infrastructuur.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Beste praktijken om de MySQL slave verbinding te vormen

>[!NOTE]
>
>Dit artikel bevat industriestandaard softwaretermen die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen kwetsen, traumatiseren of onwelkom maken. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.

Voor Adobe Commerce-sites die zijn geïmplementeerd op de Pro-architectuur van de cloud, raadt Adobe aan de MYSQL-slave-verbinding standaard in te schakelen voor de database.

Adobe Commerce kan meerdere databases asynchroon lezen. Wanneer u de MYSQL slave verbinding toelaat, gebruikt Adobe Commerce een read-only verbinding aan het gegevensbestand om read-only verkeer op een niet-master knoop te ontvangen. De prestaties verbeteren door lading het in evenwicht brengen wanneer slechts één knoop lees-schrijf verkeer behandelt.

## Betrokken versies

Adobe Commerce op cloudinfrastructuur, Pro-architectuur

## MySQL-slave-verbinding configureren

In de Adobe Commerce op cloudinfrastructuur kunt u de standaardconfiguratie voor de MYSQL-slave-verbinding overschrijven door de instelling van de [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabele. Stel deze variabele in op true als u automatisch een alleen-lezen verbinding met de database wilt gebruiken.

**De MySQL-slave-verbinding inschakelen**:

1. Wijzig op uw lokale werkstation de projectmap.

1. In de `.magento.env.yaml` bestand instellen `MYSQL_USE_SLAVE_CONNECTION` naar waar.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. De `.magento.env.yaml` bestand verandert en naar de externe omgeving duwen.

   Nadat de implementatie met succes is voltooid, wordt de MySQL-slave-verbinding ingeschakeld voor de cloudomgeving.

Meer informatie over het aanpassen van de wolkenomgeving door uw bestaande Commerce-configuratie te overschrijven met [Omgevingsvariabelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) in de _Adobe Commerce on cloud Infrastructure Guide_.

## Aanvullende informatie

- [MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](database-on-cloud.md)

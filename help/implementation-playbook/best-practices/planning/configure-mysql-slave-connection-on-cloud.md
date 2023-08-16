---
title: Beste praktijken om de MySQL slave verbinding te vormen
description: Leer hoe u de MySQL-slave-verbinding configureert voor Adobe Commerce-sites die worden geïmplementeerd in de cloud-infrastructuur.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Beste praktijken om de MySQL slave verbinding te vormen

>[!NOTE]
>
>Dit artikel bevat industriestandaard softwaretermen die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen kwetsen, traumatiseren of onwelkom maken. Adobe werkt eraan deze termen te verwijderen uit code, documentatie en gebruikerservaring.

Adobe Commerce kan meerdere databases asynchroon lezen. Als u een hoge lading voor het gegevensbestand MySQL van een plaats van de Handel verwacht die op de architectuur van de wolkeninfrastructuur Pro wordt opgesteld, adviseert de Adobe toelatend de slave MYSQL verbinding.

Wanneer u de MYSQL slave verbinding toelaat, gebruikt Adobe Commerce een read-only verbinding aan het gegevensbestand om read-only verkeer op een niet hoofdknoop te ontvangen. De prestaties verbeteren door lading het in evenwicht brengen wanneer slechts één knoop lees-schrijf verkeer behandelt.

## Betrokken versies

Adobe Commerce op cloudinfrastructuur, alleen Pro-architectuur

## MySQL-slave-verbinding configureren

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

## Aanvullende informatie

Meer informatie over het aanpassen van de wolkenomgeving door uw bestaande Commerce-configuratie te overschrijven met [Omgevingsvariabelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) in de _Adobe Commerce on cloud Infrastructure Guide_.

Zie de [MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) artikel in het _Kennisbank voor ondersteuning_.

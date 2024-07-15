---
title: Voorwaarden voor installatie op locatie
description: Meer informatie over de softwareafhankelijkheden die vereist zijn voor installaties in Adobe Commerce op locatie.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# Voorwaarden voor installatie op locatie

Voordat u Adobe Commerce installeert, moet u het volgende doen:

* Opstelling één of meerdere gastheren die aan de [ systeemvereisten ](../system-requirements.md) voldoen.
* Als u opstelling meer dan één Webknoop met lading het in evenwicht brengen, opstelling en test dat deel van uw systeem _alvorens_ u de toepassing installeert.
* Zorg ervoor dat u op verschillende punten tijdens de installatie een back-up van het gehele systeem kunt maken, zodat u het systeem kunt terugdraaien als er problemen zijn.

>[!NOTE]
>
>Wij veronderstellen u de Adobe Commerce in a **ontwikkelomgeving** installeert, dat u de toegang van de wortelgebruiker tot de machine hebt, **en** dat de machine niet hoogst veilig moet zijn. Als u opstelling een veiliger machine bent, adviseren wij sterk u een netwerkbeheerder voor extra hulp raadplegen.

We raden u ten zeerste aan uw besturingssysteemsoftware bij te werken en bij te werken. Deze verbeteringen kunnen veiligheid en softwaremoeilijke situaties verstrekken die toekomstige problemen zouden kunnen verhinderen. Weet u niet wat dit betekent? Controle uit onze [ pagina van het installatieoverzicht ](../overview.md).

Voer de volgende opdrachten in als een gebruiker met `root` -rechten:

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## Vereiste controle

Voer de volgende opdrachten in om uw systeem op voorwaarden te controleren:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce ondersteunt Apache versie 2.4 zoals het volgende resultaat aangeeft:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Om Apache te installeren of te bevorderen, zie [ Apache ](web-server/apache.md).

### PHP

Zie [ systeemvereisten ](../system-requirements.md) voor gesteunde versies van PHP en [ PHP ](../system-requirements.md#php-settings) voor PHP vereisten.

### MySQL

Controleer of u een compatibele versie van MySQL hebt voor de versie van Adobe Commerce die u installeert. Zie {de vereisten van 0} Systeem ](../system-requirements.md) voor gesteunde versies.[

```bash
mysql -u <database root user or database owner name> -p
```

Bijvoorbeeld:

```bash
mysql -u magento -p
```

Het volgende resultaat geeft de versie aan die u uitvoert.

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Typ `help` of `\h` voor hulp. Typ `\c` om de huidige invoerinstructie te wissen.

Typ `exit` bij de `mysql>` -prompt om af te sluiten.

Om MySQL te installeren of te bevorderen, zie [ MySQL ](database/mysql.md).

### Zoekmachine

Om uw installatie van OpenSearch te verifiëren:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Om de installatie van uw Elasticsearch te verifiëren:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Bijvoorbeeld:

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```

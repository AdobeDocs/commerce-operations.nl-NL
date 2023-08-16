---
title: Voorwaarden voor installatie op locatie
description: Meer informatie over de softwareafhankelijkheden die vereist zijn voor installaties op locatie van Adobe Commerce en Magento Open Source.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# Voorwaarden voor installatie op locatie

Voordat u Adobe Commerce of Magento Open Source installeert, moet u het volgende doen:

* Stel een of meer hosts in die voldoen aan de [systeemvereisten](../system-requirements.md).
* Als u meerdere webknooppunten instelt met taakverdeling, stelt u dat deel van uw systeem in en test u dit _voor_ installeert u de toepassing.
* Zorg ervoor dat u op verschillende punten tijdens de installatie een back-up van het gehele systeem kunt maken, zodat u het systeem kunt terugdraaien als er problemen zijn.

>[!NOTE]
>
>We gaan ervan uit dat u de Adobe Commerce of Magento Open Source installeert in een **ontwikkelomgeving**, dat u toegang hebt tot de computer voor de basisgebruiker, **en** dat de machine niet zeer veilig hoeft te zijn. Als u opstelling een veiliger machine bent, adviseren wij sterk u een netwerkbeheerder voor extra hulp raadplegen.

We raden u ten zeerste aan uw besturingssysteemsoftware bij te werken en bij te werken. Deze verbeteringen kunnen veiligheid en softwaremoeilijke situaties verstrekken die toekomstige problemen zouden kunnen verhinderen. Weet u niet wat dit betekent? Bekijk onze [overzichtspagina voor installatie](../overview.md).

Voer de volgende opdrachten in als een gebruiker met `root` rechten:

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

Adobe Commerce en Magento Open Source ondersteunen Apache versie 2.4, zoals het volgende resultaat aangeeft:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Als u Apache wilt installeren of upgraden, raadpleegt u [Apache](web-server/apache.md).

### PHP

Zie [systeemvereisten](../system-requirements.md) voor ondersteunde versies van PHP en [PHP] voor PHP vereisten.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

Bijvoorbeeld:

```bash
mysql -u magento -p
```

Controleer of u de juiste versie van MySQL hebt voor de versie van Adobe Commerce of Magento Open Source die u installeert ([hier controleren op ondersteunde versies](../system-requirements.md). Het volgende resultaat geeft de versie aan die u uitvoert.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Type `help` of `\h` voor hulp. Type `\c` de huidige invoerinstructie wissen.

Enter `exit` bij de `mysql>` wordt gevraagd af te sluiten.

Ga voor het installeren of upgraden van MySQL naar [MySQL](database/mysql.md).

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

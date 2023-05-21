---
title: Voorwaarden voor zoekmachines
description: Voer de volgende stappen uit om ondersteunde software voor zoekprogramma's te installeren en te configureren voor installaties op locatie van Adobe Commerce en Magento Open Source.
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# Voorwaarden voor zoekmachines

Vanaf Adobe Commerce en Magento Open Source 2.4 moeten alle installaties zodanig zijn geconfigureerd dat ze worden gebruikt [Elasticsearch](https://www.elastic.co) of [OpenSearch](https://opensearch.org/) als zoekoplossing voor de catalogus.

>[!NOTE]
>
>Ondersteuning voor OpenSearch is toegevoegd in 2.4.4. OpenSearch is een compatibele vork van Elasticsearch. Alle instructies voor het configureren van Elasticsearch 7 zijn van toepassing op OpenSearch. [Migreren van Elasticsearch naar OpenSearch](../../../upgrade/prepare/opensearch-migration.md) biedt richtlijnen voor het schakelen naar OpenSearch.

## Ondersteunde versies

U moet Elasticsearch of OpenSearch installeren en configureren voordat u Adobe Commerce 2.4.4 en hoger installeert.

Zie de [Systeemvereisten](../../system-requirements.md) voor specifieke versiegegevens.

## Aanbevolen configuratie

We raden het volgende aan:

* [Nginx voor uw zoekmachine configureren](configure-nginx.md)
* [Apache configureren voor uw zoekmachine](configure-apache.md)

## Installatielocatie

De volgende taken veronderstellen dat u uw systeem volgens het volgende diagram hebt gevormd:

![Zoekmachineschema](../../../assets/installation/search-engine-config.svg)

Het voorgaande diagram toont:

* De toepassing van de Handel en de onderzoeksmotor zijn geïnstalleerd op verschillende gastheren.

   Als u op aparte hosts werkt, moet u de proxy opnieuw gebruiken. (Het groeperen van de onderzoeksmotor is voorbij het werkingsgebied van deze gids, maar u kunt meer informatie in vinden [Elasticsearch clustering-documentatie](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Elke host heeft een eigen webserver. de webservers hoeven niet hetzelfde te zijn .

   De toepassing Commerce kan bijvoorbeeld Apache uitvoeren en de zoekfunctie kan nginx uitvoeren.

* Beide Webservers gebruiken de Veiligheid van de Laag van het Vervoer (TLS).

   Het instellen van TLS valt buiten het bereik van onze documentatie.

Zoekverzoeken worden als volgt verwerkt:

1. Een onderzoeksverzoek van een gebruiker wordt ontvangen door de Webserver van de Handel, die het aan de server van de onderzoeksmotor door:sturen.

   U vormt de onderzoeksmotor om met de gastheer en de haven van de volmacht te verbinden. We raden de SSL-poort van de webserver aan (standaard ingesteld op 443).

1. De zoekmachine-webserver (die luistert op poort 443) vult de aanvraag aan bij de zoekmachine-server (standaard luistert deze naar poort 9200).

1. De toegang tot de onderzoeksmotor wordt verder beschermd door de Basisauthentificatie van HTTP. Een verzoek om de zoekmachine te bereiken, moet via SSL worden verzonden *en* Geef een geldige gebruikersnaam en wachtwoord op.

1. Het zoekprogramma verwerkt het verzoek.

1. De mededeling keert langs de zelfde route terug, met de Webserver die van Elasticsearch als veilige omgekeerde volmacht dienst doet.

## Vereisten

De in deze sectie besproken taken vereisen het volgende:

* [Firewall en SELinux](#firewall-and-selinux)
* [De JDK (Java Software Development Kit) installeren](#install-the-java-software-development-kit)
* [De zoekfunctie installeren](#install-the-search-engine)
* [Elasticsearch bijwerken](#upgrading-elasticsearch)

### Firewall en SELinux

Beveiligingsgerelateerde software (iptables, SELinux, AppArmor) kan standaard worden geconfigureerd om communicatie tussen subsystemen te blokkeren. Het is misschien een goed idee om deze te controleren als er problemen zijn.

#### Regels instellen voor iptables en SELinux

Raadpleeg de volgende bronnen als u regels wilt instellen voor communicatie met de firewall of SELinux ingeschakeld:

* [iptables how-to](https://help.ubuntu.com/community/IptablesHowTo)
* [Hoe te om iptables regels (fedora project) uit te geven](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Inleiding tot SELinux (CentOS.org)](https://www.centos.org)
* [SELinux How-To Wiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### De Java Software Development Kit installeren

Voer de volgende opdracht in om te bepalen of Java al is geïnstalleerd:

```bash
java -version
```

Indien het bericht `java: command not found` wordt weergegeven, moet u de Java SDK installeren zoals beschreven in de volgende sectie.

Zie een van de volgende secties:

* [De nieuwste JDK installeren op CentOS](#install-the-jdk-on-centos)
* [De nieuwste JDK installeren op Ubuntu](#install-the-jdk-on-ubuntu)

#### De JDK installeren op CentOS

Zie dit [Lesbestand digitale oceaan](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Zorg ervoor dat u de JDK installeert en *niet* de JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java versie 8 is mogelijk niet voor alle besturingssystemen beschikbaar. U kunt bijvoorbeeld [Zoek in de lijst met beschikbare pakketten naar Ubuntu](https://packages.ubuntu.com/).

#### De JDK installeren op Ubuntu

Als u JDK 1.8 op Ubuntu wilt installeren, voert u de volgende opdrachten in als een gebruiker met `root` rechten:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Voor andere opties raadpleegt u [Documentatie oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### De zoekfunctie installeren

Volg [Elasticsearch installeren](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) of [OpenSearch installeren en configureren](https://opensearch.org/docs/latest/opensearch/install/index/) voor uw platformspecifieke stappen.

Om te verifiëren dat Elasticsearch werkt, ga het volgende bevel op de server in waarop het loopt:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Er wordt een bericht weergegeven dat lijkt op het volgende:

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Voer de volgende opdrachten in om te controleren of OpenSearch werkt:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Elasticsearch bijwerken

Zie [Elasticsearch bijwerken](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies voor het maken van back-ups van uw gegevens, het opsporen van potentiële migratiekwesties en het testen van upgrades voordat u deze implementeert naar de productie. Afhankelijk van uw huidige versie van Elasticsearch, is het mogelijk dat een volledige clusterherstart al dan niet vereist is.

Elasticsearch vereist JDK 1.8 of hoger. Zie [De Java Software Development Kit installeren](#install-the-java-software-development-kit) om te controleren welke versie van JDK is geïnstalleerd.

## Aanvullende bronnen

Zie de [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) of [OpenSearch](https://opensearch.org/docs/latest/) documentatie.

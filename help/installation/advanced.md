---
title: Geavanceerde installatie op locatie
description: Leer meer over geavanceerde installatiescenario's voor Adobe Commerce of Magento Open Source over infrastructuur die u bezit.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2406'
ht-degree: 0%

---

# Geavanceerde installatie op locatie

>[!TIP]
>
>Verloren? Hebt u een helpende hand nodig? Probeer onze [Snelle start](composer.md) of [Contribute installeren](https://developer.adobe.com/commerce/contributor/guides/install/) hulplijnen.

>[!NOTE]
>
>Als u SELinux wilt inschakelen, raadpleegt u [SELinux en iptables](prerequisites/security.md).

## Command-lijn interface (CLI)

Adobe Commerce en Magento Open Source beschikken over één opdrachtregelinterface voor installatie- en configuratietaken: `<magento_root>/bin/magento`. De interface voert veelvoudige taken uit, die omvatten:

* Installatie (en verwante taken zoals het creëren of bijwerken van het gegevensbestandschema, het creëren van de plaatsingsconfiguratie).
* De cache wissen.
* Indexen beheren, inclusief opnieuw indexeren.
* Vertaal- en vertaalwoordenboeken maken.
* Het produceren van niet-bestaande klassen zoals fabrieken en interceptors voor stop-ins, die de configuratie van de gebiedsinjectie voor de objecten manager produceren.
* Statische weergavebestanden gebruiken.
* CSS maken van minder.

Overige uitkeringen:

* Eén opdracht (`<magento_root>/bin/magento list`) bevat een lijst met alle beschikbare installatie- en configuratieopdrachten.
* Consistente gebruikersinterface gebaseerd op Symfony.
* CLI is verlengbaar zodat kunnen de derdeontwikkelaars &quot;binnen&quot;aan het &quot;stoppen. Dit heeft het extra voordeel om de het leren kromme van gebruikers te elimineren.
* Opdrachten voor uitgeschakelde modules worden niet weergegeven.

Dit onderwerp bespreekt het installeren van de software van Adobe Commerce of van de Magento Open Source gebruikend CLI. Voor informatie over configuratie, zie [Configuratiegids](../configuration/overview.md).

Het installatieprogramma kan indien nodig meerdere keren worden uitgevoerd, zodat u:

* Verschillende waarden opgeven

  Nadat u bijvoorbeeld uw webserver hebt geconfigureerd voor SSL (Secure Sockets Layer), kunt u het installatieprogramma uitvoeren om SSL-opties in te stellen.

* Fouten in eerdere installaties corrigeren
* Adobe Commerce of Magento Open Source installeren in een andere database-instantie

## Voordat u de installatie start

Voer de volgende stappen uit voordat u begint:

* Controleer of uw systeem voldoet aan de vereisten die worden besproken in [systeemvereisten](system-requirements.md).

* Alles voltooien [voorwaarde](prerequisites/overview.md) taken.

* Voer de eerste installatiestappen uit. Zie [uw installatie- of upgradepad](overview.md).

* Nadat u zich bij de toepassingsserver hebt aangemeld, [schakelen naar de eigenaar van het bestandssysteem](prerequisites/file-system/overview.md).

* Controleer de [snel starten van installatie](composer.md) overzicht.

>[!NOTE]
>
>U moet Adobe Commerce of Magento Open Source installeren via de `bin` subdirectory.

U kunt het installatieprogramma meerdere keren uitvoeren met verschillende opties om installatietaken zoals de volgende uit te voeren:

* Installeren in fasen — Nadat u bijvoorbeeld uw webserver hebt geconfigureerd voor SSL (Secure Sockets Layer), kunt u het installatieprogramma opnieuw uitvoeren om SSL-opties in te stellen.

* Corrigeer fouten in eerdere installaties.

* Installeer Adobe Commerce of Magento Open Source in een andere database-instantie.

>[!NOTE]
>
>Standaard overschrijft het installatieprogramma de database niet als u de software in dezelfde database-instantie installeert. U kunt de optionele `cleanup-database` parameter om dit gedrag te wijzigen.

Zie ook [Bijwerken, opnieuw installeren, verwijderen](tutorials/uninstall.md).

### Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## Opdrachten voor Help bij de installateur

U kunt de volgende opdrachten uitvoeren om naar waarden voor bepaalde vereiste argumenten te zoeken:

| Installatieargument | Opdracht |
| ------------------ | ------------------------------- |
| Taal | bin/magento-info:language:list |
| Valuta | bin/magento-info:currency:list |
| Tijdzone | bin/magento-info:timezone:list |

>[!NOTE]
>
>Als er een fout wordt weergegeven wanneer u deze opdrachten uitvoert, controleert u of u de installatieafhankelijkheden hebt bijgewerkt zoals in [Installatieafhankelijkheden bijwerken](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installeren vanaf de opdrachtregel

Voor de installatieopdracht wordt de volgende indeling gebruikt:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

In de volgende tabellen worden de namen en waarden van de installatieopties beschreven. Zie bijvoorbeeld installatieopdrachten [Voorbeeld van localhost-installaties](#sample-localhost-installations).

>[!NOTE]
>
>Alle opties die spaties of speciale tekens bevatten, moeten tussen enkele of dubbele aanhalingstekens staan.

**Beheerdersreferenties:**

Met de volgende opties geeft u de gebruikersgegevens en gebruikersgegevens voor de Admin-gebruiker op.

U kunt de Admin-gebruiker tijdens of na de installatie maken. Als u de gebruiker tijdens de installatie creeert, zijn alle admin credentievariabelen vereist. Zie [Voorbeeld van localhost-installaties](#sample-localhost-installations).

De volgende tabellen bevatten veel, maar niet alle beschikbare installatieparameters. Voor een volledige lijst raadpleegt u de [Referentie voor opdrachtregelprogramma&#39;s](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--admin-firstname` | Voornaam van beheerder. | Ja |
| `--admin-lastname` | Achternaam van beheerder. | Ja |
| `--admin-email` | E-mailadres van de beheerder. | Ja |
| `--admin-user` | Gebruikersnaam beheerder. | Ja |
| `--admin-password` | Beheerderswachtwoord. Het wachtwoord moet ten minste 7 tekens lang zijn en ten minste één alfabetisch en numeriek teken bevatten. We raden een langer, complexer wachtwoord aan. Plaats de gehele wachtwoordtekenreeks tussen enkele aanhalingstekens. Bijvoorbeeld: `--admin-password='A0b9%t3g'` | Ja |

**Opties voor site- en databaseconfiguratie:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--base-url` | Baseer URL om tot uw Admin en opslag in om het even welke volgende formaten toegang te hebben:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Opmerking:** Het schema (http:// of https://) en een slash zijn beide vereist.<br><br>`<your install dir>` is het documentafhankelijke relatieve pad waarin de Adobe Commerce- of Magento Open Source-software moet worden geïnstalleerd. Afhankelijk van hoe u opstelling uw Webserver en virtuele gastheren, de weg magento2 zou kunnen zijn of het zou leeg kunnen zijn.<br><br>Als u toegang wilt tot Adobe Commerce of Magento Open Source op localhost, kunt u `http://127.0.0.1/<your install dir>/` of `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` die een basis-URL vertegenwoordigt die wordt gedefinieerd door een virtuele host-instelling of door een virtualisatieomgeving zoals Docker. Als u bijvoorbeeld een virtuele host instelt met de hostnaam `magento.example.com`, kunt u de software installeren met `--base-url={{base_url}}` en heb toegang tot Admin met een URL als `http://magento.example.com/admin`. | Ja |
| `--backend-frontname` | Uniform Resource Identifier (URI) voor toegang tot de beheerder. U kunt deze parameter weglaten zodat de toepassing een willekeurige URI met het volgende patroon kan genereren <code>admin_jkhgdfq</code>.<br><br>We raden een willekeurige URI aan voor beveiligingsdoeleinden. Willekeurige URI is moeilijker voor hakkers of kwaadwillige software om te exploiteren.<br><br>De URI wordt weergegeven aan het einde van de installatie. U kunt deze later op elk gewenst moment weergeven met de `bin/magento info:adminuri` gebruiken.<br><br>Als u ervoor kiest een waarde in te voeren, raden we u aan geen algemeen woord te gebruiken zoals admin, backend. De Admin URI kan alfanumerieke waarden en het onderstrepingsteken (`_`alleen ). | Nee |
| `--db-host` | Voer een van de volgende handelingen uit:<br><br>- De volledig gekwalificeerde hostname of IP van de databaseserver.<br><br>- `localhost` (standaardwaarde) of `127.0.0.1` als uw databaseserver zich op dezelfde host bevindt als uw webserver.localhost betekent, gebruikt de MySQL-clientbibliotheek UNIX-sockets om verbinding te maken met de database. `127.0.0.1` veroorzaakt de cliëntbibliotheek om het protocol van TCP te gebruiken. Raadpleeg voor meer informatie over sockets de [PHP-documentatie over BOB_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Opmerking:** U kunt desgewenst de poort van de databaseserver in de hostnaam opgeven, bijvoorbeeld www.example.com:9000 | Ja |
| `--db-name` | Naam van de database-instantie waarin u de databasetabellen wilt installeren.<br><br>Standaard is `magento2`. | Ja |
| `--db-user` | Gebruikersnaam van de eigenaar van de databaseinstantie.<br><br>Standaard is `root`. | Ja |
| `--db-password` | Het wachtwoord van de eigenaar van de databaseinstantie. | Ja |
| `--db-prefix` | Gebruik dit alleen als u de databasetabellen installeert in een database-instantie waarin al Adobe Commerce- of Magento Open Source-tabellen staan.<br><br>In dat geval gebruikt u een voorvoegsel om de tabellen voor deze installatie te identificeren. Sommige klanten hebben meer dan één Adobe Commerce- of Magento Open Source-instantie die op een server met alle tabellen in dezelfde database wordt uitgevoerd.<br><br>Het voorvoegsel mag maximaal vijf tekens lang zijn. De naam moet met een letter beginnen en mag alleen letters, cijfers en onderstrepingstekens bevatten.<br><br>Met deze optie kunnen deze klanten de databaseserver delen met meerdere Adobe Commerce- of Magento Open Source-installaties. | Nee |
| `--db-ssl-key` | Pad naar de clientsleutel. | Nee |
| `--db-ssl-cert` | Pad naar het clientcertificaat. | Nee |
| `--db-ssl-ca` | Pad naar het servercertificaat. | Nee |
| `--language` | Taalcode die moet worden gebruikt in Admin en storefront. (Als u dit nog niet hebt gedaan, kunt u de lijst met taalcodes weergeven door `bin/magento info:language:list` uit de map bin.) | Nee |
| `--currency` | Standaardvaluta voor gebruik in de winkel. (Als u dit nog niet hebt gedaan, kunt u de lijst met valuta&#39;s weergeven door `bin/magento info:currency:list` uit de map bin.) | Nee |
| `--timezone` | Standaardtijdzone die moet worden gebruikt in Admin en Storage. (Als u dit nog niet hebt gedaan, kunt u de lijst met tijdzones weergeven door `bin/magento info:timezone:list` van de `bin/` directory.) | Nee |
| `--use-rewrites` | `1` betekent dat u herschrijvingen van webservers gebruikt voor gegenereerde koppelingen in de winkel en in Admin.<br><br>`0` Hiermee schakelt u het gebruik van herschrijvingen van webservers uit. Dit is de standaardinstelling. | Nee |
| `--use-secure` | `1` laat het gebruik van de Veilige Laag van Contactdozen (SSL) in opslag URLs toe. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` schakelt het gebruik van SSL uit. In dit geval wordt aangenomen dat alle andere veilige URL-opties ook 0 zijn. Dit is de standaardinstelling. | Nee |
| `--base-url-secure` | Beveilig basis-URL voor toegang tot uw Admin en winkel in de volgende indeling: `http[s]://<host or ip>/<your install dir>/` | Nee |
| `--use-secure-admin` | `1` betekent dat u SSL gebruikt om toegang te krijgen tot Admin. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` betekent dat u geen SSL gebruikt met de Admin. Dit is de standaardinstelling. | Nee |
| `--admin-use-security-key` | 1 zorgt ervoor dat de toepassing een willekeurig gegenereerde sleutelwaarde gebruikt om toegang te krijgen tot pagina&#39;s in de Admin en in formulieren. Deze zeer belangrijke waarden helpen dwars-plaats manuscriptvervalsingsaanvallen verhinderen. Dit is de standaardinstelling.<br><br>`0` Hiermee schakelt u het gebruik van de toets uit. | Nee |
| `--session-save` | Voer een van de volgende handelingen uit:<br><br>- `db` om sessiegegevens in de database op te slaan. Kies gegevensbestandopslag als u een gegroepeerd gegevensbestand hebt; anders, zou er niet veel voordeel over op dossier-gebaseerde opslag kunnen zijn.<br><br>- `files` om sessiegegevens op te slaan in het bestandssysteem. De op dossier-gebaseerde zittingsopslag is aangewezen tenzij de toegang van het dossiersysteem langzaam is, hebt u een gegroepeerd gegevensbestand, of u wilt zittingsgegevens in Redis opslaan.<br><br>- `redis` om sessiegegevens op te slaan in Redis. Als u Redis gebruikt als standaardinstelling of als u pagina&#39;s in cache plaatst, moet Redis al zijn geïnstalleerd. Zie Redis gebruiken voor sessieopslag voor aanvullende informatie over het configureren van ondersteuning voor Redis. | Nee |
| `--key` | Als u er een hebt, geeft u een sleutel op om vertrouwelijke gegevens in de database te coderen. Als u er geen hebt, genereert de toepassing er een voor u. | Ja |
| `--cleanup-database` | Als u databasetabellen wilt neerzetten voordat u Adobe Commerce of Magento Open Source installeert, geeft u deze parameter zonder waarde op. Anders blijft de database intact. | Nee |
| `--db-init-statements` | Geavanceerde MySQL-configuratieparameter. Gebruikt de verklaringen van de gegevensbestandinitialisatie om te lopen wanneer het verbinden met het gegevensbestand MySQL. Raadpleeg een verwijzing die vergelijkbaar is met deze voordat u waarden instelt.<br><br>Standaard is `SET NAMES utf8;`. | Nee |
| `--sales-order-increment-prefix` | Geef een tekenreekswaarde op die als voorvoegsel voor verkooporders moet worden gebruikt. Dit wordt doorgaans gebruikt om unieke bestelnummers voor betalingsverwerkers te garanderen. | Nee |

**Opties voor de configuratie van zoekmachines:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--search-engine` | De versie van Elasticsearch of OpenSearch die als zoekmachine moet worden gebruikt. De standaardwaarde is `elasticsearch7`. Elasticsearch 5 is afgekeurd en wordt niet aanbevolen. | Nee |
| `--elasticsearch-host` | De gastheernaam of IP adres waar de Elasticsearch loopt. De standaardwaarde is `localhost`. | Nee |
| `--elasticsearch-port` | De poort van de Elasticsearch voor binnenkomende HTTP-aanvragen. De standaardwaarde is `9200`. | Nee |
| `--elasticsearch-index-prefix` | Een voorvoegsel dat de zoekindex van de Elasticsearch aangeeft. De standaardwaarde is `magento2`. | Nee |
| `--elasticsearch-timeout` | Het aantal seconden voordat het systeem uitvalt. De standaardwaarde is `15`. | Nee |
| `--elasticsearch-enable-auth` | Laat authentificatie op de server van de Elasticsearch toe. De standaardwaarde is `false`. | Nee |
| `--elasticsearch-username` | De gebruikers-id die moet worden geverifieerd bij de Elasticsearch-server. | Nee, tenzij verificatie is ingeschakeld |
| `--elasticsearch-password` | Het wachtwoord voor verificatie bij de Elasticzoekserver. | Nee, tenzij verificatie is ingeschakeld |
| `--opensearch-host` | De hostnaam of het IP-adres waar OpenSearch wordt uitgevoerd. De standaardwaarde is `localhost`. | Nee |
| `--opensearch-port` | De OpenSearch-poort voor binnenkomende HTTP-aanvragen. De standaardwaarde is `9200`. | Nee |
| `--opensearch-index-prefix` | Een voorvoegsel dat de zoekindex van OpenSearch aangeeft. De standaardwaarde is `magento2`. | Nee |
| `--opensearch-timeout` | Het aantal seconden voordat het systeem uitvalt. De standaardwaarde is `15`. | Nee |
| `--opensearch-enable-auth` | Hiermee wordt verificatie op de OpenSearch-server ingeschakeld. De standaardwaarde is `false`. | Nee |
| `--opensearch-username` | De gebruikersnaam die moet worden geverifieerd bij de OpenSearch-server. | Nee, tenzij verificatie is ingeschakeld |
| `--opensearch-password` | Het wachtwoord voor verificatie bij de OpenSearch-server. | Nee, tenzij verificatie is ingeschakeld |

**[!DNL RabbitMQ]configuratieopties:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--amqp-host` | Gebruik de `--amqp` tenzij u al een installatie van [!DNL RabbitMQ]. Zie [!DNL RabbitMQ] installatie voor meer informatie over installeren en configureren [!DNL RabbitMQ].<br><br>De hostnaam waarbij [!DNL RabbitMQ] is geïnstalleerd. | Nee |
| `--amqp-port` | De poort waarmee verbinding moet worden gemaakt [!DNL RabbitMQ]. De standaardwaarde is 5672. | Nee |
| `--amqp-user` | De gebruikersnaam waarmee verbinding wordt gemaakt [!DNL RabbitMQ]. De standaardgebruiker niet gebruiken `guest`. | Nee |
| `--amqp-password` | Het wachtwoord voor verbinding maken met [!DNL RabbitMQ]. Het standaardwachtwoord niet gebruiken `guest`. | Nee |
| `--amqp-virtualhost` | De virtuele host voor verbinding met [!DNL RabbitMQ]. De standaardwaarde is `/`. | Nee |
| `--amqp-ssl` | Geeft aan of verbinding moet worden gemaakt [!DNL RabbitMQ]. De standaardwaarde is `false`. Zie [!DNL RabbitMQ] voor informatie over het instellen van SSL voor [!DNL RabbitMQ]. | Nee |
| `--consumers-wait-for-messages` | Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee | Nee |

**Configuratieopties vergrendelen:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--lock-provider` | Naam provider vergrendelen.<br><br>Beschikbare vergrendelingsproviders: `db`, `zookeeper`, `file`.<br><br>De standaardvergrendelingsprovider: `db` | Nee |
| `--lock-db-prefix` | Het specifieke db voorvoegsel om vergrendelingsconflicten te voorkomen bij gebruik `db` vergrendelingsprovider.<br><br>De standaardwaarde: `NULL` | Nee |
| `--lock-zookeeper-host` | Host en poort voor verbinding met Zookeeper-cluster wanneer u `zookeeper` vergrendelingsprovider.<br><br>Bijvoorbeeld: `127.0.0.1:2181` | Ja, als u `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Het pad waar Zookeeper vergrendelingen opslaat.<br><br>Het standaardpad is: `/magento/locks` | Nee |
| `--lock-file-path` | Het pad waar de bestandsvergrendelingen worden opgeslagen. | Ja, als u `--lock-provider=file` |

**Configuratieopties van de consument:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Als u modules wilt in- of uitschakelen na de installatie van Adobe Commerce of Magento Open Source, raadpleegt u [Modules in- en uitschakelen](tutorials/manage-modules.md).

**Gevoelige gegevens:**

{{$include /help/_includes/sensitive-data.md}}

### Voorbeeld van localhost-installaties

In de volgende voorbeelden ziet u de opdrachten voor het lokaal installeren van Adobe Commerce met verschillende opties.

#### Voorbeeld 1—Basisinstallatie met beheergebruikersaccount

In het volgende voorbeeld wordt Adobe Commerce of Magento Open Source met de volgende opties geïnstalleerd:

* De toepassing wordt geïnstalleerd in het dialoogvenster `magento2` directory relatief ten opzichte van de webserverhoofdmap op `localhost` en het pad naar de beheerder is `admin`; derhalve

  De URL van je winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento`en de gebruikersnaam en het wachtwoord beide zijn `magento`

* Gebruikt herschrijvingen van server

* De beheerder heeft de volgende eigenschappen:

   * Voor- en achternamen zijn `Magento User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (V.S. Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* OpenSearch 1.2 is geïnstalleerd op `os-host.example.com` en maakt verbinding met poort 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Berichten die lijken op de volgende weergave om aan te geven dat de installatie is gelukt:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Voorbeeld 2— Basisinstallatie zonder beheergebruikersaccount

U kunt Adobe Commerce of Magento Open Source installeren zonder de beheerdersgebruiker te maken, zoals in het volgende voorbeeld wordt getoond.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Berichten zoals de volgende weergave als de installatie is gelukt:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Na de installatie kunt u een beheerder maken met de `admin:user:create` opdracht:
[Beheerders maken of bewerken](tutorials/admin.md#create-or-edit-an-administrator)

#### Voorbeeld 3—Installeren met extra opties

In het volgende voorbeeld wordt Adobe Commerce of Magento Open Source met de volgende opties geïnstalleerd:

* De toepassing wordt geïnstalleerd in het dialoogvenster `magento2` directory relatief ten opzichte van de webserverhoofdmap op `localhost` en het pad naar de beheerder is `admin`; derhalve

  De URL van je winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento`en de gebruikersnaam en het wachtwoord beide zijn `magento`

* De beheerder heeft de volgende eigenschappen:

   * Voor- en achternamen zijn `Magento User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (V.S. Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* Het installatieprogramma schoont eerst de database voordat de tabellen en het schema worden geïnstalleerd
* U kunt het voorvoegsel van de de verhogingsfactor van de verkooporde gebruiken `ORD$` (omdat het een speciaal teken bevat) [`$`], moet de waarde tussen dubbele aanhalingstekens staan)
* Sessiegegevens worden opgeslagen in de database
* Gebruikt herschrijvingen van server
* OpenSearch is geïnstalleerd op `os-host.example.com` en maakt verbinding met poort 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>U moet de opdracht invoeren op één regel of, zoals in het vorige voorbeeld, met een `\` aan het einde van elke regel.

Berichten zoals de volgende weergave als de installatie is gelukt:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

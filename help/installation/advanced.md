---
title: Geavanceerde installatie op locatie
description: Meer informatie over geavanceerde installatiescenario's voor Adobe Commerce-implementaties op locatie. Ontdek complexe configuraties en aangepaste instellingsopties.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: cb89f0c0a576cf6cd8b53a4ade12c21106e2cdf3
workflow-type: tm+mt
source-wordcount: '2485'
ht-degree: 0%

---

# Geavanceerde installatie op locatie

>[!TIP]
>
>Verloren? Hebt u een helpende hand nodig? Probeer onze [ Snelle begin installeert ](composer.md) of [ Medewerker ](https://developer.adobe.com/commerce/contributor/guides/install/) gidsen installeert.

>[!NOTE]
>
>Als u verkoos om SELinux toe te laten, zie [ SELinux en iptables ](prerequisites/security.md).

## Command-lijn interface (CLI)

Adobe Commerce heeft één opdrachtregelinterface voor installatie- en configuratietaken: `<magento_root>/bin/magento` . De interface voert veelvoudige taken uit, die omvatten:

* Installatie (en verwante taken zoals het creëren of bijwerken van het gegevensbestandschema, het creëren van de plaatsingsconfiguratie).
* De cache wissen.
* Indexen beheren, inclusief opnieuw indexeren.
* Vertaal- en vertaalwoordenboeken maken.
* Het produceren van niet-bestaande klassen zoals fabrieken en interceptors voor stop-ins, die de configuratie van de gebiedsinjectie voor de objecten manager produceren.
* Statische weergavebestanden gebruiken.
* CSS maken van minder.

Overige uitkeringen:

* Één enkel bevel (`<magento_root>/bin/magento list`) maakt een lijst van alle beschikbare installatie en configuratiebevelen.
* Consistente gebruikersinterface gebaseerd op Symfony.
* CLI is verlengbaar zodat kunnen de derdeontwikkelaars &quot;binnen&quot;aan het &quot;stoppen. Dit heeft het extra voordeel om de het leren kromme van gebruikers te elimineren.
* Opdrachten voor uitgeschakelde modules worden niet weergegeven.

Dit onderwerp bespreekt het installeren van de software van Adobe Commerce gebruikend CLI. Voor informatie over configuratie, zie de [ Gids van de Configuratie ](../configuration/overview.md).

Het installatieprogramma kan indien nodig meerdere keren worden uitgevoerd, zodat u:

* Verschillende waarden opgeven

  Nadat u bijvoorbeeld uw webserver hebt geconfigureerd voor SSL (Secure Sockets Layer), kunt u het installatieprogramma uitvoeren om SSL-opties in te stellen.

* Fouten in eerdere installaties corrigeren
* Adobe Commerce in een andere database-instantie installeren

## Voordat u de installatie start

Voer de volgende stappen uit voordat u begint:

* Verifieer dat uw systeem aan de vereisten voldoet die in [ worden besproken systeemvereisten ](system-requirements.md).

* Voltooi alle [ voorwaarde ](prerequisites/overview.md) taken.

* Voer de eerste installatiestappen uit. Zie [ uw installeer of verbeteringspad ](overview.md).

* Nadat u login aan de toepassingsserver, [ schakelaar aan de eigenaar van het dossiersysteem ](prerequisites/file-system/overview.md).

* Herzie het [ snel begin van de installatie ](composer.md) overzicht.

>[!NOTE]
>
>U moet Adobe Commerce installeren vanuit de submap `bin` .

U kunt het installatieprogramma meerdere keren uitvoeren met verschillende opties om installatietaken zoals de volgende uit te voeren:

* Installeren in fasen — Nadat u bijvoorbeeld uw webserver hebt geconfigureerd voor SSL (Secure Sockets Layer), kunt u het installatieprogramma opnieuw uitvoeren om SSL-opties in te stellen.

* Corrigeer fouten in eerdere installaties.

* Installeer Adobe Commerce in een andere database-instantie.

>[!NOTE]
>
>Standaard overschrijft het installatieprogramma de database niet als u de software in dezelfde database-instantie installeert. U kunt de optionele parameter `cleanup-database` gebruiken om dit gedrag te wijzigen.

Zie ook [ Update, herinstalleer, desinstalleer ](tutorials/uninstall.md).

### Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## Opdrachten voor Help bij de installateur

U kunt de volgende opdrachten uitvoeren om naar waarden voor bepaalde vereiste argumenten te zoeken:

| Installatieargument | Opdracht |
| ------------------ | ------------------------------- |
| Taal | `bin/magento info:language:list` |
| Valuta | `bin/magento info:currency:list` |
| Tijdzone | `bin/magento info:timezone:list` |

>[!NOTE]
>
>Als een foutenvertoningen wanneer u deze bevelen in werking stelt, verifieer dat u installatiegebiedsdelen zoals besproken in [ de installatiegebiedsdelen van de Update ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) bijwerkte.

## Installeren vanaf de opdrachtregel

Voor de installatieopdracht wordt de volgende indeling gebruikt:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

In de volgende tabellen worden de namen en waarden van de installatieopties beschreven. Bijvoorbeeld installatiebevelen, zie [ de installaties van de Steekproef localhost ](#sample-localhost-installations).

>[!NOTE]
>
>Alle opties die spaties of speciale tekens bevatten, moeten tussen enkele of dubbele aanhalingstekens staan.

**geloofsbrieven Admin:**

Met de volgende opties geeft u de gebruikersgegevens en gebruikersgegevens voor de Admin-gebruiker op.

U kunt de Admin-gebruiker tijdens of na de installatie maken. Als u de gebruiker tijdens de installatie creeert, zijn alle admin credentievariabelen vereist. Zie [ installaties van de Steekproef localhost ](#sample-localhost-installations).

De volgende tabellen bevatten veel, maar niet alle beschikbare installatieparameters. Voor een volledige lijst, zie de [ bevel-lijn Verwijzing van Hulpmiddelen ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises).

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--admin-firstname` | Voornaam van beheerder. | Ja |
| `--admin-lastname` | Achternaam van beheerder. | Ja |
| `--admin-email` | E-mailadres van de beheerder. | Ja |
| `--admin-user` | Gebruikersnaam beheerder. | Ja |
| `--admin-password` | Beheerderswachtwoord. Het wachtwoord moet ten minste 7 tekens lang zijn en ten minste één alfabetisch en numeriek teken bevatten. We raden een langer, complexer wachtwoord aan. Plaats de gehele wachtwoordtekenreeks tussen enkele aanhalingstekens. Bijvoorbeeld: `--admin-password='A0b9%t3g'` | Ja |

**de configuratieopties van de Plaats en van het gegevensbestand:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--base-url` | Basis URL aan gebruik om tot uw Admin en opslag in om het even welke volgende formaten toegang te hebben:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** de regeling (http:// of https://) en een het slepen schuine streep worden allebei vereist.<br><br>`<your install dir>` is het documentafhankelijke relatieve pad voor de installatie van de Adobe Commerce-software. Afhankelijk van hoe u opstelling uw Webserver en virtuele gastheren, de weg magento2 zou kunnen zijn of het zou leeg kunnen zijn.<br><br> om tot Adobe Commerce of tot MagenAdobe Commercieel toegang te hebben `http://127.0.0.1/<your install dir>/` of `http://127.0.0.1/<your install dir>/`.<br><br> - `{{base_url}}` die een basis-URL vertegenwoordigt die wordt gedefinieerd door een virtuele hostinstelling of door een virtualisatieomgeving zoals Docker. Als u bijvoorbeeld een virtuele host instelt met de hostnaam `magento.example.com` , kunt u de software installeren met `--base-url={{base_url}}` en toegang krijgen tot de beheerder met een URL zoals `http://magento.example.com/admin` . | Ja |
| `--backend-frontname` | Uniform Resource Identifier (URI) voor toegang tot de beheerder. U kunt deze parameter weglaten om de toepassing willekeurige URI voor u met het volgende patroon <code> te laten produceren admin_jkhgdfq</code>.<br><br> wij adviseren willekeurige URI voor veiligheidsdoeleinden. Willekeurige URI is moeilijker voor hakkers of kwaadwillige software om te exploiteren.<br><br> de vertoningen van URI aan het eind van de installatie. U kunt deze later op elk gewenst moment weergeven met de opdracht `bin/magento info:adminuri` .<br><br> als u verkiest om een waarde in te gaan, adviseren wij u geen gemeenschappelijk woord zoals admin, backend. De Admin-URI kan alleen alfanumerieke waarden en het onderstrepingsteken (`_`) bevatten. | Nee |
| `--db-host` | Gebruik om het even welk van het volgende:<br><br> - de volledig gekwalificeerde hostname van de gegevensbestandserver of IP adres.<br><br>- `localhost` (standaardwaarde) of `127.0.0.1` als uw databaseserver zich op dezelfde host bevindt als uw webserver.localhost betekent dat de MySQL-clientbibliotheek gebruikmaakt van UNIX-sockets om verbinding te maken met de database. `127.0.0.1` zorgt ervoor dat de clientbibliotheek het TCP-protocol gebruikt. Voor meer informatie over contactdozen, zie de [ PHP documentatie BOB_MYSQL ](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** U kunt naar keuze de haven van de gegevensbestandserver in zijn hostname als www.example.com specificeren :9000 | Ja |
| `--db-name` | Naam van de database-instantie waarin u de databasetabellen wilt installeren.<br><br> Standaard is `magento2`. | Ja |
| `--db-user` | Gebruikersnaam van de eigenaar van de databaseinstantie.<br><br> Standaard is `root`. | Ja |
| `--db-password` | Het wachtwoord van de eigenaar van de databaseinstantie. | Ja |
| `--db-prefix` | Gebruik het slechts als u de gegevensbestandlijsten in een gegevensbestandinstantie installeert die Adobe Commerce lijsten in het reeds heeft.<br><br> In dat geval, gebruik een prefix om de lijsten voor deze installatie te identificeren. Sommige klanten hebben meer dan één Adobe Commerce of MagenAdobe Commerceserver met alle tabellen in dezelfde database.<br><br> de prefix kan een maximum van vijf karakters in lengte zijn. De naam moet met een letter beginnen en mag alleen letters, cijfers en onderstrepingstekens bevatten.<br><br> Deze optie laat die klanten toe om de gegevensbestandserver met meer dan één installatie van Adobe Commerce te delen |
| `--db-ssl-key` | Pad naar de clientsleutel. | Nee |
| `--db-ssl-cert` | Pad naar het clientcertificaat. | Nee |
| `--db-ssl-ca` | Pad naar het servercertificaat. | Nee |
| `--language` | Taalcode die moet worden gebruikt in Admin en storefront. (Als u dit nog niet hebt gedaan, kunt u de lijst met taalcodes weergeven door `bin/magento info:language:list` in te voeren in de map bin.) | Nee |
| `--currency` | Standaardvaluta voor gebruik in de winkel. (Als u dit nog niet hebt gedaan, kunt u de lijst met valuta&#39;s weergeven door `bin/magento info:currency:list` in te voeren in de map bin.) | Nee |
| `--timezone` | Standaardtijdzone die moet worden gebruikt in Admin en Storage. (Als u dit nog niet hebt gedaan, kunt u de lijst met tijdzones weergeven door `bin/magento info:timezone:list` in te voeren in de map `bin/` .) | Nee |
| `--use-rewrites` | `1` betekent dat u herschrijvingen van webservers gebruikt voor gegenereerde koppelingen in de winkel en in Admin.<br><br>`0` schakelt het gebruik van herschrijven van webservers uit. Dit is de standaardinstelling. | Nee |
| `--use-secure` | `1` maakt het gebruik van SSL (Secure Sockets Layer) in winkel-URL&#39;s mogelijk. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` schakelt het gebruik van SSL uit. In dit geval wordt aangenomen dat alle andere veilige URL-opties ook 0 zijn. Dit is de standaardinstelling. | Nee |
| `--base-url-secure` | Beveilig basis-URL voor toegang tot uw beheerder en winkel in de volgende indeling: `http[s]://<host or ip>/<your install dir>/` | Nee |
| `--use-secure-admin` | `1` betekent dat u SSL gebruikt om toegang te krijgen tot Admin. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` betekent dat u geen SSL gebruikt met de Admin. Dit is de standaardinstelling. | Nee |
| `--admin-use-security-key` | 1 zorgt ervoor dat de toepassing een willekeurig gegenereerde sleutelwaarde gebruikt om toegang te krijgen tot pagina&#39;s in de Admin en in formulieren. Deze zeer belangrijke waarden helpen dwars-plaats manuscriptvervalsingsaanvallen verhinderen. Dit is de standaardinstelling.<br><br>`0` schakelt het gebruik van de toets uit. | Nee |
| `--session-save` | Gebruik om het even welke volgend:<br><br> - `db` om zittingsgegevens in het gegevensbestand op te slaan. Kies gegevensbestandopslag als u een gegroepeerd gegevensbestand hebt; anders, zou er niet veel voordeel over op dossier-gebaseerde opslag kunnen zijn.<br><br> - `files` om sessiegegevens op te slaan in het bestandssysteem. De op dossier-gebaseerde zittingsopslag is aangewezen tenzij de toegang van het dossiersysteem langzaam is, hebt u een gegroepeerd gegevensbestand, of u wilt zittingsgegevens in Redis opslaan.<br><br> - `redis` om sessiegegevens op te slaan in Redis. Als u Redis gebruikt als standaardinstelling of als u pagina&#39;s in cache plaatst, moet Redis al zijn geïnstalleerd. Zie Redis gebruiken voor sessieopslag voor aanvullende informatie over het configureren van ondersteuning voor Redis. | Nee |
| `--key` | Als u er een hebt, geeft u een sleutel op om vertrouwelijke gegevens in de database te coderen. Als u er geen hebt, genereert de toepassing er een voor u. | Ja |
| `--cleanup-database` | Als u databasetabellen wilt neerzetten voordat u Adobe Commerce installeert, geeft u deze parameter zonder waarde op. Anders blijft de database intact. | Nee |
| `--db-init-statements` | Geavanceerde MySQL-configuratieparameter. Gebruikt de verklaringen van de gegevensbestandinitialisatie om te lopen wanneer het verbinden met het gegevensbestand MySQL. Raadpleeg een verwijzing die vergelijkbaar is met deze voordat u waarden instelt.<br><br> Standaard is `SET NAMES utf8;`. | Nee |
| `--sales-order-increment-prefix` | Geef een tekenreekswaarde op die als voorvoegsel voor verkooporders moet worden gebruikt. Dit wordt doorgaans gebruikt om unieke bestelnummers voor betalingsverwerkers te garanderen. | Nee |

**de configuratieopties van de motor van het Onderzoek:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--search-engine` | De versie van Elasticsearch of OpenSearch die als zoekmachine moet worden gebruikt. De standaardwaarde is `elasticsearch7` . Elasticsearch 5 is afgekeurd en wordt niet aanbevolen. | Nee |
| `--elasticsearch-host` | De hostnaam of het IP-adres waarop Elasticsearch wordt uitgevoerd. De standaardwaarde is `localhost` . | Nee |
| `--elasticsearch-port` | De Elasticsearch-poort voor binnenkomende HTTP-aanvragen. De standaardwaarde is `9200` . | Nee |
| `--elasticsearch-index-prefix` | Een voorvoegsel dat de zoekindex van Elasticsearch aangeeft. De standaardwaarde is `magento2` . | Nee |
| `--elasticsearch-timeout` | Het aantal seconden voordat het systeem uitvalt. De standaardwaarde is `15` . | Nee |
| `--elasticsearch-enable-auth` | Hiermee wordt verificatie op de Elasticsearch-server ingeschakeld. De standaardwaarde is `false` . | Nee |
| `--elasticsearch-username` | De gebruikersnaam die moet worden geverifieerd bij de Elasticsearch-server. | Nee, tenzij verificatie is ingeschakeld |
| `--elasticsearch-password` | Het wachtwoord voor verificatie bij de Elasticzoekserver. | Nee, tenzij verificatie is ingeschakeld |
| `--opensearch-host` | De hostnaam of het IP-adres waar OpenSearch wordt uitgevoerd. De standaardwaarde is `localhost` . | Nee |
| `--opensearch-port` | De OpenSearch-poort voor binnenkomende HTTP-aanvragen. De standaardwaarde is `9200` . | Nee |
| `--opensearch-index-prefix` | Een voorvoegsel dat de zoekindex van OpenSearch aangeeft. De standaardwaarde is `magento2` . | Nee |
| `--opensearch-timeout` | Het aantal seconden voordat het systeem uitvalt. De standaardwaarde is `15` . | Nee |
| `--opensearch-enable-auth` | Hiermee wordt verificatie op de OpenSearch-server ingeschakeld. De standaardwaarde is `false` . | Nee |
| `--opensearch-username` | De gebruikersnaam die moet worden geverifieerd bij de OpenSearch-server. | Nee, tenzij verificatie is ingeschakeld |
| `--opensearch-password` | Het wachtwoord voor verificatie bij de OpenSearch-server. | Nee, tenzij verificatie is ingeschakeld |

**[!DNL RabbitMQ]configuratieopties:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--amqp-host` | Gebruik de opties voor `--amqp` alleen als u al een installatie van [!DNL RabbitMQ] hebt ingesteld. Zie [!DNL RabbitMQ] voor meer informatie over het installeren en configureren van [!DNL RabbitMQ] .<br><br> hostname waar [!DNL RabbitMQ] geïnstalleerd is. | Nee |
| `--amqp-port` | De poort die moet worden gebruikt om verbinding te maken met [!DNL RabbitMQ] . De standaardwaarde is 5672. | Nee |
| `--amqp-user` | De gebruikersnaam voor het verbinden met [!DNL RabbitMQ] . Gebruik de standaardgebruiker `guest` niet. | Nee |
| `--amqp-password` | Het wachtwoord voor het maken van verbinding met [!DNL RabbitMQ] . Gebruik het standaardwachtwoord niet `guest` . | Nee |
| `--amqp-virtualhost` | De virtuele host voor verbinding met [!DNL RabbitMQ]. De standaardwaarde is `/` . | Nee |
| `--amqp-ssl` | Geeft aan of verbinding moet worden gemaakt met [!DNL RabbitMQ] . De standaardwaarde is `false` . Zie [!DNL RabbitMQ] voor informatie over het instellen van SSL voor [!DNL RabbitMQ] . | Nee |
| `--consumers-wait-for-messages` | Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee | Nee |

**ActiveMQ de configuratieopties van Artemis:**

>[!NOTE]
>
>ActiveMQ Artemis is geïntroduceerd in Adobe Commerce 2.4.6 en latere versies.

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--stomp-host` | Gebruik de `--stomp` -opties alleen als u al een installatie van ActiveMQ-artemis hebt ingesteld. Zie de Artemis-installatie van ActiveMQ voor meer informatie over het installeren en configureren van ActiveMQ-artemis.<br><br> hostname waar de Artemis ActiveMQ geïnstalleerd is. | Nee |
| `--stomp-port` | De poort die moet worden gebruikt om verbinding te maken met ActiveMQ Artemis. De standaardwaarde is 61613. | Nee |
| `--stomp-user` | De gebruikersnaam voor het maken van verbinding met ActiveMQ Artemis. Gebruik de standaardgebruiker `artemis` niet. | Nee |
| `--stomp-password` | Het wachtwoord voor het maken van verbinding met ActiveMQ-artemis. Gebruik het standaardwachtwoord niet `artemis` . | Nee |
| `--stomp-ssl` | Geeft aan of verbinding moet worden gemaakt met ActiveMQ-artemis via SSL. De standaardwaarde is `false` . Zie de Artemis van ActiveMQ voor informatie over vestiging SSL voor Artemis ActiveMQ. | Nee |
| `--consumers-wait-for-messages` | Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee | Nee |

**de configuratieopties van het Slot:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--lock-provider` | Naam provider vergrendelen.<br><br> Beschikbare vergrendelingsproviders: `db`, `zookeeper`, `file` .<br><br> De standaardvergrendelingsprovider: `db` | Nee |
| `--lock-db-prefix` | Het specifieke voorvoegsel van de tab om vergrendelingsconflicten te voorkomen wanneer u `db` vergrendelingsprovider gebruikt.<br><br> De standaardwaarde: `NULL` | Nee |
| `--lock-zookeeper-host` | Gastheer en poort om verbinding te maken met de Zookeeper-cluster wanneer u `zookeeper` lock provider gebruikt.<br><br> Bijvoorbeeld: `127.0.0.1:2181` | Ja, als u `--lock-provider=zookeeper` instelt |
| `--lock-zookeeper-path` | Het pad waar Zookeeper vergrendelingen opslaat.<br><br> Het standaardpad is: `/magento/locks` | Nee |
| `--lock-file-path` | Het pad waar de bestandsvergrendelingen worden opgeslagen. | Ja, als u `--lock-provider=file` instelt |

**de configuratieopties van de Consumenten:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Om modules toe te laten of onbruikbaar te maken na het installeren van Adobe Commerce, zie [ modules ](tutorials/manage-modules.md) toelaten en onbruikbaar maken.

**Gevoelige gegevens:**

{{$include /help/_includes/sensitive-data.md}}

### Voorbeeld van localhost-installaties

In de volgende voorbeelden ziet u de opdrachten voor het lokaal installeren van Adobe Commerce met verschillende opties.

#### Voorbeeld 1—Basisinstallatie met beheergebruikersaccount

In het volgende voorbeeld wordt Adobe Commerce geïnstalleerd met de volgende opties:

* De toepassing wordt geïnstalleerd in de map `magento2` ten opzichte van de hoofdmap van de webserver op `localhost` en het pad naar de beheerdersmap is `admin` . Dit betekent dat:

  De URL van uw winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento` en de gebruikersnaam en het wachtwoord zijn beide `magento`

* Gebruikt herschrijvingen van server

* De beheerder heeft de volgende eigenschappen:

   * Voornaam en achternaam zijn `Magento User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (Amerikaans Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* OpenSearch 1.2 is geïnstalleerd op `os-host.example.com` en maakt verbinding op poort 9200

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

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Voorbeeld 2— Basisinstallatie zonder beheergebruikersaccount

U kunt Adobe Commerce installeren zonder de beheerdersgebruiker te maken, zoals in het volgende voorbeeld wordt getoond.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Berichten zoals de volgende weergave als de installatie is gelukt:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Na de installatie kunt u een beheerder maken met de opdracht `admin:user:create` :
[ creeer of geef een beheerder ](tutorials/admin.md#create-or-edit-an-administrator) uit

#### Voorbeeld 3—Installeren met extra opties

In het volgende voorbeeld wordt Adobe Commerce geïnstalleerd met de volgende opties:

* De toepassing wordt geïnstalleerd in de map `magento2` ten opzichte van de hoofdmap van de webserver op `localhost` en het pad naar de beheerdersmap is `admin` . Dit betekent dat:

  De URL van uw winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento` en de gebruikersnaam en het wachtwoord zijn beide `magento`

* De beheerder heeft de volgende eigenschappen:

   * Voornaam en achternaam zijn `Magento User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (Amerikaans Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* Het installatieprogramma schoont eerst de database voordat de tabellen en het schema worden geïnstalleerd
* U kunt het voorvoegsel voor de verhoging van de verkooporder gebruiken `ORD$` (omdat het een speciaal teken [`$`] bevat, moet de waarde tussen dubbele aanhalingstekens staan)
* Sessiegegevens worden opgeslagen in de database
* Gebruikt herschrijvingen van server
* OpenSearch is geïnstalleerd op `os-host.example.com` en maakt verbinding op poort 9200

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
>U moet de opdracht op één regel invoeren of, zoals in het vorige voorbeeld, met een `\` -teken aan het einde van elke regel.

Berichten zoals de volgende weergave als de installatie is gelukt:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Voorbeeld 4—Installeren met ActiveMQ-artemis

In het volgende voorbeeld wordt getoond hoe u Adobe Commerce met ActiveMQ-artemis als berichtbroker installeert:

```bash
bin/magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>Voor de installatie van ActiveMQ Artemis is Adobe Commerce 2.4.6 of hoger vereist.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->

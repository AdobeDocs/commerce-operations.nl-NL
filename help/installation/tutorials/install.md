---
title: Adobe Commerce installeren
description: Voer de volgende stappen uit om Adobe Commerce te installeren op uw eigen infrastructuur.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 47525e8d8379061b254bfa90ab46e27a1ee2f524
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# Adobe Commerce installeren

Voer de volgende stappen uit voordat u begint:

* Verifieer dat uw systeem aan de vereisten voldoet die in de [ systeemvereisten ](../system-requirements.md) worden besproken.

* Voltooi alle [ voorwaarde ](../prerequisites/overview.md) taken.

* Voer de eerste installatiestappen uit. Zie [ Uw installeer of verbeteringspad ](../overview.md).

* Nadat u login aan de toepassingsserver, [ schakelaar aan de eigenaar van het dossiersysteem ](../prerequisites/file-system/overview.md).

* Herzie [ begonnen worden met bevel-lijn installatie ](../composer.md) overzicht.

>[!NOTE]
>
>U moet de toepassing installeren vanuit de submap `bin` .

U kunt het installatieprogramma meerdere keren uitvoeren met verschillende opties om installatietaken zoals de volgende uit te voeren:

* Installeren in fasen—Nadat u bijvoorbeeld uw webserver hebt geconfigureerd voor SSL (Secure Sockets Layer), kunt u het installatieprogramma opnieuw uitvoeren om SSL-opties in te stellen.

* Corrigeer fouten in eerdere installaties.

* Installeer de toepassing in een andere database-instantie.

>[!NOTE]
>
>Standaard overschrijft het installatieprogramma de database niet als u de Commerce-software in dezelfde database-instantie installeert. U kunt de optionele parameter `cleanup-database` gebruiken om dit gedrag te wijzigen.

Zie ook [ Update, herinstalleer, desinstalleer ](uninstall.md).

## Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## Opdrachten voor Help bij de installateur

U kunt de volgende opdrachten uitvoeren om naar waarden voor bepaalde vereiste argumenten te zoeken:

| Installatieargument | Opdracht |
| ------------------ | ------------------------------- |
| Taal | `magento info:language:list` |
| Valuta | `magento info:currency:list` |
| Tijdzone | `magento info:timezone:list` |

>[!NOTE]
>
>Als een foutenvertoningen wanneer u deze bevelen in werking stelt, verifieer dat u installatiegebiedsdelen zoals besproken in [ de installatiegebiedsdelen van de Update ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) bijwerkte.

## Installeren vanaf de opdrachtregel

Voor de installatieopdracht wordt de volgende indeling gebruikt:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

In de volgende tabellen worden de namen en waarden van de installatieopties beschreven, zoals installatieopdrachten. Zie [ installaties van de Steekproef localhost ](#sample-localhost-installations).

>[!NOTE]
>
>Alle opties die spaties of speciale tekens bevatten, moeten tussen enkele of dubbele aanhalingstekens staan.

**geloofsbrieven Admin:**

Met de volgende opties geeft u de gebruikersgegevens en gebruikersgegevens voor de beheerder op.

In Adobe Commerce versie 2.2.8 en hoger kunt u tijdens of na de installatie de beheerder-gebruiker maken. Als u de gebruiker tijdens de installatie creeert, zijn alle admin credentievariabelen vereist. Zie [ installaties van de Steekproef localhost ](#sample-localhost-installations).

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
| `--base-url` | Basis URL aan gebruik om tot uw Admin en opslag in om het even welke volgende formaten toegang te hebben:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** de regeling (http:// of https://) en een het slepen schuine streep worden allebei vereist.<br><br>`<your install dir>` is het documentafhankelijke relatieve pad waarin de toepassing wordt geïnstalleerd. Afhankelijk van hoe u opstelling uw Webserver en virtuele gastheren, de weg magento2 zou kunnen zijn of het zou leeg kunnen zijn.<br><br> om tot de toepassing op localhost toegang te hebben, kunt u of `http://127.0.0.1/<your install dir>/` of `http://127.0.0.1/<your install dir>/` gebruiken.<br><br> - `{{base_url}}` die een basis-URL vertegenwoordigt die wordt gedefinieerd door een virtuele hostinstelling of door een virtualisatieomgeving zoals Docker. Als u bijvoorbeeld een virtuele host instelt met de hostnaam commerce.example.com, kunt u de toepassing installeren met `--base-url={{base_url}}` en toegang krijgen tot de beheerder met een URL zoals `http://commerce.example.com/admin` . | Ja |
| `--backend-frontname` | Uniform Resource Identifier (URI) voor toegang tot de beheerder. U kunt deze parameter weglaten om de toepassing willekeurige URI voor u met het volgende patroon <code> te laten produceren admin_jkhgdfq</code>.<br><br> wij adviseren willekeurige URI voor veiligheidsdoeleinden. Willekeurige URI is moeilijker voor hakkers of kwaadwillige software om te exploiteren.<br><br> de vertoningen van URI aan het eind van de installatie. U kunt deze later op elk gewenst moment weergeven met de opdracht `magento info:adminuri` .<br><br> als u verkiest om een waarde in te gaan, adviseren wij u geen gemeenschappelijk woord zoals admin, backend. De Admin-URI kan alleen alfanumerieke waarden en het onderstrepingsteken (`_`) bevatten. | Nee |
| `--db-host` | Gebruik om het even welk van het volgende:<br><br> - de volledig gekwalificeerde hostname van de gegevensbestandserver of IP adres.<br><br>- `localhost` (standaardwaarde) of `127.0.0.1` als uw databaseserver zich op dezelfde host bevindt als uw webserver.localhost betekent dat de MySQL-clientbibliotheek gebruikmaakt van UNIX-sockets om verbinding te maken met de database. `127.0.0.1` zorgt ervoor dat de clientbibliotheek het TCP-protocol gebruikt. Voor meer informatie over contactdozen, zie de [ PHP documentatie BOB_MYSQL ](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** U kunt naar keuze de haven van de gegevensbestandserver in zijn hostname als www.example.com specificeren :9000 | Ja |
| `--db-name` | Naam van de database-instantie waarin u de databasetabellen wilt installeren.<br><br> Standaard is `magento2`. | Ja |
| `--db-user` | Gebruikersnaam van de eigenaar van de databaseinstantie.<br><br> Standaard is `root`. | Ja |
| `--db-password` | Het wachtwoord van de eigenaar van de databaseinstantie. | Ja |
| `--db-prefix` | Gebruik het slechts als u de gegevensbestandlijsten in een gegevensbestandinstantie installeert die Adobe Commerce lijsten in het reeds heeft.<br><br> In dat geval, gebruik een prefix om de lijsten voor deze installatie te identificeren. Sommige klanten hebben meer dan één Adobe Commerce-instantie die op een server met alle tabellen in dezelfde database wordt uitgevoerd.<br><br> de prefix kan een maximum van vijf karakters in lengte zijn. De naam moet met een letter beginnen en mag alleen letters, cijfers en onderstrepingstekens bevatten.<br><br> Deze optie laat die klanten toe om de gegevensbestandserver met meer dan één installatie te delen. | Nee |
| `--db-ssl-key` | Pad naar de clientsleutel. | Nee |
| `--db-ssl-cert` | Pad naar het clientcertificaat. | Nee |
| `--db-ssl-ca` | Pad naar het servercertificaat. | Nee |
| `--language` | Taalcode die moet worden gebruikt in Admin en storefront. (Als u dit nog niet hebt gedaan, kunt u de lijst met taalcodes weergeven door `magento info:language:list` in te voeren in de map bin.) | Nee |
| `--currency` | Standaardvaluta voor gebruik in de winkel. (Als u dit nog niet hebt gedaan, kunt u de lijst met valuta&#39;s weergeven door `magento info:currency:list` in te voeren in de map bin.) | Nee |
| `--timezone` | Standaardtijdzone die moet worden gebruikt in Admin en Storage. (Als u dit nog niet hebt gedaan, kunt u de lijst met tijdzones weergeven door `magento info:timezone:list` in te voeren in de map bin.) | Nee |
| `--use-rewrites` | `1` betekent dat u herschrijvingen van webservers gebruikt voor gegenereerde koppelingen in de winkel en in Admin.<br><br>`0` schakelt het gebruik van herschrijven van webservers uit. Dit is de standaardinstelling. | Nee |
| `--use-secure` | `1` maakt het gebruik van SSL (Secure Sockets Layer) in winkel-URL&#39;s mogelijk. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` schakelt het gebruik van SSL uit. In dit geval wordt aangenomen dat alle andere veilige URL-opties ook 0 zijn. Dit is de standaardinstelling. | Nee |
| `--base-url-secure` | Beveilig basis-URL voor toegang tot uw beheerder en winkel in de volgende indeling: `http[s]://<host or ip>/<your install dir>/` | Nee |
| `--use-secure-admin` | `1` betekent dat u SSL gebruikt om toegang te krijgen tot Admin. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` betekent dat u geen SSL gebruikt met de Admin. Dit is de standaardinstelling. | Nee |
| `--admin-use-security-key` | 1 zorgt ervoor dat de toepassing een willekeurig gegenereerde sleutelwaarde gebruikt om toegang te krijgen tot pagina&#39;s in de Admin en in formulieren. Deze zeer belangrijke waarden helpen dwars-plaats manuscriptvervalsingsaanvallen verhinderen. Dit is de standaardinstelling.<br><br>`0` schakelt het gebruik van de toets uit. | Nee |
| `--session-save` | Gebruik om het even welke volgend:<br><br> - `db` om zittingsgegevens in het gegevensbestand op te slaan. Kies gegevensbestandopslag als u een gegroepeerd gegevensbestand hebt; anders, zou er niet veel voordeel over op dossier-gebaseerde opslag kunnen zijn.<br><br> - `files` om sessiegegevens op te slaan in het bestandssysteem. De op dossier-gebaseerde zittingsopslag is aangewezen tenzij de toegang van het dossiersysteem langzaam is, hebt u een gegroepeerd gegevensbestand, of u wilt zittingsgegevens in Redis opslaan.<br><br> - `redis` om sessiegegevens op te slaan in Redis. Als u Redis gebruikt als standaardinstelling of als u pagina&#39;s in cache plaatst, moet Redis al zijn geïnstalleerd. Zie Redis gebruiken voor sessieopslag voor aanvullende informatie over het configureren van ondersteuning voor Redis. | Nee |
| `--key` | Als u er een hebt, geeft u een sleutel op om vertrouwelijke gegevens in de database te coderen. Als u er geen hebt, genereert de toepassing er een voor u. | Ja |
| `--cleanup-database` | Als u databasetabellen wilt neerzetten voordat u de toepassing installeert, geeft u deze parameter zonder waarde op. Anders blijft de database intact. | Nee |
| `--db-init-statements` | Geavanceerde MySQL-configuratieparameter. Gebruikt de verklaringen van de gegevensbestandinitialisatie om te lopen wanneer het verbinden met het gegevensbestand MySQL. Raadpleeg een verwijzing die vergelijkbaar is met deze voordat u waarden instelt.<br><br> Standaard is `SET NAMES utf8;`. | Nee |
| `--sales-order-increment-prefix` | Geef een tekenreekswaarde op die als voorvoegsel voor verkooporders moet worden gebruikt. Dit wordt doorgaans gebruikt om unieke bestelnummers voor betalingsverwerkers te garanderen. | Nee |

>[!TIP]
>
>Om de verre opslagdiensten tijdens installatie toe te laten, zie [ Verre Opslag ](../../configuration/remote-storage/remote-storage.md) in de _Gids van de Configuratie_ vormen.

**de configuratieopties van de motor van het Onderzoek:**

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--search-engine` | De versie van het zoekprogramma. Mogelijke waarden zijn `elasticsearch7` , `elasticsearch6` en `elasticsearch5` . De standaardwaarde is `elasticsearch7` . Als u OpenSearch als zoekprogramma hebt geïnstalleerd, geeft u de waarde `elasticsearch7` op. Elasticsearch 5 is afgekeurd en wordt niet aanbevolen. | Nee |
| `--elasticsearch-host` | De hostnaam of het IP-adres waar de zoekmachine wordt uitgevoerd. De standaardwaarde is `localhost` . | Nee |
| `--elasticsearch-port` | De poort voor binnenkomende HTTP-aanvragen. De standaardwaarde is `9200` . | Nee |
| `--elasticsearch-index-prefix` | Een voorvoegsel dat de zoekindex aangeeft. De standaardwaarde is `magento2` . | Nee |
| `--elasticsearch-timeout` | Het aantal seconden voordat het systeem uitvalt. De standaardwaarde is `15` . | Nee |
| `--elasticsearch-enable-auth` | Hiermee wordt verificatie ingeschakeld op de zoekmachineserver. De standaardwaarde is `false` . | Nee |
| `--elasticsearch-username` | De gebruikersnaam die moet worden geverifieerd | Nee, tenzij verificatie is ingeschakeld |
| `--elasticsearch-password` | Het wachtwoord voor verificatie | Nee, tenzij verificatie is ingeschakeld |

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

**Verre opslagopties:**

| Naam | Beschrijving | Vereist? |
|--- |--- |--- |
| `remote-storage-driver` | De naam van de adapter <br> Mogelijke waarden:<br>**dossier**: Maakt verre opslag onbruikbaar en gebruikt het lokale filesystem <br>**aws-s3**: Gebruik de [ Eenvoudige Dienst van de Opslag van Amazon (Amazon S3) ](https://aws.amazon.com/s3/) | Nee |
| `remote-storage-bucket` | Objectopslag of containernaam | Nee |
| `remote-storage-prefix` | Optioneel voorvoegsel (locatie binnen opslag van object) | Nee |
| `remote-storage-region` | Naam regio | Nee |
| `remote-storage-key` | Optionele toegangstoets | Nee |
| `remote-storage-secret` | Optionele geheime sleutel | Nee |

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
>Om modules toe te laten of onbruikbaar te maken na het installeren van de toepassing, zie [ modules ](manage-modules.md) toelaten en onbruikbaar maken.

**Gevoelige gegevens:**

{{$include /help/_includes/sensitive-data.md}}

### Voorbeeld van localhost-installaties

In de volgende voorbeelden ziet u de opdrachten voor het lokaal installeren van Adobe Commerce met verschillende opties.

#### Voorbeeld 1—Basisinstallatie met beheergebruikersaccount

In het volgende voorbeeld wordt de toepassing met de volgende opties geïnstalleerd:

* De toepassing wordt geïnstalleerd in de map `magento2` ten opzichte van de hoofdmap van de webserver op `localhost` en het pad naar de beheerdersmap is `admin` . Dit betekent dat:

  De URL van uw winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento` en de gebruikersnaam en het wachtwoord zijn beide `magento`

* Gebruikt herschrijvingen van server

* De beheerder heeft de volgende eigenschappen:

   * Voornaam en achternaam zijn `Commerce User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (Amerikaans Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* Elasticsearch 7 is geïnstalleerd op `es-host.example.com` en maakt verbinding met poort 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Berichten die lijken op de volgende weergave om aan te geven dat de installatie is gelukt:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Voorbeeld 2—Basisinstallatie zonder beheergebruikersaccount

U kunt de toepassing installeren zonder de beheerdersgebruiker te creëren zoals in het volgende voorbeeld wordt getoond.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
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
[ creeer of geef een beheerder ](admin.md#create-or-edit-an-administrator) uit

#### Voorbeeld 3—Installeren met extra opties

In het volgende voorbeeld wordt de toepassing met de volgende opties geïnstalleerd:

* De Magapplication is geïnstalleerd in de map `magento2` ten opzichte van de hoofdmap van de webserver op `localhost` en het pad naar de beheerder is `admin` ; daarom:

  De URL van uw winkel is `http://127.0.0.1`

* De databaseserver bevindt zich op dezelfde host als de webserver.

  De databasenaam is `magento` en de gebruikersnaam en het wachtwoord zijn beide `magento`

* De beheerder heeft de volgende eigenschappen:

   * Voornaam en achternaam zijn `Commerce User`
   * Gebruikersnaam is `admin` en het wachtwoord is `admin123`
   * E-mailadres is `user@example.com`

* Standaardtaal is `en_US` (Amerikaans Engels)
* Standaardvaluta is Amerikaanse dollars
* Standaardtijdzone is VS Central (Amerika/Chicago)
* Het installatieprogramma schoont eerst de database voordat de tabellen en het schema worden geïnstalleerd
* U gebruikt een `ORD$` prefix voor de verhoging van de verkooporde (aangezien het een speciaal karakter [`$`] bevat, moet de waarde in dubbele citaten worden ingesloten)
* Sessiegegevens worden opgeslagen in de database
* Gebruikt herschrijvingen van server
* Elasticsearch 7 is geïnstalleerd op `es-host.example.com` en maakt verbinding met poort 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
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
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>Voor de installatie van ActiveMQ Artemis is Adobe Commerce 2.4.6 of hoger vereist.

>[!TIP]
>
>Als u één gebruikersrekening hebt om tot de toepassingsserver toegang te hebben, zie [ plaats een masker ](../next-steps/set-umask.md). Dit type installatie is standaard voor gedeelde hosting.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->

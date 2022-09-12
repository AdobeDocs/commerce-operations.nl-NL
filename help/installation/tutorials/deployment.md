---
title: Implementatieconfiguratie maken of bijwerken
description: Voer de volgende stappen uit om uw Adobe Commerce- of Magento Open Source-implementatieconfiguratie te beheren.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Implementatieconfiguratie maken of bijwerken

Er zijn geen voorwaarden om dit bevel te gebruiken.

## Implementatieconfiguratie maken of bijwerken

[Implementatieconfiguratie](../../configuration/reference/deployment-files.md) verstrekt de informatie die de toepassing moet initialiseren en laarzentrekker.

U kunt deze opdracht gebruiken als:

* U hebt de toepassing eerder geïnstalleerd en u wilt de configuratie van de implementatie wijzigen
* U wilt slechts de plaatsingsconfiguratie tot stand brengen en de installatie op één of andere andere manier voortzetten
* Om de plaatsingsconfiguratie bij te werken zonder iets anders te beïnvloeden

Opdrachtopties:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

In de volgende tabel worden de betekenis van installatieparameters en -waarden besproken.

| Parameter | Waarde | Vereist? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) om toegang te krijgen tot de beheerder.<br><br>Om misbruik te voorkomen, adviseren wij u geen gemeenschappelijk woord zoals admin, backend te gebruiken. De Admin URI kan alfanumerieke waarden en het onderstrepingsteken (`_`alleen ). | Nee |
| `--db-host` | Voer een van de volgende handelingen uit:<br><br>- De volledig gekwalificeerde hostnaam of IP-adres van de databaseserver.<br><br>- `localhost` (standaardwaarde) of `127.0.0.1` als uw databaseserver zich op dezelfde host bevindt als uw webserver. localhost betekent dat de MySQL-clientbibliotheek gebruikmaakt van UNIX-sockets om verbinding te maken met de database. `127.0.0.1` veroorzaakt de cliëntbibliotheek om het protocol van TCP te gebruiken. Raadpleeg voor meer informatie over sockets de [PHP-documentatie over BOB_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Opmerking:** U kunt optioneel de poort van de databaseserver in de hostnaam opgeven, zoals `www.example.com:9000` | Nee |
| `--db-name` | Naam van de database-instantie waarin u de databasetabellen wilt installeren.<br><br>Standaard is `magento2`. | Nee |
| `--db-user` | Gebruikersnaam van de eigenaar van de databaseinstantie.<br><br>Standaard is `root`. | Nee |
| `--db-password` | Het wachtwoord van de eigenaar van de databaseinstantie. | Nee |
| `--db-prefix` | Gebruik dit alleen als u de databasetabellen installeert in een database-instantie waarin al Adobe Commerce- en Magento Open Source-tabellen staan.<br><br>In dat geval gebruikt u een voorvoegsel om de tabellen voor deze installatie te identificeren. Sommige klanten hebben meer dan één Adobe Commerce- of Magento Open Source-instantie die op een server met alle tabellen in dezelfde database wordt uitgevoerd.<br><br>Het voorvoegsel mag maximaal vijf tekens lang zijn. De naam moet met een letter beginnen en mag alleen letters, cijfers en onderstrepingstekens bevatten.<br><br>Met deze optie kunnen deze klanten de databaseserver delen met meerdere Adobe Commerce- of Magento Open Source-installaties. | Nee |
| `--session-save` | Voer een van de volgende handelingen uit:<br><br>- `db` om sessiegegevens op te slaan in het dialoogvenster [database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Kies gegevensbestandopslag als u een gegroepeerd gegevensbestand hebt; anders, zou er niet veel voordeel over op dossier-gebaseerde opslag kunnen zijn.<br><br>- `files` om sessiegegevens op te slaan in het bestandssysteem. De op dossier-gebaseerde zittingsopslag is aangewezen tenzij de toegang van het dossiersysteem langzaam is, hebt u een gegroepeerd gegevensbestand, of u wilt zittingsgegevens in Redis opslaan.<br><br>- `redis` om sessiegegevens op te slaan in [Redis gebruiken voor sessieopslag](../../configuration/cache/config-redis.md). Als u Redis gebruikt als standaardinstelling of als u pagina&#39;s in cache plaatst, moet Redis al zijn geïnstalleerd. | Nee |
| `--key` | Als u er een hebt, geeft u een sleutel op die u wilt versleutelen [vertrouwelijke gegevens](#sensitive-data) in de database. Als u er geen hebt, genereert de toepassing er een voor u. | Nee |
| `--db-init-statements` | Geavanceerde MySQL-configuratieparameter. Gebruikt de verklaringen van de gegevensbestandinitialisatie om te lopen wanneer het verbinden met het gegevensbestand MySQL.<br><br>Standaard is `SET NAMES utf8;`.<br><br>Raadpleeg een verwijzing die vergelijkbaar is met [deze](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) voordat u waarden instelt. | Nee |
| `--http-cache-hosts` | Lijst met komma&#39;s als scheidingstekens van HTTP-cachegatewayhosts waarnaar purge-aanvragen moeten worden verzonden. (Bijvoorbeeld Varnish-servers.) Gebruik deze parameter om de host(s) op te geven die in dezelfde aanvraag moeten worden gewist. (Het maakt niet uit of u slechts één host of veel hosts hebt.)<br><br>Formaat moet `<hostname or ip>:<listen port>`, waar u kunt weglaten `<listen port>` als het poort 80 is. Bijvoorbeeld, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Plaats geen spatie tussen de hosts. | Nee |

## Configuratiegegevens importeren

Wanneer vestiging een productiesysteem, is het goede praktijk om configuratiemontages van in te voeren `config.php` en `env.php` in de database.
Deze instellingen zijn onder andere configuratiepaden en -waarden, websites, winkels, winkelweergaven en thema&#39;s.

Nadat u websites, winkels, weergaven en thema&#39;s hebt geïmporteerd, kunt u productkenmerken maken en deze toepassen op websites, winkels en winkelweergaven op het productiesysteem.

Voer in het productiesysteem de volgende opdracht uit om gegevens uit de configuratiebestanden te importeren (`config.php` en `env.php`) aan de database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

De optionele `[-n, --no-interaction]` De markering staat het bevel toe om zonder extra bevestigingen te lopen.

Voor meer informatie raadpleegt u de [Gegevens importeren uit configuratiebestanden](../../configuration/cli/import-configuration.md)

### Gevoelige gegevens

{{$include /help/_includes/sensitive-data.md}}

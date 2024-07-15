---
title: Implementatieconfiguratie maken of bijwerken
description: Voer de volgende stappen uit om uw Adobe Commerce-implementatieconfiguratie te beheren.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Implementatieconfiguratie maken of bijwerken

Er zijn geen voorwaarden om dit bevel te gebruiken.

## Implementatieconfiguratie maken of bijwerken

[ configuratie van de Plaatsing ](../../configuration/reference/deployment-files.md) verstrekt de informatie die de toepassing moet initialiseren en laarzentrekker.

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
| `--backend-frontname` | Uniform Herkenningsteken van het Middel ([ URI ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) om tot Admin toegang te hebben.<br><br> om exploits te verhinderen, adviseren wij u geen gemeenschappelijk woord zoals admin, backend te gebruiken. De Admin-URI kan alleen alfanumerieke waarden en het onderstrepingsteken (`_`) bevatten. | Nee |
| `--db-host` | Gebruik om het even welk van het volgende:<br><br> - de volledig gekwalificeerde hostname van de gegevensbestandserver of IP adres.<br><br> - `localhost` (standaardwaarde) of `127.0.0.1` als uw databaseserver zich op dezelfde host bevindt als uw webserver. localhost betekent dat de MySQL-clientbibliotheek gebruikmaakt van UNIX-sockets om verbinding te maken met de database. `127.0.0.1` zorgt ervoor dat de clientbibliotheek het TCP-protocol gebruikt. Voor meer informatie over contactdozen, zie de [ PHP documentatie BOB_MYSQL ](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** U kunt naar keuze de haven van de gegevensbestandserver in zijn hostname als `www.example.com:9000` specificeren | Nee |
| `--db-name` | Naam van de database-instantie waarin u de databasetabellen wilt installeren.<br><br> Standaard is `magento2`. | Nee |
| `--db-user` | Gebruikersnaam van de eigenaar van de databaseinstantie.<br><br> Standaard is `root`. | Nee |
| `--db-password` | Het wachtwoord van de eigenaar van de databaseinstantie. | Nee |
| `--db-prefix` | Gebruik het slechts als u de gegevensbestandlijsten in een gegevensbestandinstantie installeert die Adobe Commerce lijsten in het reeds heeft.<br><br> In dat geval, gebruik een prefix om de lijsten voor deze installatie te identificeren. Sommige klanten hebben meer dan één Adobe Commerce-instantie die op een server met alle tabellen in dezelfde database wordt uitgevoerd.<br><br> de prefix kan een maximum van vijf karakters in lengte zijn. De naam moet met een letter beginnen en mag alleen letters, cijfers en onderstrepingstekens bevatten.<br><br> Deze optie laat die klanten toe om de gegevensbestandserver met meer dan één installatie van Adobe Commerce te delen. | Nee |
| `--session-save` | Gebruik om het even welk van het volgende:<br><br> - `db` om zittingsgegevens in het [ gegevensbestand ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) op te slaan. Kies gegevensbestandopslag als u een gegroepeerd gegevensbestand hebt; anders, zou er niet veel voordeel over op dossier-gebaseerde opslag kunnen zijn.<br><br> - `files` om sessiegegevens op te slaan in het bestandssysteem. De op dossier-gebaseerde zittingsopslag is aangewezen tenzij de toegang van het dossiersysteem langzaam is, hebt u een gegroepeerd gegevensbestand, of u wilt zittingsgegevens in Redis opslaan.<br><br> - `redis` om zittingsgegevens in [ Redis van het Gebruik voor zittingsopslag ](../../configuration/cache/config-redis.md) op te slaan. Als u Redis gebruikt als standaardinstelling of als u pagina&#39;s in cache plaatst, moet Redis al zijn geïnstalleerd. | Nee |
| `--key` | Als u één hebt, specificeer een sleutel om [ gevoelige gegevens ](#sensitive-data) in het gegevensbestand te coderen. Als u er geen hebt, genereert de toepassing er een voor u. | Nee |
| `--db-init-statements` | Geavanceerde MySQL-configuratieparameter. Gebruikt de verklaringen van de gegevensbestandinitialisatie om te lopen wanneer het verbinden met het gegevensbestand MySQL.<br><br> Standaard is `SET NAMES utf8;`.<br><br> raadpleeg een verwijzing gelijkend op [ dit ](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) alvorens u om het even welke waarden plaatst. | Nee |
| `--http-cache-hosts` | Lijst met komma&#39;s als scheidingstekens van HTTP-cachegatewayhosts waarnaar purge-aanvragen moeten worden verzonden. (Bijvoorbeeld Varnish-servers.) Gebruik deze parameter om de host(s) op te geven die in dezelfde aanvraag moeten worden gewist. (Het maakt niet uit of u slechts één host of veel hosts hebt.)<br><br> Formaat moet `<hostname or ip>:<listen port>` zijn, waar u `<listen port>` kunt weglaten als het haven 80 is. Bijvoorbeeld `--http-cache-hosts=192.0.2.100,192.0.2.155:6081` . Plaats geen spatie tussen de hosts. | Nee |

## Configuratiegegevens importeren

Wanneer u een productiesysteem instelt, is het verstandig om configuratie-instellingen uit `config.php` en `env.php` te importeren in de database.
Deze instellingen zijn onder andere configuratiepaden en -waarden, websites, winkels, winkelweergaven en thema&#39;s.

Nadat u websites, winkels, weergaven en thema&#39;s hebt geïmporteerd, kunt u productkenmerken maken en deze toepassen op websites, winkels en winkelweergaven op het productiesysteem.

Voer in het productiesysteem de volgende opdracht uit om gegevens uit de configuratiebestanden (`config.php` en `env.php` ) te importeren naar de database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Met de optionele markering `[-n, --no-interaction]` kan de opdracht zonder aanvullende bevestigingen worden uitgevoerd.

Voor extra informatie, gelieve, de [ gegevens van de Invoer van configuratiedossiers ](../../configuration/cli/import-configuration.md) te controleren

### Gevoelige gegevens

{{$include /help/_includes/sensitive-data.md}}

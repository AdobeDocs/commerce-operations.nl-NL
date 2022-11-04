---
title: Snelle start van de installatie op locatie
description: Voer de volgende stappen uit om Adobe Commerce of Magento Open Source op uw eigen infrastructuur te installeren.
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---


# Snelle start van de installatie op locatie

We gebruiken [Composer](https://getcomposer.org/) om Adobe Commerce en Magento Open Source-componenten en hun afhankelijkheden te beheren. Composer gebruiken om de Adobe Commerce en de Magento Open Source op te halen [pakket](https://glossary.magento.com/metapackage) biedt de volgende voordelen:

- Bibliotheken van derden opnieuw gebruiken zonder deze te bundelen met broncode
- Verminder uitbreidingsconflicten en compatibiliteitskwesties door een op componenten-gebaseerde architectuur met robuust gebiedsbeheer te gebruiken
- Adhere to [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/) normen
- Magento Open Source opnieuw verpakken met andere componenten
- De Adobe Commerce- of Magento Open Source-software gebruiken in een productieomgeving

>[!NOTE]
>
>Ontwikkelaars die bijdragen aan Magento Open Source moeten de [op basis van git](https://developer.adobe.com/commerce/contributor/guides/install/) installatiemethode.

## Vereisten

Voordat u verdergaat, moet u het volgende doen:

- Alles voltooien [vereiste taken](system-requirements.md).
- [Composer installeren](https://getcomposer.org/download/).
- Get [verificatietoetsen](prerequisites/authentication-keys.md) naar de Adobe Commerce en de Magento Open Source Composer-opslagplaats.

## Aanmelden als eigenaar van bestandssysteem

Meer informatie over eigendom, machtigingen en de eigenaar van het bestandssysteem vindt u in onze [Overzicht van het onderwerp van eigendom en toestemmingen](prerequisites/file-system/overview.md).

Ga naar de eigenaar van het bestandssysteem:

1. Meld u aan bij de toepassingsserver of schakel over naar een gebruiker met schrijfmachtigingen naar het bestandssysteem.

   Als u bash shell gebruikt, kunt u de volgende syntaxis gebruiken om aan de eigenaar van het dossiersysteem over te schakelen en het bevel tezelfdertijd in te gaan:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Als de eigenaar van het bestandssysteem geen aanmeldingen toestaat, kunt u het volgende doen:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Om CLI bevelen van om het even welke folder in werking te stellen, voeg toe `<app_root>/bin` op uw systeem `PATH`.

   Omdat de syntaxis van schelpen verschilt, raadpleegt u een referentie zoals [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Voorbeeld van bash-shell voor CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   U kunt de opdrachten optioneel op de volgende manieren uitvoeren:

   - `cd <app_root>/bin` en uitvoeren als `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` is een submap van de webserverhoofdmap

## De metapakket ophalen

Zo krijgt u het metapakket Adobe Commerce of Magento Open Source:

1. Meld u aan bij de toepassingsserver als of schakel over naar de [eigenaar van bestandssysteem](prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de webserver of een map die u hebt geconfigureerd als een virtueel hoofddocument van de host.
1. Maak een Composer-project met het Adobe Commerce- of Magento Open Source-pakket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Voer desgevraagd uw verificatietoetsen in. De openbare en privé sleutels worden gecreeerd en in uw gevormd [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   Als u fouten tegenkomt, zoals `Could not find package...` of `...no matching package found`, zorg ervoor dat er geen typos in uw bevel zijn. Als er nog steeds fouten optreden, kunt u geen Adobe Commerce downloaden. Contact [Adobe Commerce-ondersteuning](https://support.magento.com/hc/en-us) voor hulp.

   Zie [Problemen oplossen](https://support.magento.com/hc/en-us/articles/360033818091) voor hulp bij meer fouten.

   >[!NOTE]
   >
   >Adobe Commerce-klanten hebben twee weken voor de datum van algemene beschikbaarheid (GA) toegang tot patches. Pakketten met pre-release zijn alleen beschikbaar via Composer. U kunt tot pre-versies op het Portaal van de Ontwikkelaar of GitHub tot GA niet toegang hebben. Neem contact op met Adobe Commerce Support als u deze pakketten niet kunt vinden in Composer.

### Voorbeeld - kleine release

Kleine versies bevatten nieuwe functies, oplossingen voor de kwaliteit en beveiligingsoplossingen. Gebruik Composer om een kleine release op te geven. U kunt bijvoorbeeld als volgt het metapakket Adobe Commerce 2.4.5 opgeven:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Voorbeeld - Kwaliteitspatch

Kwaliteitspatches bevatten voornamelijk functionele _en_ beveiligingsoplossingen. Soms kunnen ze echter ook nieuwe, achterwaartse compatibele functies bevatten. Gebruik Composer om een kwaliteitspatch te downloaden. U kunt bijvoorbeeld als volgt het metapakket Adobe Commerce 2.4.5 opgeven:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Voorbeeld - Beveiligingspatch

Beveiligingspatches bevatten alleen beveiligingsoplossingen. Ze zijn ontworpen om het upgradeproces sneller en eenvoudiger te maken.

Beveiligingspatches gebruiken de naamgevingsconventie van Composer `2.4.5-px`. Gebruik Composer om een patch op te geven. Als u bijvoorbeeld het pakket met Adobe Commerce 2.4.5-p1 wilt downloaden:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## Bestandsmachtigingen instellen

U moet lees-/schrijfmachtigingen instellen voor de webservergroep voordat u Adobe Commerce of Magento Open Source installeert. Dit is nodig, zodat de opdrachtregel bestanden naar het bestandssysteem kan schrijven.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## De toepassing installeren

U moet de opdrachtregel gebruiken om Adobe Commerce of Magento Open Source te installeren.

In dit voorbeeld wordt ervan uitgegaan dat de naam van de installatiemap is `magento2ee`de `db-host` bevindt zich op dezelfde computer (`localhost`en dat de `db-name`, `db-user`, en `db-password` alles `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=elasticsearch7 \
--elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 \
--elasticsearch-index-prefix=magento2 \
--elasticsearch-timeout=15
```

>[!TIP]
>
>U kunt de Admin URI aanpassen met de `--backend-frontname` optie. Nochtans, adviseren wij het weglaten van deze optie en het toestaan van het installatiebevel om een willekeurige URI automatisch te produceren. Willekeurige URI is moeilijker voor hakkers of kwaadwillige software om te exploiteren. De URI wordt in uw console weergegeven wanneer de installatie is voltooid.

>[!TIP]
>
>Voor een volledige beschrijving van de CLI-installatieopties raadpleegt u [De toepassing installeren vanaf de opdrachtregel](advanced.md).

## Overzicht van Command

Als u een volledige lijst met opdrachten wilt weergeven, voert u in:

```bash
bin/magento list
```

Om hulp voor een bepaald bevel te krijgen, ga binnen:

```bash
bin/magento help <command>
```

Bijvoorbeeld:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

De volgende tabel geeft een overzicht van de beschikbare opdrachten. Opdrachten worden alleen in een samenvatting weergegeven. Voor meer informatie over een bevel, klik de verbinding in de kolom van het Bevel.

| Opdracht | Beschrijving | Vereisten |
|--- |--- |--- |
| `magento setup:install` | De toepassing installeren | Geen |
| `magento setup:uninstall` | Verwijdert de toepassing. | Toepassing geïnstalleerd |
| `magento setup:upgrade` | Werkt de toepassing bij. | Implementatieconfiguratie |
| `magento maintenance:{enable/disable}` | Schakelt de onderhoudsmodus in of uit (in de onderhoudsmodus hebben alleen vrijgestelde IP-adressen toegang tot Admin of storefront). | Toepassing geïnstalleerd |
| `magento setup:config:set` | Creeert of werkt de plaatsingsconfiguratie bij. | Geen |
| `magento module:{enable/disable}` | Modules in- of uitschakelen. | Geen |
| `magento setup:store-config:set` | Hiermee stelt u aan de winkel gerelateerde opties in, zoals basis-URL, taal en tijdzone. | Implementatieconfiguratie |
| `magento setup:db-schema:upgrade` | Werkt het databaseschema bij. | Implementatieconfiguratie |
| `magento setup:db-data:upgrade` | Werkt de databasegegevens bij. | Implementatieconfiguratie |
| `magento setup:db:status` | Controleert of de database up-to-date is met de code. | Implementatieconfiguratie |
| `magento admin:user:create` | Maakt een beheerdersgebruiker. | U kunt gebruikers maken voor het volgende:<br><br>Implementatieconfiguratie<br><br>Schakel minimaal de optie `Magento_User` en `Magento_Authorization` modules<br><br>Database (eenvoudigste manier is om te gebruiken) `bin/magento setup:upgrade`) |
| `magento list` | Hiermee geeft u alle beschikbare opdrachten weer. | Geen |
| `magento help` | Biedt hulp voor de opgegeven opdracht. | Geen |

### Algemene argumenten

De volgende argumenten gelden voor alle opdrachten. Deze opdrachten kunnen worden uitgevoerd vóór of nadat de toepassing is geïnstalleerd:

| Lange versie | Korte versie | Betekenis |
|--- |--- |--- |
| `--help` | `-h` | Krijg hulp voor om het even welk bevel. Bijvoorbeeld: `./magento help setup:install` of `./magento help setup:config:set`. |
| `--quiet` | `-q` | stille modus; geen uitvoer. |
| `--no-interaction` | `-n` | Geen interactieve vragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbositeitsniveau. Bijvoorbeeld: `--verbose=3` of `-vvv` vertoningen zuiveren breedtegraad, die de breedste output is. Standaard is `--verbose=1` of `-v`. |
| `--version` | `-V` | Deze toepassingsversie weergeven |
| `--ansi` | n.v.t. | ANSI-uitvoer forceren |
| `--no-ansi` | n.v.t. | ANSI-uitvoer uitschakelen |

>[!NOTE]
>
>Gefeliciteerd! U hebt de snelle installatie voltooid. Hebt u meer geavanceerde hulp nodig? Bekijk onze [Geavanceerde installatie](advanced.md) hulplijn.

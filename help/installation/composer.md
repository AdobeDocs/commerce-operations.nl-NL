---
title: Snelle start van de installatie op locatie
description: Leer hoe u Adobe Commerce met Composer op uw eigen infrastructuur installeert. Ontdek de snelstartstappen en configuratievereisten.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Snelle start van de installatie op locatie

In de instructies op deze pagina wordt beschreven hoe u Adobe Commerce op zelfgehoste infrastructuur kunt installeren. Voor begeleiding bij de bevordering van een bestaande installatie, zie de [_Gids van de Verbetering_](../upgrade/overview.md).

Adobe gebruikt [&#x200B; Composer &#x200B;](https://getcomposer.org/) om de componenten van Adobe Commerce en hun gebiedsdelen te beheren. Het gebruik van Composer voor het ophalen van het Adobe Commerce-pakket biedt de volgende voordelen:

- Bibliotheken van derden opnieuw gebruiken zonder deze te bundelen met broncode
- Verminder uitbreidingsconflicten en compatibiliteitskwesties door een op componenten-gebaseerde architectuur met robuust gebiedsbeheer te gebruiken
- Adhere aan [&#x200B; PHP-Kader de Groep van de Interoperabiliteit (FIG) &#x200B;](https://www.php-fig.org/) normen
- Magento Open Source opnieuw verpakken met andere componenten
- De Adobe Commerce-software gebruiken in een productieomgeving

>[!NOTE]
>
>De ontwikkelaars die tot Magento Open Source bijdragen zouden de [&#x200B; op git-Gebaseerde &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/) installatiemethode moeten gebruiken.

## Vereisten

Voordat u verdergaat, moet u het volgende doen:

- Voltooi alle [&#x200B; in eerste instantie vereiste taken &#x200B;](system-requirements.md).
- [&#x200B; installeer Composer &#x200B;](https://getcomposer.org/download/).
- Krijg [&#x200B; authentificatietoetsen &#x200B;](prerequisites/authentication-keys.md) aan de bewaarplaats van de Composer van Adobe Commerce.

## Aanmelden als eigenaar van bestandssysteem

Leer over eigendom, toestemmingen, en de eigenaar van het dossiersysteem in het [&#x200B; Overzicht van eigendom en toestemmingenonderwerp &#x200B;](prerequisites/file-system/overview.md).

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

1. Als u CLI-opdrachten vanuit een willekeurige map wilt uitvoeren, voegt u `<app_root>/bin` toe aan uw systeem `PATH` .

   Omdat de cellen verschillende syntaxis hebben, raadpleeg een verwijzing als [&#x200B; unix.stackexchange.com &#x200B;](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Voorbeeld van bash-shell voor CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   U kunt de opdrachten optioneel op de volgende manieren uitvoeren:

   - `cd <app_root>/bin` en voer ze als `./magento <command name>` uit
   - `app_root>/bin/magento <command name>`
   - `<app_root>` is een submap van de webserverhoofdmap

## De metapakket ophalen

Zo krijgt u het Adobe Commerce-pakket:

1. Login aan uw toepassingsserver als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de webserver of een map die u hebt geconfigureerd als een virtueel hoofddocument van de host.
1. Maak een Composer-project met een Commerce-metapakket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Voer desgevraagd uw verificatietoetsen in. Openbare en privé sleutels worden gecreeerd en gevormd van [&#x200B; Commerce Marketplace - de Sleutels van de Toegang &#x200B;](https://commercemarketplace.adobe.com/customer/account/login/). Kopieer en plak voor de `[!UICONTROL username]` de waarde voor de openbare sleutel. Kopieer en plak voor de `[!UICONTROL password]` de waarde van de persoonlijke sleutel.

   >[!NOTE]
   >
   > Als u een Composer `[auth.json](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` -bestand of een omgevingsvariabele gebruikt die is geconfigureerd met de Commerce-verificatietoetsen, wordt u niet gevraagd verificatietoetsen in te voeren.

   Als er fouten optreden, zoals `Could not find package...` of `...no matching package found` , controleert u of de opdracht geen typos bevat. Als er nog steeds fouten optreden, kunt u geen Adobe Commerce downloaden. Contact {de Steun van 0} Adobe Commerce [&#x200B; voor hulp.](https://support.magento.com/hc/en-us)

   Zie [&#x200B; het Oplossen van problemen &#x200B;](https://support.magento.com/hc/en-us/articles/360033818091) voor hulp met meer fouten.

### Voorbeeld - kleine release

Kleine versies bevatten nieuwe functies, oplossingen voor de kwaliteit en beveiligingsoplossingen. Gebruik Composer om een kleine release op te geven. U kunt bijvoorbeeld als volgt het metapakket Adobe Commerce 2.4.6 opgeven:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Voorbeeld - Kwaliteitspatch

De flarden van de kwaliteit bevatten hoofdzakelijk functionele _en_ veiligheidsmoeilijke situaties. Soms kunnen ze echter ook nieuwe, achterwaartse compatibele functies bevatten. Gebruik Composer om een kwaliteitspatch te downloaden. U kunt bijvoorbeeld als volgt het metapakket Adobe Commerce 2.4.6 opgeven:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Voorbeeld - Beveiligingspatch

Beveiligingspatches bevatten alleen beveiligingsoplossingen. Ze zijn ontworpen om het upgradeproces sneller en eenvoudiger te maken.

Beveiligingspatches maken gebruik van de naamgevingsconventie van Composer `2.4.6-px` . Gebruik Composer om een patch op te geven. Als u bijvoorbeeld het pakket met Adobe Commerce 2.4.6-p1 wilt downloaden:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Bestandsmachtigingen instellen

U moet lees- en schrijfmachtigingen instellen voor de webservergroep voordat u Adobe Commerce installeert. Dit is nodig, zodat de opdrachtregel bestanden naar het bestandssysteem kan schrijven.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## De toepassing installeren

U moet de opdrachtregel gebruiken om Adobe Commerce te installeren.

In dit voorbeeld wordt ervan uitgegaan dat de installatiemap de naam `magento2ee` heeft, `db-host` zich op dezelfde computer bevindt (`localhost`) en `db-name` , `db-user` en `db-password` alle `magento` zijn:

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
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>U kunt de Admin URI aanpassen met de optie `--backend-frontname` . Adobe raadt echter aan deze optie weg te laten en de installatieopdracht toe te staan automatisch een willekeurige URI te genereren. Willekeurige URI is moeilijker voor hakkers of kwaadwillige software om te exploiteren. De URI wordt in uw console weergegeven wanneer de installatie is voltooid.

>[!TIP]
>
>Voor een volledige beschrijving van CLI installeert opties, zie [&#x200B; de toepassing van de bevellijn &#x200B;](advanced.md) installeren.

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
| `magento admin:user:create` | Maakt een beheerdersgebruiker. | U kunt gebruikers voor het volgende tot stand brengen:<br><br> de configuratie van de Plaatsing <br><br> laat minstens toe `Magento_User` en `Magento_Authorization` modules <br><br> Gegevensbestand (de eenvoudigste manier is `bin/magento setup:upgrade` te gebruiken) |
| `magento list` | Hiermee geeft u alle beschikbare opdrachten weer. | Geen |
| `magento help` | Biedt hulp voor de opgegeven opdracht. | Geen |

### Algemene argumenten

De volgende argumenten gelden voor alle opdrachten. Deze opdrachten kunnen worden uitgevoerd vóór of nadat de toepassing is geïnstalleerd:

| Lange versie | Korte versie | Betekenis |
|--- |--- |--- |
| `--help` | `-h` | Krijg hulp voor om het even welk bevel. Bijvoorbeeld `./magento help setup:install` of `./magento help setup:config:set` . |
| `--quiet` | `-q` | Stille modus; geen uitvoer. |
| `--no-interaction` | `-n` | Geen interactieve vragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbositeitsniveau. `--verbose=3` of `-vvv` geeft bijvoorbeeld een uitgebreide foutopsporing weer. Dit is de meest uitgebreide uitvoer. De standaardwaarde is `--verbose=1` of `-v` . |
| `--version` | `-V` | Deze toepassingsversie weergeven |
| `--ansi` | nvt | ANSI-uitvoer forceren |
| `--no-ansi` | nvt | ANSI-uitvoer uitschakelen |

>[!NOTE]
>
>Gefeliciteerd! U hebt de snelle installatie voltooid. Hebt u meer geavanceerde hulp nodig? Controle uit [&#x200B; Geavanceerde installeert &#x200B;](advanced.md) gids.

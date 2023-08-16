---
title: De waarde van bootstrap-parameters instellen
description: Leer hoe te om laarzentrekkerparameters voor de toepassing van de Handel te plaatsen.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# Parameters Bootstrap

Dit onderwerp toont aan hoe te om de waarden van de toepassings laarzentrekkerparameters van de Handel te plaatsen. Zie [Overzicht van initialisatie en bootstrapping van toepassingen](initialization.md).

De volgende lijst bespreekt de laarzentrekkerparameters die u kunt plaatsen:

| Bootstrap, parameter | Beschrijving |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Aangepaste map- en URL-paden opgeven |
| MAGE_PROFILER | Maakt afhankelijkheidsgrafieken en HTML-profilering mogelijk |

>[!INFO]
>
>- Niet alle laarzentrekkerparameters worden gedocumenteerd.
>- U stelt nu de toepassingsmodus (ontwikkelaar, standaard, productie) in met de opdracht [`magento deploy:mode:set {mode}`](../cli/set-mode.md) gebruiken.

## Parameters instellen met een omgevingsvariabele

In deze sectie wordt beschreven hoe u de waarden van bootstrap-parameters instelt met omgevingsvariabelen.

### De toepassingsmodus instellen

U kunt bootstrap-variabelen opgeven als systeembrede omgevingsvariabelen, zodat alle processen deze kunnen gebruiken.

U kunt bijvoorbeeld de opdracht `MAGE_PROFILER` systeemomgevingsvariabele om een modus als volgt op te geven:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Stel de variabele in met behulp van een shell-specifieke opdracht. Omdat de syntaxis van schelpen verschilt, raadpleegt u een referentie zoals [unix.stackexchange.com][unix-stackx].

Bash shell voorbeeld voor CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Indien een `PHP Fatal error` wordt weergegeven in de browser nadat u een profilerwaarde hebt ingesteld en de webserver opnieuw hebt gestart. De reden kan gerelateerd zijn aan het in cache plaatsen van PHP bytecode, waardoor bytecodes en PHP klassenpaden in cache worden geplaatst.

## Parameters instellen voor Apache of Nginx

In deze sectie wordt besproken hoe u de modus voor Apache of Nginx kunt opgeven.

### Nginx-instelling

Zie de [Nginx-voorbeeldconfiguratie] op _GitHub_.

### Instelling Apache.htaccess

U kunt de toepassingsmodus onder andere instellen door te bewerken `.htaccess`. Op deze manier hoeft u de Apache-instellingen niet te wijzigen.

U kunt `.htaccess` in om het even welke volgende plaatsen, afhankelijk van uw ingangspunt aan de toepassing van de Handel:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Een variabele instellen**:

1. Open de voorgaande bestanden in een teksteditor en voeg de gewenste instelling toe of verwijder de commentaarmarkering.

   Als u bijvoorbeeld een [mode](application-modes.md)Verwijder de commentaarmarkering uit:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Stel de waarde in van `MAGE_PROFILER` op een van de volgende wijzen:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Sla uw wijzigingen op in `.htaccess`; u hoeft Apache niet opnieuw te starten om de wijziging van kracht te laten worden.

### Apache-instelling

De Apache-webserver ondersteunt het instellen van de toepassingsmodus met `mod_env` richtlijnen.

De Apache `mod_env` richtlijn verschilt enigszins in [Apache versie 2.2] en [Apache versie 2.4].

De volgende procedures tonen hoe u de toepassingsmodus instelt in een virtuele Apache-host. Dit is niet de enige manier om te gebruiken `mod_env` richtlijnen; raadpleeg de documentatie van Apache voor meer informatie.

>[!TIP]
>
>In de volgende sectie wordt ervan uitgegaan dat u uw virtuele host al hebt ingesteld. Als u dat niet hebt gedaan, raadpleegt u een bron zoals [deze DigitalOcean-zelfstudie](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Een bootstrap-variabele opgeven voor Apache op Ubuntu**:

1. Als gebruiker met `root` voorrechten, open uw virtueel dossier van de gastheerconfiguratie in een tekstredacteur.

   Als uw virtuele host bijvoorbeeld een naam heeft `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. Voeg overal in de virtuele gastheerconfiguratie de volgende lijn toe:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Bijvoorbeeld:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.
1. Schakel uw virtuele host in als u dat nog niet hebt gedaan:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Bijvoorbeeld:

   ```bash
   a2ensite my.magento.conf
   ```

1. Nadat u de modus hebt ingesteld, start u de webserver opnieuw:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>In deze sectie wordt ervan uitgegaan dat u al een virtuele host hebt ingesteld. Als u dat niet hebt gedaan, raadpleegt u een bron zoals [deze DigitalOcean-zelfstudie](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Een bootstrap-variabele opgeven voor Apache op CentOS**:

1. Als gebruiker met `root` rechten, openen `/etc/httpd/conf/httpd.conf` in een teksteditor.

1. Voeg overal in de virtuele gastheerconfiguratie de volgende lijn toe:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Bijvoorbeeld:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.

1. Nadat u de modus hebt ingesteld, start u de webserver opnieuw:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versie 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versie 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx-voorbeeldconfiguratie]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables

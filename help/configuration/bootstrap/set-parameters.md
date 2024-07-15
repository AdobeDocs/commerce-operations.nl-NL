---
title: De waarde van bootstrap-parameters instellen
description: Leer hoe u opstartparameters instelt voor de Commerce-toepassing.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Parameters Bootstrap

Dit onderwerp toont aan hoe te om de waarden van de parameters van de toepassingslaarzentrekker van Commerce te plaatsen. Zie [ Overzicht van toepassingsinitialisatie en bootstrapping ](initialization.md).

De volgende lijst bespreekt de laarzentrekkerparameters die u kunt plaatsen:

| Bootstrap, parameter | Beschrijving |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Aangepaste map- en URL-paden opgeven |
| MAGE_PROFILER | Maakt afhankelijkheidsgrafieken en HTML-profilering mogelijk |

>[!INFO]
>
>- Niet alle laarzentrekkerparameters worden gedocumenteerd.
>- U kunt nu de toepassingsmodus (ontwikkelaar, standaard, productie) instellen met de opdracht [`magento deploy:mode:set {mode}`](../cli/set-mode.md) .

## Parameters instellen met een omgevingsvariabele

In deze sectie wordt beschreven hoe u de waarden van bootstrap-parameters instelt met omgevingsvariabelen.

### De toepassingsmodus instellen

U kunt bootstrap-variabelen opgeven als systeembrede omgevingsvariabelen, zodat alle processen deze kunnen gebruiken.

U kunt bijvoorbeeld de systeemomgevingsvariabele `MAGE_PROFILER` als volgt gebruiken om een modus op te geven:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Stel de variabele in met behulp van een shell-specifieke opdracht. Omdat de cellen verschillende syntaxis hebben, raadpleeg een verwijzing als [ unix.stackexchange.com ][unix-stackx].

Bash shell voorbeeld voor CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Als een `PHP Fatal error` in de browser wordt weergegeven nadat u een waarde voor de analyse hebt ingesteld, start u de webserver opnieuw. De reden kan gerelateerd zijn aan het in cache plaatsen van PHP bytecode, waardoor bytecodes en PHP klassenpaden in cache worden geplaatst.

## Parameters instellen voor Apache of Nginx

In deze sectie wordt besproken hoe u de modus voor Apache of Nginx kunt opgeven.

### Nginx-instelling

Zie de [ Nginx steekproefconfiguratie ] op _GitHub_.

### Instelling Apache.htaccess

U kunt de toepassingsmodus bijvoorbeeld instellen door `.htaccess` te bewerken. Op deze manier hoeft u de Apache-instellingen niet te wijzigen.

U kunt `.htaccess` op elk van de volgende locaties wijzigen, afhankelijk van het toegangspunt tot de Commerce-toepassing:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**om een variabele** te plaatsen:

1. Open de voorgaande bestanden in een teksteditor en voeg de gewenste instelling toe of verwijder de commentaarmarkering.

   Bijvoorbeeld, om a [ wijze ](application-modes.md) te specificeren, verwijder commentaar het volgende:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Stel de waarde van `MAGE_PROFILER` in op een van de volgende opties:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Sla uw wijzigingen in `.htaccess` op. U hoeft Apache niet opnieuw te starten om de wijziging van kracht te laten worden.

### Apache-instelling

De Apache-webserver ondersteunt het instellen van de toepassingsmodus met `mod_env` -instructies.

De Apache `mod_env` richtlijn is lichtjes verschillend in [ Apache versie 2.2 ] en [ Apache versie 2.4 ].

De volgende procedures tonen hoe u de toepassingsmodus instelt in een virtuele Apache-host. Dit is niet de enige manier om `mod_env` richtlijnen te gebruiken; raadpleeg de documentatie van Apache voor details.

>[!TIP]
>
>In de volgende sectie wordt ervan uitgegaan dat u uw virtuele host al hebt ingesteld. Als u niet hebt, raadpleeg een middel zoals [ dit leerprogramma DigitalOcean ](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**om een bootstrap variabele voor Apache op Ubuntu** te specificeren:

1. Als gebruiker met `root` voorrechten, open uw virtueel dossier van de gastheerconfiguratie in een tekstredacteur.

   Als uw virtuele host bijvoorbeeld de naam `my.magento` heeft,

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
>In deze sectie wordt ervan uitgegaan dat u al een virtuele host hebt ingesteld. Als u niet hebt, raadpleeg een middel zoals [ dit leerprogramma DigitalOcean ](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**om een bootstrap variabele voor Apache op CentOS** te specificeren:

1. Als gebruiker met `root` rechten, opent u `/etc/httpd/conf/httpd.conf` in een teksteditor.

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

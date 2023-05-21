---
title: Beveiliging van installatie op locatie
description: Meer informatie over manieren om de beveiligingspositie van uw Adobe Commerce- of Magento Open Source-installatie op locatie te verbeteren.
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Beveiliging van installatie op locatie

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) biedt CentOS- en Ubuntu-beheerders meer toegangscontrole over hun servers. Als u SELinux gebruikt *en* Apache moet een verbinding met een andere gastheer in werking stellen, moet u de bevelen in werking stellen die in deze sectie worden besproken.

>[!NOTE]
>
>Adobe heeft geen aanbeveling over het gebruik van SELinux; U kunt deze desgewenst gebruiken voor uitgebreide beveiliging. Als u SELinux gebruikt, moet u het correct vormen of Adobe Commerce en Magento Open Source kunnen onvoorspelbaar functioneren. Als u ervoor kiest SELinux te gebruiken, raadpleeg dan een bron zoals de [CentOS wiki](https://wiki.centos.org/HowTos/SELinux) regels op te stellen om communicatie mogelijk te maken.

## Suggesties voor installatie met Apache

Als u SELinux inschakelt, kunnen er problemen optreden met het uitvoeren van het installatieprogramma, tenzij u het *beveiligingscontext* van sommige directory&#39;s, als volgt:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

De voorgaande opdrachten werken alleen met de Apache-webserver. Wegens de verscheidenheid van configuraties en veiligheidsvereisten, waarborgen wij deze bevelen werk in alle situaties niet. Zie voor meer informatie:

* [man page](https://linux.die.net/man/8/httpd_selinux)
* [Server Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Communicatie tussen servers inschakelen

Als Apache en de databaseserver zich op dezelfde host bevinden, gebruikt u de volgende opdracht als u integratie wilt gebruiken die `curl` (bv. Paypal en USPS).
Om Apache in staat te stellen een verbinding met een andere gastheer met toegelaten SELinux in werking te stellen:

1. Gebruik de volgende opdracht om te bepalen of SELinux is ingeschakeld:

   ```bash
   getenforce
   ```

   `Enforcing` geeft aan dat SELinux wordt uitgevoerd.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Poorten openen in uw firewall

Afhankelijk van uw veiligheidsvereisten, zou u het noodzakelijk kunnen vinden om haven 80 en andere havens in uw firewall te openen. Wegens de gevoelige aard van voorzien van een netwerkveiligheid, adviseert Adobe sterk dat u met uw afdeling van IT alvorens te werk te gaan raadpleegt. Hier volgen enkele suggesties voor verwijzingen:

* Ubuntu: [Documentatiepagina Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Hoe-kan-ik-bestand voor CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

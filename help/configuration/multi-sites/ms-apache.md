---
title: Meerdere websites instellen met Apache
description: Volg deze zelfstudie om meerdere websites in te stellen met Apache.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Meerdere websites instellen met Apache

Wij gaan ervan uit dat:

Kopieer, indien nodig, de bestaande `index.php` script voor het ingangspunt voor uw website of [winkelweergave](https://glossary.magento.com/store-view) en voeg hieraan het volgende toe:

- U werkt op een ontwikkelcomputer (laptop, virtuele machine, enzovoort)

   Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Raadpleeg uw hostingprovider voor meer informatie.

   Er zijn extra taken nodig om Adobe Commerce in te stellen op cloudinfrastructuur. Nadat u de taken voltooit die in dit onderwerp worden besproken, zie [Meerdere websites of winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in de _Commerce Cloud-hulplijn_.

- U gebruikt één virtuele host per website; het virtuele hostconfiguratiebestand is `/etc/httpd/httpd.conf`

   Met verschillende versies van Apache op verschillende besturingssystemen worden virtuele hosts op verschillende manieren ingesteld. Raadpleeg de [Apache-documentatie](https://httpd.apache.org/docs/2.4/vhosts) of een netwerkbeheerder als u niet zeker bent hoe te opstelling een virtuele gastheer.

- De software Commerce is geïnstalleerd in `/var/www/html/magento2`
- U hebt twee andere websites dan de standaard:

   - `french.mysite.mg` met websitecode `french` en archiefweergavecode `fr`
   - `german.mysite.mg` met websitecode `german` en archiefweergavecode `de`

## Routekaart voor het instellen van meerdere websites met Apache

De vestiging veelvoudige opslag bestaat uit de volgende taken:

1. [Websites, winkels en winkels instellen](ms-admin.md) in de Admin.
1. Een maken [Virtuele host Apache](#step-2-create-apache-virtual-hosts) per Commerce-website.

## Stap 1: Websites maken, winkels maken en weergaven opslaan in Beheer

Zie [Meerdere websites instellen, weergaven opslaan en opslaan in de beheerfunctie](ms-admin.md).

## Stap 2: Virtuele Apache-hosts maken

In deze sectie wordt besproken hoe u waarden kunt instellen voor `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` met de Apache-servervariabele `SetEnvIf` in een virtuele host.

Meer informatie over `SetEnvIf`, zie:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Virtuele Apache-hosts maken**:

1. Als gebruiker met `root` rechten, opent u het virtuele hostconfiguratiebestand in een teksteditor.

   Open bijvoorbeeld `/etc/httpd/conf/httpd.conf`

1. De sectie zoeken die begint met `<VirtualHost *:80>`.
1. De volgende virtuele hosts maken na bestaande virtuele hosts:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Sla uw wijzigingen op in `httpd.conf` en sluit de teksteditor af.
1. Apache opnieuw starten:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Uw site verifiëren

Tenzij u DNS opstelling voor de URL van uw opslag hebt, moet u een statische route aan de gastheer in uw toevoegen `hosts` bestand:

1. Het besturingssysteem zoeken `hosts` bestand.
1. Voeg de statische route in het formaat toe:

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Ga naar een van de volgende URL&#39;s in uw browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Raadpleeg uw hostingprovider voor meer informatie.
>- Er zijn extra taken nodig om Adobe Commerce op cloudinfrastructuur in te stellen. zie [Meerdere Cloud-websites of -winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in de _Commerce Cloud-hulplijn_.


### Problemen oplossen

- Als uw Franse en Duitse sites 404s retourneren maar uw Admin-account wordt geladen, moet u de handeling voltooien [Stap 6: De code van de winkel toevoegen aan de basis-URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Als alle URL&#39;s 404 retourneren, moet u de webserver opnieuw starten.
- Als de beheerder niet correct werkt, zorg ervoor u opstelling uw virtuele gastheren behoorlijk.

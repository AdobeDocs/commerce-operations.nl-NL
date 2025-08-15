---
title: Meerdere websites instellen met Apache
description: Volg deze zelfstudie om meerdere websites in te stellen met Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Meerdere websites instellen met Apache

Wij gaan ervan uit dat:

Kopieer indien nodig het bestaande script voor het `index.php` ingangspunt voor uw website of de opslagweergave en voeg er het volgende aan toe:

- U werkt op een ontwikkelcomputer (laptop, virtuele machine, enzovoort)

  Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Neem contact op met uw hostingprovider voor meer informatie.

  Er zijn extra taken nodig om Adobe Commerce in te stellen op cloudinfrastructuur. Nadat u de taken voltooit die in dit onderwerp worden besproken, zie [ Opstelling veelvoudige websites of opslag ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) in _Commerce op de gids van de Infrastructuur van de Wolk_.

- U gebruikt één virtuele host per website; het configuratiebestand van de virtuele host is `/etc/httpd/httpd.conf`

  Met verschillende versies van Apache op verschillende besturingssystemen worden virtuele hosts op verschillende manieren ingesteld. Raadpleeg de [ documentatie Apache ](https://httpd.apache.org/docs/2.4/vhosts) of een netwerkbeheerder als u niet zeker bent hoe te opstelling een virtuele gastheer.

- De Commerce-software wordt geïnstalleerd in `/var/www/html/magento2`
- U hebt twee andere websites dan de standaard:

   - `french.mysite.mg` met websitecode `french` en code van de opslagweergave `fr`
   - `german.mysite.mg` met websitecode `german` en code van de opslagweergave `de`

## Routekaart voor het instellen van meerdere websites met Apache

De vestiging veelvoudige opslag bestaat uit de volgende taken:

1. [ Opstelling websites, opslag, en opslagmeningen ](ms-admin.md) in Admin.
1. Creeer één [ virtuele gastheer van Apache ](#step-2-create-apache-virtual-hosts) per website van Commerce.

## Stap 1: Websites maken, winkels maken en weergaven opslaan in Beheer

Zie [ Opstelling veelvoudige websites, opslag, en opslagmeningen in Admin ](ms-admin.md).

## Stap 2: virtuele Apache-hosts maken

In deze sectie wordt beschreven hoe u waarden instelt voor `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` de Apache-servervariabele `SetEnvIf` in een virtuele host.

Zie voor meer informatie over `SetEnvIf` :

- [ Apache 2.2 ](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [ Apache 2.4 ](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**om virtuele gastheren Apache** te creëren:

1. Als gebruiker met `root` voorrechten, open het virtuele dossier van de gastheerconfiguratie in een tekstredacteur.

   Open bijvoorbeeld `/etc/httpd/conf/httpd.conf`

1. Zoek de sectie die begint met `<VirtualHost *:80>` .
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

1. Sla de wijzigingen in `httpd.conf` op en sluit de teksteditor af.
1. Apache opnieuw starten:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Uw site verifiëren

Tenzij u DNS opstelling voor URLs van uw opslag hebt, moet u een statische route aan de gastheer in uw `hosts` dossier toevoegen:

1. Zoek het `hosts` -bestand van uw besturingssysteem.
1. Voeg de statische route in het formaat toe:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Ga naar een van de volgende URL&#39;s in uw browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Neem contact op met uw hostingprovider voor meer informatie.
>- De extra taken worden vereist aan opstelling Adobe Commerce op wolkeninfrastructuur; zie [ Opstelling veelvoudige websites of opslag van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) in _Commerce op de gids van de Infrastructuur van de Wolk_.

### Problemen oplossen

- Als uw Franse en Duitse plaatsen 404s maar uw Admin laadt terugkeren, zorg u [ Stap 6 voltooide: voeg de opslagcode aan basisURL ](ms-admin.md#step-6-add-the-store-code-to-the-base-url) toe.
- Als alle URL&#39;s 404 retourneren, moet u de webserver opnieuw starten.
- Als de beheerder niet correct werkt, zorg ervoor u opstelling uw virtuele gastheren behoorlijk.

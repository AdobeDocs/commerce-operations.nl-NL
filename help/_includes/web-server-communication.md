---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# Beveiligde webservercommunicatie

Dit onderwerp bespreekt een voorbeeld om communicatie tussen uw Webserver en onderzoeksmotor (Elasticsearch of OpenSearch) te beveiligen gebruikend een combinatie van de encryptie van de Veiligheid van de Laag van het Vervoer (TLS) en [HTTP-basisverificatie](https://datatracker.ietf.org/doc/html/rfc2617). U kunt naar keuze andere soorten authentificatie eveneens vormen; wij geven referenties aan die informatie .

(Een oudere termijn, de Veilige Laag van Contactdozen (SSL), wordt vaak gebruikt onderling verwisselbaar met TLS. In dit onderwerp verwijzen wij naar *TLS*.)

>[!WARNING]
>
>Tenzij anders vermeld, moeten alle bevelen in dit onderwerp als gebruiker met zijn ingegaan `root` rechten.

## Recommendations

We raden het volgende aan:

* De webserver gebruikt TLS.

   TLS valt buiten het toepassingsgebied van dit onderwerp; wij raden u echter ten zeerste aan een echt certificaat in productie te gebruiken en geen zelfondertekend certificaat.

* De zoekmachine werkt op dezelfde host als een webserver. Het runnen van de onderzoeksmotor en de Webserver op verschillende gastheren is voorbij het werkingsgebied van dit onderwerp.

   Het voordeel van het plaatsen van zoekmachine en de webserver op dezelfde host is dat gecodeerde communicatie hierdoor niet kan worden onderschept. De webserver van de zoekmachine hoeft niet gelijk te zijn aan de Adobe Commerce- of Magento Open Source-webserver. Adobe Commerce kan bijvoorbeeld Apache uitvoeren en Elasticsearch/OpenSearch kan nginx uitvoeren.

   Als de zoekmachine wordt blootgesteld aan het openbare web, moet u verificatie configureren. Als uw zoekmachine-instantie binnen uw netwerk is beveiligd, is dit mogelijk niet nodig. Werk met uw hostingprovider om te bepalen welke beveiligingsmaatregelen u moet implementeren om uw instantie te beschermen.

## Meer informatie over TLS

Zie een van de volgende bronnen:

* Apache

   * [Sterke codering van Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Hoe maakt u een SSL-certificaat op Apache voor Ubuntu 14.04 (zelfstudie Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Een SSL beveiligde webserver instellen met CentOS (CentOS wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL-beëindiging](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Hoe te om een SSL Certificaat op Nginx voor Ubuntu 14.04 (Digitalocean zelfstudie) te creëren](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL Certificate Installation (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)

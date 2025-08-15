---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Beveiligde webservercommunicatie

Dit onderwerp bespreekt een voorbeeld om communicatie tussen uw Webserver en onderzoeksmotor (Elasticsearch of OpenSearch) te beveiligen gebruikend een combinatie van de encryptie van de Veiligheid van de Laag van het Vervoer (TLS) en [ basisauthentificatie van HTTP ](https://datatracker.ietf.org/doc/html/rfc2617). U kunt naar keuze andere soorten authentificatie eveneens vormen; wij verstrekken verwijzingen voor die informatie.

(Een oudere termijn, de Veilige Laag van Contactdozen (SSL), wordt vaak gebruikt onderling verwisselbaar met TLS. In dit onderwerp, verwijzen wij naar *TLS*.)

>[!WARNING]
>
>Tenzij anders vermeld, moeten alle bevelen in dit onderwerp als gebruiker met `root` voorrechten zijn ingegaan.

## Aanbevelingen

We raden het volgende aan:

* De webserver gebruikt TLS.

  TLS valt buiten het bereik van dit onderwerp. Wij raden u echter ten zeerste aan een echt certificaat te gebruiken in productie en niet een zelfondertekend certificaat.

* De zoekmachine werkt op dezelfde host als een webserver. Het runnen van de onderzoeksmotor en de Webserver op verschillende gastheren is voorbij het werkingsgebied van dit onderwerp.

  Het voordeel van het plaatsen van zoekmachine en de webserver op dezelfde host is dat gecodeerde communicatie hierdoor niet kan worden onderschept. De webserver van het zoekprogramma hoeft niet hetzelfde te zijn als de Adobe Commerce-webserver. Adobe Commerce kan bijvoorbeeld Apache uitvoeren en Elasticsearch/OpenSearch kan nginx uitvoeren.

  Als de zoekmachine wordt blootgesteld aan het openbare web, moet u verificatie configureren. Als uw zoekmachine-instantie binnen uw netwerk is beveiligd, is dit mogelijk niet nodig. Werk met uw hostingprovider om te bepalen welke beveiligingsmaatregelen u moet implementeren om uw instantie te beschermen.

## Meer informatie over TLS

Zie een van de volgende bronnen:

* Apache

   * [ Apache 2.4 sterke encryptie hoe te ](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [ hoe te om een SSL Certificaat op Apache voor Ubuntu 14.04 (Digitalocean leerprogramma) te creëren ](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [ Vestiging een SSL beveiligde Webserver met CentOS (wiki CentOS) ](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [ Nginx SSL beëindiging ](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [ hoe te om een SSL Certificaat op Nginx voor Ubuntu 14.04 (Digitalocean leerprogramma) te creëren ](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [ Nginx SSL de Installatie van het Certificaat (digicert) ](https://www.digicert.com/ssl-certificate-installation-nginx.htm)

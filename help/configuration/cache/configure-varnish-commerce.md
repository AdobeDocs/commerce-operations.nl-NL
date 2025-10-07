---
title: Varnish configureren voor Commerce
description: Leer hoe u Varnish specifiek voor Adobe Commerce-toepassingen configureert. Ontdek updates van configuratiebestanden en beheertechnieken.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# De Commerce-toepassing configureren voor het gebruik van Varnish

Commerce configureren voor het gebruik van Varnish:

1. Meld u als beheerder aan bij de beheerder.
1. Klik **[!UICONTROL Stores]** > Montages > **Configuratie** > **Geavanceerd** > **Systeem** > **het Volledige Geheime voorgeheugen van de Pagina**.
1. Van de **[!UICONTROL Caching Application]** lijst, klik **Varnish Caching**.
1. Voer een waarde in het veld **[!UICONTROL TTL for public content]** in.
1. Vouw **[!UICONTROL Varnish Configuration]** uit en voer de volgende informatie in:

   | Veld | Beschrijving |
   | ----- | ----------- |
   | Toegangslijst | Ga volledig in - gekwalificeerde hostname, IP adres, of [ Klasseloze inter-domein Verpletterend (CIDR) ](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) notatieIP adreswaaier waarvoor om inhoud ongeldig te maken. Zie [ het geheime voorgeheugen van de Varnish Wissen ](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Backend-host | Ga volledig in - gekwalificeerde hostname of IP adres en luister haven van het Varnish _achterste eind_ of _oorsprongserver_; namelijk de server die de inhoud verstrekt vergroot. Dit is doorgaans uw webserver. Zie [ servers van de het geheime voorgeheugensteun van 0} Varnish.](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) |
   | Backend-poort | De luisterpoort van de oorspronkelijke server. |
   | Respijtperiode | Hiermee bepaalt u hoe lang Varnish schaalinhoud dient als de backend niet reageert. De standaardwaarde is 300 seconden. |
   | Hiermee wordt de grootte van params afgehandeld | Specificeert het maximumaantal [ lay-outhandvatten ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) om op het [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) eindpunt van HTTP voor volledig-pagina caching te verwerken. Het beperken van de grootte kan de veiligheid en de prestaties verbeteren. De standaardwaarde is 100. |

1. Klik **sparen Config**.

U kunt Varnish van het bevel ook activeren lijn-in plaats van het programma te openen aan Admin-gebruikend het bevel-lijn de interfacegereedschap van C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Een vernis-configuratiebestand exporteren

Een vernis-configuratiebestand exporteren vanuit de beheerfunctie:

1. Klik op een van de exportknoppen om een `varnish.vcl` te maken die u met Vierkant kunt gebruiken.

   Bijvoorbeeld, als u Varnish 4 hebt, klik **Uitvoer VCL voor Varnish 4**

   In de volgende afbeelding ziet u een voorbeeld:

   ![ vorm Commerce om Varnish in Admin te gebruiken ](../../assets/configuration/varnish-admin-22.png)

1. Maak een back-up van uw bestaande `default.vcl` . Wijzig vervolgens de naam van het `varnish.vcl` -bestand waarnaar u zojuist hebt geëxporteerd. `default.vcl` Kopieer het bestand vervolgens naar de map `/etc/varnish/` .

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe raadt u aan `default.vcl` te openen en de waarde van `acl purge` te wijzigen in het IP-adres van de Varnish-host. (U kunt meerdere hosts op aparte regels opgeven of u kunt ook CIDR-notatie gebruiken.)

   Bijvoorbeeld:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Als u de gezondheidscontroles van Vagrant of de wijze of de configuratie van de saint wijze wilt aanpassen, zie [ Geavanceerde configuratie van de Varnish ](config-varnish-advanced.md).

1. Varnish en uw webserver opnieuw starten:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Statische bestanden in cache opslaan

Statische bestanden moeten niet standaard in de cache worden geplaatst, maar als u ze in de cache wilt plaatsen, kunt u de sectie `Static files caching` in de VCL bewerken zodat deze de volgende inhoud bevat:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

U moet deze wijzigingen aanbrengen voordat u Commerce configureert voor het gebruik van Varnish.

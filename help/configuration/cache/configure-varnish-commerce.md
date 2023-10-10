---
title: Varnish configureren voor handel
description: Leer om uw Varnish configuratiedossier voor de toepassing van de Handel bij te werken en te beheren.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 11ccc59230a7a0d1768c043c39df43c7df031efd
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Vorm de toepassing van de Handel om Varnish te gebruiken

Om Handel te vormen om Varnish te gebruiken:

1. Meld u als beheerder aan bij de beheerder.
1. Klikken **[!UICONTROL Stores]** > Instellingen > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache**.
1. Van de **[!UICONTROL Caching Application]** lijst, klik **Varnish Caching**.
1. Voer een waarde in het dialoogvenster **[!UICONTROL TTL for public content]** veld.
1. Uitbreiden **[!UICONTROL Varnish Configuration]** en voert u de volgende gegevens in:

   | Veld | Beschrijving |
   | ----- | ----------- |
   | Toegangslijst | Ga volledig in - gekwalificeerde hostname, IP adres, of [Klasseloze inter-domein het Verpletteren (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) IP van de notatie adreswaaier waarvoor om inhoud ongeldig te maken. Zie [Varnish cache Purging](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Backend-host | Ga volledig in - gekwalificeerde hostname of IP adres en luister haven van Varnish _achterste_ of _oorspronkelijke server_ De server die de inhoud levert, Varnish versnelt. Dit is doorgaans uw webserver. Zie [Varnish cache Backend-servers](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Backend-poort | De luisterpoort van de oorspronkelijke server. |
   | Respijtperiode | Hiermee bepaalt u hoe lang Varnish schaalinhoud dient als de backend niet reageert. De standaardwaarde is 300 seconden. |
   | Hiermee wordt de grootte van params afgehandeld  [!BADGE 2.4.7-bèta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Alleen beschikbaar in 2.4.7 bèta"} | Hiermee wordt het maximale aantal [layouthandgrepen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) om op de [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP-eindpunt voor het in cache plaatsen van volledige pagina. Het beperken van de grootte kan de veiligheid en de prestaties verbeteren. De standaardwaarde is 100. |

1. Klikken **Config opslaan**.

U kunt Varnish van het bevel ook activeren lijn-in plaats van het programma te openen aan Admin-gebruikend het bevel-lijn de interfacegereedschap van C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Een vernis-configuratiebestand exporteren

Een vernis-configuratiebestand exporteren vanuit de beheerfunctie:

1. Klik op een van de exportknoppen om een `varnish.vcl` u kunt gebruiken met Varnish.

   Als u bijvoorbeeld Varnish 4 hebt, klikt u op **VCL exporteren voor Varnish 4**

   In de volgende afbeelding ziet u een voorbeeld:

   ![Handel configureren voor gebruik van Varnish in Admin](../../assets/configuration/varnish-admin-22.png)

1. Maak een back-up van uw bestaande `default.vcl`. Wijzig vervolgens de naam van de `varnish.vcl` bestand waarnaar u zojuist hebt geëxporteerd `default.vcl`. Kopieer het bestand vervolgens naar de `/etc/varnish/` directory.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe beveelt aan `default.vcl` en wijzigt u de waarde `acl purge` aan het IP adres van de gastheer van Varnish. (U kunt meerdere hosts op aparte regels opgeven of u kunt ook CIDR-notatie gebruiken.)

   Bijvoorbeeld:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Als u de gezondheidscontroles van Vagrant of de configuratie van de de aflossingswijze of van de vlekkenwijze wilt aanpassen, zie [Geavanceerde Varnish-configuratie](config-varnish-advanced.md).

1. Varnish en uw webserver opnieuw starten:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Statische bestanden in cache opslaan

Statische bestanden moeten niet standaard in de cache worden geplaatst, maar als u ze in de cache wilt plaatsen, kunt u de sectie bewerken `Static files caching` in de VCL om de volgende inhoud te hebben:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

U moet deze veranderingen aanbrengen alvorens u Handel vormt om Varnish te gebruiken.

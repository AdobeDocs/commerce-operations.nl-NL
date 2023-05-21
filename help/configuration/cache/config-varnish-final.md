---
title: Laatste verificatie
description: Controleer of uw Varnish-configuratie op de juiste wijze is ingesteld voor gebruik met de Adobe Commerce-toepassing.
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Laatste verificatie van de Varnish-configuratie

Nu gebruikt u de `default.vcl` gegenereerd voor u door Handel, kunt u enkele laatste controles uitvoeren om ervoor te zorgen dat Varnish werkt.

## HTTP-antwoordheaders verifiëren

Gebruiken `curl` of een ander hulpprogramma om HTTP-antwoordheaders weer te geven wanneer u een willekeurige handelspagina in een webbrowser bezoekt.

Controleer eerst of u [ontwikkelmodus](../cli/set-mode.md#change-to-developer-mode); anders ziet u de koppen niet.

Bijvoorbeeld:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Belangrijke koppen:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Deze waarde is ook acceptabel: `X-Magento-Cache-Debug: HIT`.

## De laadtijden van de pagina controleren

Als Varnish werkt, zou om het even welke pagina van de Handel met cacheable blokken binnen minder dan 150 ms moeten laden. Voorbeelden van dergelijke pagina&#39;s zijn de pagina&#39;s van de eerste en de winkelcategorie.

Met een browsercontrole kunt u de laadtijden van de pagina meten.

U kunt bijvoorbeeld als volgt de Chrome-controle gebruiken:

1. Heb toegang tot om het even welke cacheable pagina van de Handel in Chrome.
1. Klik met de rechtermuisknop ergens op de pagina.
1. Klik in het pop-upmenu op **[!UICONTROL Inspect Element]**
1. Klik in het deelvenster Inspecteur op de knop **[!UICONTROL Network]** tab.
1. Vernieuw de pagina.
1. Blader naar de bovenkant van het deelvenster met de controle, zodat u de URL kunt zien van de pagina die u bekijkt.

   In de volgende afbeelding ziet u een voorbeeld van het laden van de `magento2` indexpagina.

   ![Klik op de pagina die u weergeeft](../../assets/configuration/varnish-inspector.png)

   De laadtijd van de pagina wordt weergegeven naast de pagina-URL. In dit geval is de laadtijd 5 ms. Zo kunt u bevestigen dat Varnish de pagina in het cachegeheugen heeft opgeslagen.

1. Klik op de pagina-URL (in de kolom Naam) om HTTP-antwoordheaders weer te geven.

   U kunt de kopballen van HTTP bekijken die meer in detail in de Verify sectie van de reactiekoppen van HTTP worden besproken.

## De cache van Commerce controleren

Zorg ervoor dat de `<magento_root>/var/page_cache` directory is leeg:

1. Meld u aan bij de Commerce-server of schakel over naar de eigenaar van het bestandssysteem.
1. Voer de volgende opdracht in:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Heb toegang tot één of meerdere cacheable pagina&#39;s van de Handel.
1. Controleer de `var/page_cache/` directory.

   Als de directory leeg is, gefeliciteerd! U hebt Varnish en Commerce geconfigureerd om samen te werken!

1. Als u de `var/page_cache/` directory, begin Varnish opnieuw.

>[!TIP]
>
>Als er 503 (Backend Fetch Failed) fouten optreden, raadpleegt u [Problemen oplossen met 503 (service niet beschikbaar) fouten](https://support.magento.com/hc/en-us/articles/360034631211) in de _Adobe Commerce Help Center_.

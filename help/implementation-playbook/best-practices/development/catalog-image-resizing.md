---
title: Aanbevolen werkwijzen voor het wijzigen van het formaat van catalogusafbeeldingen
description: Leer hoe u kunt voorkomen dat de prestaties achteruitgaan voordat u de productie van uw Adobe Commerce-site start.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor het wijzigen van het formaat van catalogusafbeeldingen

Alle catalogusafbeeldingen moeten worden vergroot of verkleind voordat een winkel in productie wordt genomen. Als u het formaat van afbeeldingen niet aanpast voordat de productie wordt uitgevoerd, wordt het formaat van de afbeelding tijdens het laden van de pagina forceerd aangepast. Hierdoor wordt de snelheid van de site aanzienlijk verlaagd en wordt de server gedurende de eerste dagen tot weken na het opstarten meer belast.

## De trage weg

Gebruik het standaard CLI bevel resize alle beelden:

```bash
bin/magento catalog:images:resize
```

De nadelen van deze aanpak zijn:

- Het proces is single-threaded
- Het proces wijzigt de grootte van afbeeldingen die al zijn gewijzigd
- Het proces kan niet worden onderbroken, wat dagen kan duren

## De snelle (er) manier

Asynchrone afbeeldingsformaatwijziging is geïntroduceerd in Adobe Commerce 2.4 en kan afbeeldingen sneller vergroten of verkleinen.

1. Start op elke webserver tijdelijk een aantal extra wachtrijhandlers (twee keer zoveel fysieke processors per server):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Verifieer dat de rijmanagers lopen:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Vul de wachtrij met alle aanvragen voor het vergroten of verkleinen van afbeeldingen:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Nadat de grootte van alle afbeeldingen is gewijzigd, beëindigt u het proces:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## De snelle weg

Er is een andere manier om het formaat van afbeeldingen te wijzigen met de voorzijde.

De voordelen van deze aanpak zijn:

- Het proces is multi-threaded
- Het proces bestaat uit meerdere servers (als u meerdere webknooppunten hebt, een taakverdelingsmechanisme en gedeelde schijfruimte voor de `media/` map)
- Tijdens het proces worden afbeeldingen overgeslagen waarvan de grootte al is gewijzigd

Deze benadering resizes 100.000 beelden in minder dan 8 uren, terwijl het CLI bevel 6 dagen om vergt te voltooien.

1. Log in bij de server.
1. Navigeren naar `pub/media/catalog/product` en noteer een van de hashes (bijvoorbeeld 0047d83143a5a3a4683afdf116df680).
1. In de volgende voorbeelden vervangt u `www.example.com` met het domein van uw winkel en vervang de hash door de hash die u hebt vermeld.

>[!BEGINTABS]

>[!TAB gebruikt]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB beleg]

Het nadeel van `siege` is dat het alle URL&#39;s in de 10 keer bezoekt als de gelijktijdige uitvoering is ingesteld op 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB krullen]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

De `-P` argument bepaalt het aantal draden.

>[!TAB bash one-liner]

De één-lijn voor `find/curl` voorbeeld, voor het geval u kunt lopen `curl` vanaf dezelfde computer staan de afbeeldingen op:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Opnieuw vervangen `www.example.com` met het domein en de set van uw website `-P` aan het aantal draden uw server kan behandelen zonder te crashen.

>[!ENDTABS]

De uitvoer retourneert een lijst met alle productafbeeldingen in de winkel. U kunt de afbeeldingen horizontaal verslepen (met `siege` of een andere crawler) met gebruik van alle servers en processorcores die u tot uw beschikking hebt, en het vergroten of verkleinen van de cache met aanzienlijk hogere snelheid dan bij andere benaderingen.

Als u één URL voor de afbeeldingscache bezoekt, worden alle afbeeldingsgrootten op de achtergrond gegenereerd als deze nog niet bestaan. Bovendien worden bestanden overgeslagen waarvan de grootte al is gewijzigd.

>[!NOTE]
>
>- Adobe Commerce op cloud-infrastructuurprojecten kan de grootte van productafbeeldingen verschuiven naar de Fastly-service. Zie [Diepe optimalisatie van afbeeldingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) in de _Cloud Guide_.
>- Als u de externe opslagmodule gebruikt, kunt u ook proberen de afbeeldingsgrootte te verschuiven naar nginx. Zie [Afbeeldingsgrootte configureren voor externe opslag](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) in de _Configuratiegids_.

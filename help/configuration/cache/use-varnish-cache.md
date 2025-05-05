---
title: Cache wissen met Varnish
description: Leer hoe het leegmaken van cache werkt met Varnish en hoe u dit gebruikt als een web-caching accelerator voor de Adobe Commerce-toepassing.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Cache wissen met Varnish

Dit onderwerp bespreekt de grondbeginselen van het gebruiken van Varnish als web-caching accelerator voor Adobe Commerce.

## Varnish puring

Volgens [ de documentatie van Varnish ](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *zuivering* is wat gebeurt wanneer u een voorwerp uit het geheime voorgeheugen plukt en het samen met zijn varianten verwerpen.&quot; Een lade van de Varkenshaar is gelijkaardig aan een geheim voorgeheugenschoon bevel (of het klikken van **Ontruim Geheime voorgeheugen van het Magento** in Admin).

Als u de Commerce cache schoonmaakt, leegmaakt of vernieuwt, wordt Varnish ook gezuiverd.

Nadat u Varnish hebt geïnstalleerd en geconfigureerd om met Commerce te werken, kunnen de volgende acties resulteren in een Varnish purge:

- Een website onderhouden.

  Alles wat u bijvoorbeeld doet in de Admin in:

   - **BEWAART** > **Montages** > **Configuratie** > ALGEMEEN > **Algemeen**
   - **BEWAART** > **Montages** > **Configuratie** > ALGEMEEN > **Opstelling van de Valuta**
   - **BEWAART** > **Montages** > **Configuratie** > ALGEMEEN > **E-mailadressen van de opslag**

  Wanneer Commerce een dergelijke wijziging detecteert, wordt een bericht weergegeven waarin u wordt geïnformeerd de cache te vernieuwen.

- Een winkel onderhouden (bijvoorbeeld categorieën, prijzen, producten en promotieprijsregels toevoegen of bewerken).

  Varnish wordt automatisch leeggemaakt wanneer u om het even welk van deze taken uitvoert.

- Broncode onderhouden.

  Vernieuw de cache en verwijder regelmatig alles in de mappen `generated/code` en `generated/metadata` . Zie de volgende sectie voor informatie over het vernieuwen van de cache.

## Commerce configureren om vernis te zuiveren

Commerce zuivert de gastheren van Varnish nadat u de gastheren van Varnish gebruikend het [`magento setup:config:set` ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) bevel vormt.

U kunt de optionele parameter `--http-cache-hosts` gebruiken om een door komma&#39;s gescheiden lijst met varens-hosts op te geven en poorten te beluisteren. Vorm alle gastheren van Varnish, of u één of vele hebt. (Plaats geen spatie tussen de hosts.)

De parameterindeling moet `<hostname or ip>:<listen port>` zijn, waarbij u `<listen port>` kunt weglaten als dit poort 80 is.

Bijvoorbeeld:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

U kunt Varnish gastheren dan zuiveren wanneer u het geheime voorgeheugen van Commerce (die ook als *wordt bedoeld schoonmaken* het geheime voorgeheugen) in Admin of het gebruiken van de bevellijn verfrist.

Om het geheime voorgeheugen te verfrissen dat Admin gebruikt, klik **[!UICONTROL SYSTEM]** > Hulpmiddelen > **Beheer van het Geheime voorgeheugen**, dan klik **het Geheime voorgeheugen van het Magento** bij de bovenkant van de pagina. (U kunt ook afzonderlijke cachetypen vernieuwen.)

Om het geheime voorgeheugen te verfrissen gebruikend de bevellijn, gebruikt u typisch het [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) bevel als [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).

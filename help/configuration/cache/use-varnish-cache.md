---
title: Cache wissen met Varnish
description: Leer hoe het leegmaken van cache werkt met Varnish en hoe u dit gebruikt als een web-caching accelerator voor de Adobe Commerce-toepassing.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Cache wissen met Varnish

Dit onderwerp bespreekt de grondbeginselen van het gebruiken van Varnish als web-caching accelerator voor Adobe Commerce.

## Varnish puring

Volgens [Varnish-documentatie](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), *zuiveren* Dit is wat er gebeurt als u een object uit de cache haalt en het samen met de varianten verwijdert.&quot; Een vernis is vergelijkbaar met een opdracht voor het opschonen van een cache (of klikken op **Cache van Magento leegmaken** in de Admin).

Als u de Commerce cache schoonmaakt, leegmaakt of vernieuwt, wordt Varnish ook gezuiverd.

Nadat u Varnish hebt geïnstalleerd en geconfigureerd om met Commerce te werken, kunnen de volgende acties resulteren in een Varnish purge:

- Een website onderhouden.

  Alles wat u bijvoorbeeld doet in de Admin in:

   - **VOORRADEN** > **Instellingen** > **Configuratie** > ALGEMEEN **Algemeen**
   - **VOORRADEN** > **Instellingen** > **Configuratie** > ALGEMEEN **Valuta-instelling**
   - **VOORRADEN** > **Instellingen** > **Configuratie** > ALGEMEEN **E-mailadressen van winkel**

  Wanneer Commerce een dergelijke wijziging detecteert, wordt een bericht weergegeven waarin u wordt geïnformeerd de cache te vernieuwen.

- Een winkel onderhouden (bijvoorbeeld categorieën, prijzen, producten en promotieprijsregels toevoegen of bewerken).

  Varnish wordt automatisch leeggemaakt wanneer u om het even welk van deze taken uitvoert.

- Broncode onderhouden.

  U moet het cachegeheugen vernieuwen en ook regelmatig alles verwijderen in het dialoogvenster `generated/code` en `generated/metadata` mappen. Zie de volgende sectie voor informatie over het vernieuwen van de cache.

## Commerce configureren om vernis te zuiveren

Commerce zuivert Varnish gastheren nadat u de gastheren van Varnish gebruikend vormt [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) gebruiken.

U kunt de optionele parameter `--http-cache-hosts` parameter om een komma-gescheiden lijst van Varnish gastheren te specificeren en havens te luisteren. Vorm alle gastheren van Varnish, of u één of vele hebt. (Plaats geen spatie tussen de hosts.)

De parameternotatie moet `<hostname or ip>:<listen port>`, waar u kunt weglaten `<listen port>` als het poort 80 is.

Bijvoorbeeld:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

U kunt Varnish gastheren dan zuiveren wanneer u het geheime voorgeheugen van Commerce (ook genoemd *schoonmaken* (de cache) in de beheerfunctie of via de opdrachtregel.

Als u de cache wilt vernieuwen met behulp van de beheerfunctie, klikt u op **[!UICONTROL SYSTEM]** > Gereedschappen > **Cachebeheer** en klik vervolgens op **Cache van Magento leegmaken** boven aan de pagina. (U kunt ook afzonderlijke cachetypen vernieuwen.)

Als u de cache wilt vernieuwen met behulp van de opdrachtregel, gebruikt u doorgaans de opdracht [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) gebruiken als de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

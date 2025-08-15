---
title: Cache wissen met meerdere instanties van Varnish
description: Leer hoe cachewissen werkt met meerdere instanties van Varnish.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Cache wissen van meerdere instanties van Varnish

Adobe Commerce biedt ondersteuning voor meerdere instanties Varnish uit het vak.

Dit onderwerp toont de grondbeginselen van het vormen van veelvoudige instanties van Varnish met Commerce.

## Configuratie om meerdere instanties van Varnish te zuiveren

Commerce zuivert Varnish gastheren nadat u de gastheren van Varnish gebruikend het [`magento setup:config:set`](../../installation/tutorials/deployment.md) bevel vormt.

Gebruik de parameter `--http-cache-hosts` om een door komma&#39;s gescheiden lijst met varens-hosts op te geven en poorten te beluisteren. (Plaats geen spatie tussen de hosts.)

De parameterindeling moet `<hostname or ip>:<listen port>` zijn, waarbij u `<listen port>` kunt weglaten als dit poort 80 is.

Bijvoorbeeld:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

U kunt alle Versijke gastheren dan zuiveren wanneer u het geheime voorgeheugen van Commerce (die ook als _wordt bedoeld schoonmaken_ het geheime voorgeheugen) in Admin of het gebruiken van de bevellijn verfrist.

Om het geheime voorgeheugen te verfrissen dat Admin gebruikt, klik **> Hulpmiddelen >** het Beheer van het Geheime voorgeheugen **, dan klik** het Geheime voorgeheugen van Magento **bij de bovenkant van de pagina.** (U kunt ook afzonderlijke cachetypen vernieuwen.)

Om het geheime voorgeheugen van veelvoudige instanties van Varnish van cli te verfrissen gebruik het [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) bevel als [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).

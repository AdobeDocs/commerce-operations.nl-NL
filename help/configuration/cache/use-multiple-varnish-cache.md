---
title: Cache wissen met meerdere instanties van Varnish
description: Leer hoe cachewissen werkt met meerdere instanties van Varnish.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Cache wissen van meerdere instanties van Varnish

Adobe Commerce en Magento Open Source ondersteunen meerdere instanties Varnish uit het vak.

Dit onderwerp toont de grondbeginselen van het vormen van veelvoudige instanties Varnish met Handel.

## Configuratie om meerdere instanties van Varnish te zuiveren

Handel koopt Varnish gastheren aan nadat u Varnish gastheren vormt gebruikend [`magento setup:config:set`](../../installation/tutorials/deployment.md) gebruiken.

U moet de opdracht `--http-cache-hosts` parameter om een komma-gescheiden lijst van Varnish gastheren te specificeren en havens te luisteren. (Plaats geen spatie tussen de hosts.)

De parameternotatie moet `<hostname or ip>:<listen port>`, waar u kunt weglaten `<listen port>` als het poort 80 is.

Bijvoorbeeld:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

U kunt dan alle Varnish gastheren leegmaken wanneer u het geheime voorgeheugen van de Handel verfrist (ook genoemd _schoonmaken_ (de cache) in de beheerfunctie of via de opdrachtregel.

Als u de cache wilt vernieuwen met behulp van de beheerfunctie, klikt u op **SYSTEEM** > Gereedschappen > **Cachebeheer** en klik vervolgens op **Cache van Magento leegmaken** boven aan de pagina. (U kunt ook afzonderlijke cachetypen vernieuwen.)

Als u het cachegeheugen van meerdere instanties Varnish wilt vernieuwen vanuit de cli, gebruikt u de opdracht [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) gebruiken als de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

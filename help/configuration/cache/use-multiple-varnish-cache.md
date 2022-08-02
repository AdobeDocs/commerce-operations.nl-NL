---
title: Cache wissen met meerdere instanties van Varnish
description: Leer hoe cachewissen werkt met meerdere instanties van Varnish.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Cache wissen van meerdere instanties van Varnish

Adobe Commerce en Magento Open Source ondersteunen meerdere instanties Varnish uit het vak.

Dit onderwerp toont de grondbeginselen van het vormen van veelvoudige instanties Varnish met Handel.

## Configuratie om meerdere instanties van Varnish te zuiveren

Handel koopt Varnish gastheren aan nadat u Varnish gastheren vormt gebruikend [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) gebruiken.

U moet de opdracht `--http-cache-hosts` parameter om een komma-gescheiden lijst van Varnish gastheren te specificeren en havens te luisteren. (Plaats geen spatie tussen de hosts.)

De parameternotatie moet `<hostname or ip>:<listen port>`, waar u kunt weglaten `<listen port>` als het poort 80 is.

Bijvoorbeeld:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

U kunt dan alle Varnish gastheren leegmaken wanneer u het geheime voorgeheugen van de Handel verfrist (ook genoemd _schoonmaken_ (de cache) in de beheerfunctie of via de opdrachtregel.

Als u de cache wilt vernieuwen met behulp van de beheerfunctie, klikt u op **SYSTEEM** > Gereedschappen > **Cachebeheer** en klik vervolgens op **Magento-cache leegmaken** boven aan de pagina. (U kunt ook afzonderlijke cachetypen vernieuwen.)

Als u het cachegeheugen van meerdere instanties Varnish wilt vernieuwen vanuit de cli, gebruikt u de opdracht [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

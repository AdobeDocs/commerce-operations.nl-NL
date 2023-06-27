---
title: Upgrade de [!DNL Data Migration Tool]
description: Leer hoe u de upgrade uitvoert voor [!DNL Data Migration Tool] gegevens tussen Magento 1 en Magento 2 over te dragen.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Upgrade de [!DNL Data Migration Tool]

Om ervoor te zorgen dat de versies van uw huidige Magento 2 installatie en [!DNL Data Migration Tool] precies hetzelfde geldt, moet u mogelijk het gereedschap upgraden.

## Vereisten

Voordat u de [!DNL Data Migration Tool]moet u:

* Upgrade uw Magento-software voor de nieuwste versie

* Maak een back-up van de `vendor/magento/data-migration-tool` directory

* Zorg ervoor dat de [!DNL Data Migration Tool] versie komt overeen met de versie van de Magento-toepassing

### Upgrade uw Magento-software

Als u dat nog niet hebt gedaan, [upgrade uitvoeren van de Magento-software](../../upgrade/overview.md).

### Maak een back-up van de `vendor/magento/data-migration-tool` directory

Voordat u de upgrade uitvoert [!DNL Data Migration Tool], minstens een back-up maken van `vendor/magento/data-migration-tool` directory. Tijdens de upgrade kan deze worden verwijderd en vervangen door de bijgewerkte code.

U kunt ook een back-up maken van de volledige Magento-codebase en -database met de volgende opdracht:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>De `vendor/magento/data-migration-tool` bevat uw aangepaste code. Als u er geen back-up van maakt, kunnen uw aanpassingen tijdens de upgrade verloren gaan.


### Versies afstemmen

De versies van de [!DNL Data Migration Tool] en uw Magento-software moet precies overeenkomen. Magento 2.1.2 vereist bijvoorbeeld versie 2.1.2 van het [!DNL Data Migration Tool].

Zie de [Installeren [!DNL Data Migration Tool]](install.md) onderwerp om te weten hoe te:

* [Controleren](install.md#check-your-version) uw versie van Magento 2

* [Zoeken](install.md#find-released-versions-of-data-migration-tool) vrijgegeven versies van de [!DNL Data Migration Tool]

* [Controleren](install.md#check-version-of-installed-data-migration-tool) de [!DNL Data Migration Tool] versie

## Upgrade de [!DNL Data Migration Tool]

1. Meld u aan bij uw toepassingsserver als, of schakel over naar, [de eigenaar van het bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
1. Voer de volgende opdracht in:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   waar `<version>` moet overeenkomen met de versie van de codebase Magento 2.

   Voer bijvoorbeeld voor versie 2.1.2 het volgende in:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Wacht terwijl het bevel voltooit.

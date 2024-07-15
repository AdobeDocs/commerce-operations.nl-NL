---
title: Upgrade de  [!DNL Data Migration Tool]
description: Leer hoe te om  [!DNL Data Migration Tool]  te bevorderen om gegevens tussen Magento 1 en Magento 2 over te brengen.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Een upgrade uitvoeren van de [!DNL Data Migration Tool]

Om ervoor te zorgen dat de versies van uw huidige Magento 2-installatie en de [!DNL Data Migration Tool] exact overeenkomen, moet u mogelijk een upgrade van het gereedschap uitvoeren.

## Vereisten

Voordat u de upgrade van [!DNL Data Migration Tool] uitvoert, moet u:

* Upgrade de software van uw Magento voor de nieuwste versie

* Maak een back-up van de map `vendor/magento/data-migration-tool`

* Zorg ervoor dat de versie van [!DNL Data Migration Tool] overeenkomt met de versie van de Magento-toepassing

### Upgrade uw Magento uitvoeren

Als u dit nog niet hebt gedaan, [ bevorder de software van het Magento ](../../upgrade/overview.md).

### Maak een back-up van de map `vendor/magento/data-migration-tool`

Maak een back-up van ten minste de map `vendor/magento/data-migration-tool` voordat u de upgrade van [!DNL Data Migration Tool] uitvoert. Tijdens de upgrade kan deze worden verwijderd en vervangen door de bijgewerkte code.

U kunt ook een back-up maken van de volledige codebase en database van het Magento met de volgende opdracht:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>De map `vendor/magento/data-migration-tool` bevat uw aangepaste code. Als u er geen back-up van maakt, kunnen uw aanpassingen tijdens de upgrade verloren gaan.


### Versies afstemmen

De versies van [!DNL Data Migration Tool] en uw software van het Magento moeten precies aanpassen. Magento 2.1.2 vereist bijvoorbeeld versie 2.1.2 van de [!DNL Data Migration Tool] .

Zie [ installeer  [!DNL Data Migration Tool]](install.md) onderwerp om te weten hoe te:

* [ Controle ](install.md#check-your-version) uw Magento 2 versie

* [ vind ](install.md#find-released-versions-of-data-migration-tool) vrijgegeven versies van [!DNL Data Migration Tool]

* [ Controle ](install.md#check-version-of-installed-data-migration-tool) de [!DNL Data Migration Tool] versie

## Een upgrade uitvoeren van de [!DNL Data Migration Tool]

1. Login aan uw toepassingsserver als, of schakelaar aan, [ de eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
1. Voer de volgende opdracht in:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   waarbij `<version>` moet overeenkomen met de versie van de codebase Magento 2.

   Voer bijvoorbeeld voor versie 2.1.2 het volgende in:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Wacht terwijl het bevel voltooit.

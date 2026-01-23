---
title: Externe opslag configureren
description: Leer hoe te om de module van de Verre Opslag voor de op-gebouwCommerce toepassing te vormen.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Externe opslag configureren

De module Externe opslag biedt de optie om mediabestanden op te slaan en de import en export te plannen in een permanente, externe opslagcontainer met behulp van een opslagservice, zoals AWS S3.

Standaard worden mediabestanden in de Adobe Commerce-toepassing opgeslagen in hetzelfde bestandssysteem dat de toepassing bevat. Dit is inefficiënt voor complexe configuraties met meerdere servers en kan leiden tot verminderde prestaties bij het delen van bronnen. Met de module Externe opslag kunt u mediabestanden opslaan in de map `pub/media` en bestanden importeren/exporteren in de map `var` van de opslagmap voor externe objecten om te profiteren van het vergroten of verkleinen van afbeeldingen aan de serverzijde.

>[!BEGINSHADEBOX]

U kunt niet zowel externe opslag _als_ die gegevensbestandopslag hebben tezelfdertijd wordt toegelaten. U moet de databaseopslag uitschakelen voordat u externe opslag inschakelt.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Het inschakelen van externe opslag kan van invloed zijn op uw bestaande ontwikkelervaring. Bepaalde PHP-bestandsfuncties werken bijvoorbeeld mogelijk niet naar behoren. Het gebruik van Commerce Framework voor bestandsbewerkingen moet worden afgedwongen. De lijst van verboden PHP inheemse functies is beschikbaar in [&#x200B; magento-coding-standard &#x200B;](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) bewaarplaats.

>[!ENDSHADEBOX]

>[!INFO]
>
>- Externe opslag is alleen beschikbaar voor Commerce versie 2.4.2 en hoger. Zie [&#x200B; 2.4.2 versienota&#39;s &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- De Verre opslagmodule heeft _beperkte_ steun op Adobe Commerce op wolkeninfrastructuur. Adobe kan de service voor opslagadapters van derden niet volledig oplossen. Zie [&#x200B; verre opslag voor Commerce op de infrastructuur van de Wolk &#x200B;](cloud-support.md) voor begeleiding die verre opslag voor wolkenprojecten uitvoeren.

![&#x200B; Verre het schema van de opslagconfiguratie illustrerend het verband tussen lokale en wolkenopslag &#x200B;](../../assets/configuration/remote-storage-schema.png)

## Opties voor externe opslag

U kunt verre opslag vormen gebruikend de `remote-storage` optie met het [`setup` bevel CLI &#x200B;](../../installation/tutorials/deployment.md). Voor de optie `remote-storage` wordt de volgende syntaxis gebruikt:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` verwijst naar de specifieke naam van de parameter voor externe opslag. De volgende lijst maakt een lijst van de parameters beschikbaar voor het vormen van verre opslag:

| Opdrachtregelparameter | Parameternaam | Beschrijving | Standaardwaarde |
|--- |--- |--- |--- |
| `remote-storage-driver` | chauffeur | De naam van de adapter <br> Mogelijke waarden:<br>**dossier**: Maakt verre opslag onbruikbaar en gebruikt het lokale filesystem <br>**aws-s3**: Gebruik de [&#x200B; Eenvoudige Dienst van de Opslag van Amazon (Amazon S3) &#x200B;](remote-storage-aws-s3.md) | none |
| `remote-storage-bucket` | emmer | Objectopslag of containernaam | none |
| `remote-storage-prefix` | prefix | Optioneel voorvoegsel (locatie binnen opslag van object) | leeg |
| `remote-storage-region` | regio | Naam regio | none |
| `remote-storage-key` | toegangstoets | Optionele toegangstoets | leeg |
| `remote-storage-secret` | geheime sleutel | Optionele geheime sleutel | leeg |

### Opslagadapters

De standaardopslaglocatie bevindt zich in het lokale bestandssysteem. A _opslagadapter_ laat u toe om met een opslagdienst te verbinden en uw dossiers op te slaan overal. [!DNL Commerce] ondersteunt het configureren van de volgende opslagservices:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Externe opslag inschakelen

U kunt externe opslag installeren tijdens een Adobe Commerce-installatie of externe opslag toevoegen aan een bestaande Commerce-instantie. In de volgende voorbeelden wordt elke methode met een set `remote-storage` -parameters met Commerce `setup` CLI-opdrachten getoond. U moet minimaal de opslagruimte `driver`, `bucket` en `region` opgeven.

- Voorbeeld: Commerce installeren met externe opslag

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Voorbeeld: externe opslag inschakelen op bestaande Commerce

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Voor Adobe Commerce op wolkeninfrastructuur, zie [&#x200B; verre opslag voor Commerce op de infrastructuur van de Wolk vormen &#x200B;](cloud-support.md).

## Inhoud migreren

Nadat u verre opslag voor een specifieke adapter toelaat, kunt u CLI gebruiken om bestaande _media_ dossiers aan de verre opslag te migreren.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Het synchronisatiebevel migreert slechts dossiers in de `pub/media` folder, _niet_ de invoer/de uitvoerdossiers in de `var` folder. Zie [&#x200B; Geplande Invoer/de Uitvoer &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=nl-NL) in _Commerce 2.4 Gids van de Gebruiker_.


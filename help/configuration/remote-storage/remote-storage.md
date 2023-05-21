---
title: Externe opslag configureren
description: Leer hoe te om de Verre module van de Opslag voor de toepassing van de Handel op-gebouw te vormen.
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Externe opslag configureren

De module Externe opslag biedt de optie om mediabestanden op te slaan en de import en export te plannen in een permanente, externe opslagcontainer met een opslagservice, zoals AWS S3. Standaard worden mediabestanden in de Adobe Commerce-toepassing opgeslagen in hetzelfde bestandssysteem dat de toepassing bevat. Dit is inefficiënt voor complexe configuraties met meerdere servers en kan leiden tot verminderde prestaties bij het delen van bronnen. Met de module Externe opslag kunt u mediabestanden opslaan in het dialoogvenster `pub/media` map en bestanden importeren/exporteren in de `var` van de externe objectopslag om te profiteren van het vergroten of verkleinen van afbeeldingen op de server.

>[!INFO]
>
>De verre opslag is beschikbaar voor Handel versie 2.4.2 en later slechts. Zie de [2.4.2 Opmerkingen bij de release](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>De externe opslagmodule heeft _beperkt_ ondersteuning voor Adobe Commerce op cloudinfrastructuur. Adobe kan de service voor opslagadapters van derden niet volledig oplossen. Zie [Externe opslag configureren voor handel op Cloud-infrastructuur](cloud-support.md) voor begeleiding bij de implementatie van externe opslag voor cloudprojecten.

![schemaafbeelding](../../assets/configuration/remote-storage-schema.png)

## Opties voor externe opslag

U kunt externe opslag configureren met de `remote-storage` met de [`setup` CLI, opdracht](../../installation/tutorials/deployment.md). De `remote-storage` gebruikt u de volgende syntaxis:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

De `parameter-name` verwijst naar de specifieke naam van de parameter voor externe opslag. De volgende lijst maakt een lijst van de parameters beschikbaar voor het vormen van verre opslag:

| Opdrachtregelparameter | Parameternaam | Beschrijving | Standaardwaarde |
|--- |--- |--- |--- |
| `remote-storage-driver` | chauffeur | Naam adapter<br>Mogelijke waarden:<br>**file**: Hiermee wordt externe opslag uitgeschakeld en wordt het lokale bestandssysteem gebruikt <br>**aws-s3**: Gebruik de [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | none |
| `remote-storage-bucket` | emmer | Objectopslag of containernaam | none |
| `remote-storage-prefix` | prefix | Optioneel voorvoegsel (locatie binnen opslag van object) | leeg |
| `remote-storage-region` | regio | Naam regio | none |
| `remote-storage-key` | toegangstoets | Optionele toegangstoets | leeg |
| `remote-storage-secret` | geheime sleutel | Optionele geheime sleutel | leeg |

### Opslagadapters

De standaardopslaglocatie bevindt zich in het lokale bestandssysteem. A _opslagadapter_ kunt u verbinding maken met een opslagservice en uw bestanden overal opslaan. [!DNL Commerce] ondersteunt het configureren van de volgende opslagservices:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Externe opslag inschakelen

U kunt externe opslag installeren tijdens een Adobe Commerce-installatie of externe opslag toevoegen aan een bestaande Commerce-instantie. In de volgende voorbeelden wordt elke methode met een set `remote-storage` parameters met handel `setup` CLI-opdrachten. U moet de opslag minimaal leveren `driver`, `bucket`, en `region`.

- Voorbeeld: Koophandel installeren met externe opslag

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Voorbeeld: Externe opslag inschakelen bij bestaande handel

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

>[!TIP]
>
>Voor Adobe Commerce over cloudinfrastructuur raadpleegt u [Externe opslag configureren voor handel op Cloud-infrastructuur](cloud-support.md).

## Beperkingen

U kunt niet tegelijkertijd zowel externe opslag als databaseopslag inschakelen. Schakel databaseopslag uit als u externe opslag gebruikt.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Het inschakelen van externe opslag kan van invloed zijn op uw bestaande ontwikkelervaring. Bepaalde PHP-bestandsfuncties werken bijvoorbeeld mogelijk niet naar behoren. Het gebruik van het Kader van de Handel voor dossierverrichtingen moet worden afgedwongen.

De lijst met verboden native PHP functies is beschikbaar in [magento-coding-standard repository][code-standard].

## Inhoud migreren

Nadat u externe opslag voor een specifieke adapter hebt ingeschakeld, kunt u de CLI gebruiken om bestaande _media_ naar de externe opslag.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Met de opdracht Synchroniseren worden alleen bestanden gemigreerd in het dialoogvenster `pub/media` directory, _niet_ de import-/exportbestanden in het dialoogvenster `var` directory. Zie [Geplande import/export][import-export] in de _Handboek Handel 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php

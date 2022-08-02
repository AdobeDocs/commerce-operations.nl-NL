---
title: Externe opslag configureren
description: Leer hoe te om de Verre module van de Opslag voor de toepassing van de Handel op-gebouw te vormen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Externe opslag configureren

De module Externe opslag biedt de optie om mediabestanden op te slaan en import/export te plannen in een permanente, externe opslagcontainer met een opslagservice, zoals AWS S3. Standaard worden de [!DNL Commerce] de toepassing slaat media dossiers in het zelfde dossiersysteem op dat de toepassing bevat. Dit is inefficiënt voor complexe configuraties met meerdere servers en kan leiden tot verminderde prestaties bij het delen van bronnen. Met de module Externe opslag kunt u mediabestanden opslaan in het dialoogvenster `pub/media` map en bestanden importeren/exporteren in de `var` van de externe objectopslag om te profiteren van het vergroten of verkleinen van afbeeldingen op de server.

>[!INFO]
>
>Externe opslag is alleen beschikbaar in versie 2.4.2 en hoger. Zie de [2.4.2 Opmerkingen bij de release](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>De externe opslagmodule heeft _beperkt_ ondersteuning voor Adobe Commerce op cloudinfrastructuur. Adobe kan de service voor opslagadapters van derden niet volledig oplossen.

![schemaafbeelding](../../assets/configuration/remote-storage-schema.png)

## Opties voor externe opslag

U kunt externe opslag configureren met de `remote-storage` met de [`setup` CLI, opdracht][setup]. De `remote-storage` gebruikt u de volgende syntaxis:

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

U kunt externe opslag installeren tijdens een nieuwe [!DNL Commerce] installatie of voeg het aan een bestaande instantie van de Handel toe gebruikend `remote-storage` naam-en-waardeparen van parameters met `setup` CLI-opdrachten. U moet de opslag minimaal leveren `driver`, `bucket`, en `region`.

In de volgende voorbeelden wordt de externe opslag met een AWS S3-opslagadapter in de VS ingeschakeld:

- Nieuwe installatie [!DNL Commerce] met externe opslag

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Externe opslag inschakelen op bestaande [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## Beperkingen

U kunt niet tegelijkertijd zowel externe opslag als databaseopslag inschakelen. Schakel databaseopslag uit als u externe opslag gebruikt.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Het inschakelen van externe opslag kan van invloed zijn op uw bestaande ontwikkelervaring. Bepaalde PHP-bestandsfuncties werken bijvoorbeeld mogelijk niet naar behoren. Het gebruik van het Kader van de Handel voor dossierverrichtingen moet worden afgedwongen.

De lijst met verboden native PHP functies is beschikbaar in [Magento-coderingsstandaard] opslagplaats.

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
[nginx-module]: http://nginx.org/en/docs/http/ngx_http_image_filter_module.html
[Magento-coderingsstandaard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp

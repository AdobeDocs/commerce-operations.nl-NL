---
title: De vergrendelingsprovider configureren
description: Voer de volgende stappen uit om te voorkomen dat de dubbele uitsnijdtaken en uitsnijdgroepen worden uitgevoerd op uw Adobe Commerce- of Magento Open Source-implementatie.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# De vergrendelingsprovider configureren

Voordat u deze opdracht uitvoert, moet u het volgende doen: *of* u moet [de toepassing installeren](../advanced.md):

* [Implementatieconfiguratie maken of bijwerken](deployment.md)
* [Het databaseschema maken](database.md)

## Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## De vergrendeling configureren

Configureer een vergrendelingsprovider om te voorkomen dat dubbele uitsnijdtaken en uitsnijdgroepen worden gestart. (Vereist Adobe Commerce of Magento Open Source 2.2.x, 2.2.5 en hoger, en 2.3.3 en hoger.)

Adobe Commerce en Magento Open Source gebruiken de database om vergrendelingen standaard op te slaan. Als u meerdere knooppunten op uw servers hebt, raden we u aan Zookeeper als vergrendelingsprovider te gebruiken.

Als u Adobe Commerce uitvoert op een cloudinfrastructuur, hoeft u geen instellingen voor een vergrendelingsprovider te configureren. De toepassing vormt de leverancier van de dossierslot voor Pro projecten tijdens het leveringsproces. Zie [Cloud-variabelen](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Opdrachtgebruik

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschrijvingen

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--lock-provider` | Naam provider vergrendelen: `db`, `zookeeper`, of `file`.<br><br>De standaardvergrendelingsprovider: `db` | Nee |
| `--lock-db-prefix` | Het specifieke db voorvoegsel om vergrendelingsconflicten te voorkomen bij het gebruik van het `db` vergrendelingsprovider.<br><br>De standaardwaarde: `NULL` | Nee |
| `--lock-zookeeper-host` | Host en poort om verbinding te maken met de Zookeeper-cluster wanneer u de `zookeeper` vergrendelingsprovider.<br><br>Bijvoorbeeld: `127.0.0.1:2181` | Ja, als u `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Het pad waar Zookeeper sloten opslaat.<br><br>Het standaardpad is: `/magento/locks` | Nee |
| `--lock-file-path` | Het pad waar de bestandsvergrendelingen worden opgeslagen. | Ja, als u `--lock-provider=file` |

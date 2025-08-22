---
title: De vergrendelingsprovider configureren
description: Voer de volgende stappen uit om te voorkomen dat de dubbele uitsnijdtaken en uitsnijdgroepen worden uitgevoerd tijdens de Adobe Commerce-implementatie.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# De vergrendelingsprovider configureren

Alvorens u dit bevel in werking stelt, moet u het volgende *doen of* u moet [ de toepassing ](../advanced.md) installeren:

* [Implementatieconfiguratie maken of bijwerken](deployment.md)
* [Het databaseschema maken](database.md)

## Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## De vergrendeling configureren

Configureer een vergrendelingsprovider om te voorkomen dat dubbele uitsnijdtaken en uitsnijdgroepen worden gestart. (Vereist Adobe Commerce 2.2.x, 2.2.5 en hoger, en 2.3.3 en hoger.)

Adobe Commerce gebruikt de database standaard om vergrendelingen op te slaan. Als u meerdere knooppunten op uw servers hebt, raden we u aan Zookeeper als vergrendelingsprovider te gebruiken.

Als u Adobe Commerce uitvoert op een cloudinfrastructuur, hoeft u geen instellingen voor een vergrendelingsprovider te configureren. De toepassing vormt de leverancier van de dossierslot voor Pro projecten tijdens het leveringsproces. Zie [ variabelen van de Wolk ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Opdrachtgebruik

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschrijvingen

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--lock-provider` | Naam van provider vergrendelen: `db`, `zookeeper` of `file` .<br><br> De standaardvergrendelingsprovider: `db` | Nee |
| `--lock-db-prefix` | Het specifieke voorvoegsel van de tab om vergrendelingsconflicten te voorkomen bij gebruik van de vergrendelingsprovider van `db` .<br><br> De standaardwaarde: `NULL` | Nee |
| `--lock-zookeeper-host` | Gastheer en poort om verbinding te maken met de Zookeeper-cluster wanneer u de vergrendelingsprovider `zookeeper` gebruikt.<br><br> Bijvoorbeeld: `127.0.0.1:2181` | Ja, als u `--lock-provider=zookeeper` instelt |
| `--lock-zookeeper-path` | Het pad waar Zookeeper vergrendelingen opslaat.<br><br> Het standaardpad is: `/magento/locks` | Nee |
| `--lock-file-path` | Het pad waar de bestandsvergrendelingen worden opgeslagen. | Ja, als u `--lock-provider=file` instelt |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->

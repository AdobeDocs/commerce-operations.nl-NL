---
title: Voorbeeldgegevenspakketten van Composer downloaden
description: Voer de volgende stappen uit om Adobe Commerce voorbeeldgegevens te installeren met behulp van Composer PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Voorbeeldgegevenspakketten van Composer downloaden

In deze sectie wordt beschreven hoe u voorbeeldgegevens kunt installeren als u de Adobe Commerce-software op een van de volgende manieren hebt geïnstalleerd:

* Een gecomprimeerd archief downloaden van `https://magento.com/tech-resources/download`.

  Als u een archief van GitHub downloadde, werkt deze methode niet omdat `composer.json` bestand bevat niet het `repo.magento.com` URL.

* Gebruikt `composer create-project`

U kunt deze methode gebruiken om voorbeeldgegevens op te halen voor Adobe Commerce, maar u moet hetzelfde doen [verificatietoetsen](../prerequisites/authentication-keys.md) die u gebruikte om de toepassing te installeren.

>[!NOTE]
>
>Als u fouten tegenkomt, zoals `Could not find package...` of `...no matching package found...`, zorg ervoor dat er geen typos in uw bevel zijn. Als er nog steeds fouten optreden, hebt u mogelijk geen toegang tot de juiste Composer-opslagruimten, met name als u Adobe Commerce gebruikt. Contact [Adobe Commerce-ondersteuning](https://support.magento.com/hc/en-us) voor hulp.

U kunt Composer gebruiken om voorbeeldgegevens te installeren voor of na de installatie van de toepassing. Het kan echter zijn dat [extra taken](remove-or-update.md).

Als u een bijdragende ontwikkelaar bent, verwijs naar [Installeren door opslagplaatsen te klonen](git-repositories.md).

>[!WARNING]
>
>Installeer geen voorbeeldgegevens als uw toepassing is ingesteld op [productiemodus](../../configuration/bootstrap/application-modes.md#production-mode). Overschakelen op [ontwikkelmodus](../../configuration/bootstrap/application-modes.md#developer-mode) eerst. Voorbeeldgegevens installeren in de productiemodus [mislukt](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Als u voorbeeldgegevens wilt installeren via de opdrachtregel, voert u de volgende opdracht in als de eigenaar van het bestandssysteem in het dialoogvenster `<app_root>` map:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Als u voorbeeldgegevens installeert _na_ wanneer u de toepassing installeert, moet u ook de volgende opdracht uitvoeren om de database en het schema in het `<app_root>` map:

```bash
bin/magento setup:upgrade
```

U moet [authenticate](../prerequisites/authentication-keys.md) om de actie te voltooien.

## Verificatiefout

De volgende verificatiefout kan worden weergegeven:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Als de fout wordt weergegeven, wijzigt u de installatiemap van de toepassing en voert u deze uit `composer update`, die u om uw [verificatietoetsen](../prerequisites/authentication-keys.md).

## De installatie van voorbeeldgegevens voltooien

{{$include /help/_includes/sample-data-complete.md}}

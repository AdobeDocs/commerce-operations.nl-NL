---
title: Voorbeeldgegevenspakketten van Composer downloaden
description: Voer de volgende stappen uit om Adobe Commerce voorbeeldgegevens te installeren met behulp van Composer PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Voorbeeldgegevenspakketten van Composer downloaden

In deze sectie wordt beschreven hoe u voorbeeldgegevens kunt installeren als u de Adobe Commerce-software op een van de volgende manieren hebt geïnstalleerd:

* Een gecomprimeerd archief downloaden vanuit `https://magento.com/tech-resources/download` .

  Als u een archief van GitHub downloadt, werkt deze methode niet omdat het `composer.json` dossier niet `repo.magento.com` URL bevat.

* Gebruikt `composer create-project`

U kunt deze methode gebruiken om steekproefgegevens voor Adobe Commerce te krijgen, maar u moet de zelfde [&#x200B; authentificatietoetsen &#x200B;](../prerequisites/authentication-keys.md) gebruiken die u gebruikte om de toepassing te installeren.

>[!NOTE]
>
>Als u fouten tegenkomt, zoals `Could not find package...` of `...no matching package found...` , moet u ervoor zorgen dat er geen typos in uw opdracht voorkomt. Als er nog steeds fouten optreden, hebt u mogelijk geen toegang tot de juiste Composer-opslagruimten, met name als u Adobe Commerce gebruikt. Contact {de Steun van 0} Adobe Commerce [&#x200B; voor hulp.](https://support.magento.com/hc/en-us)

U kunt Composer gebruiken om steekproefgegevens of vóór of na het installeren van de toepassing te installeren; nochtans, zouden er [&#x200B; extra taken &#x200B;](remove-or-update.md) kunnen zijn.

Als u een bijdragende ontwikkelaar bent, verwijs naar [&#x200B; installeren door bewaarplaatsen &#x200B;](git-repositories.md) te klonen.

>[!WARNING]
>
>Installeer geen steekproefgegevens als uw toepassing voor [&#x200B; productiemodus &#x200B;](../../configuration/bootstrap/application-modes.md#production-mode) wordt geplaatst. Schakelaar aan [&#x200B; ontwikkelaarwijze &#x200B;](../../configuration/bootstrap/application-modes.md#developer-mode) eerst. Het installeren van steekproefgegevens op productiemodus [&#x200B; ontbreekt &#x200B;](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Als u voorbeeldgegevens wilt installeren via de opdrachtregel, voert u de volgende opdracht in als de eigenaar van het bestandssysteem in de map `<app_root>` :

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Als u steekproefgegevens _na_ het installeren van de toepassing installeert, moet u het volgende bevel ook in werking stellen om het gegevensbestand en het schema in de `<app_root>` folder bij te werken:

```bash
bin/magento setup:upgrade
```

U wordt vereist om [&#128279;](../prerequisites/authentication-keys.md) voor authentiek te verklaren om de actie te voltooien.

## Verificatiefout

De volgende verificatiefout kan worden weergegeven:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Als de foutenvertoningen, verandering in uw folder van de toepassingsinstallatie en looppas `composer update`, die u voor uw [&#x200B; authentificatietoetsen &#x200B;](../prerequisites/authentication-keys.md) ertoe aanzet.

## De installatie van voorbeeldgegevens voltooien

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->

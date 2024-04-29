---
title: Tips en trucs voor composers
description: Meer informatie over algemene Composer-ontwikkelingstaken en richtlijnen voor het snel oplossen van problemen.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Tips en trucs voor composers

Er kunnen problemen optreden wanneer u Adobe Commerce-modules ontwikkelt met Composer. Deze beste praktijken beschrijven sommige gemeenschappelijke taken om ontwikkeling gemakkelijker te maken en u te helpen problemen snel oplossen.

>[!NOTE]
>
>Deze richtsnoeren zijn in de eerste plaats van toepassing op [algemene referentiearchitectuur (GRA)](../overview.md) projecten.

## Composer versnellen

Installeren [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) om Composer te versnellen met asynchrone pakketdownloads.

```bash
composer global require hirak/prestissimo
```

Als u problemen ondervindt, verwijdert u de installatie `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Problemen met vage versies oplossen

Composer wordt soms geblokkeerd door pakketversies. U kunt berichten over versies zien die incompatibel zijn zelfs als zij niet zijn. Probeer Composer opnieuw in te stellen voordat u de compatibiliteitsproblemen gaat opsporen:

1. Wis de Composer-cache.

   ```bash
   composer clearcache
   ```

1. Verwijder de `composer.lock` bestand voor alle pakketten.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Installeer de Composer-pakketten opnieuw.

   ```bash
   composer install
   ```

>[!TIP]
>
>Met deze stappen worden alle pakketten bijgewerkt naar de meest recente beschikbare versie. De `composer.lock` van Git om deze upgrades ongedaan te maken.

## Controleren op mogelijke updates in clientpakketten

1. Kom te weten welke pakketten verouderd zouden kunnen zijn.

   ```bash
   composer outdated
   ```

1. Filteren met jokertekens en/of de `--minor-only` optie voor het overslaan van niet-compatibele upgrades:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Controleren of een module is geïnstalleerd

Bekijk details over alle geïnstalleerde pakketten op een Git-vertakking.

```bash
composer info
```

Uitvoeren `composer install` na het schakelen van de takken van het Git en alvorens te lopen `composer info`. Anders geeft Composer details weer over de vorige vertakking die u had uitgecheckt.

>[!TIP]
>
>Gebruik een van de volgende opdrachten om te filteren of te zoeken.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Ontdek waarom een (specifieke versie van a) pakket is geïnstalleerd

Soms wordt door Composer de meest recente beschikbare versie van een pakket geïnstalleerd vanwege een strikte afhankelijkheid in een ander pakket.

Kom te weten als er een strikte afhankelijkheid in een ander pakket is.

```bash
composer why client/module-example
```

Als de resultaten een lijst van metapakketten of een ander pakket tonen dat niet uitdrukkelijk wordt vereist, stel het bevel op dat pakket in werking:

```bash
composer why example/metapackage
```

## Ontdek waarom een pakket niet is geïnstalleerd

Soms installeert Composer geen pakket omdat dit een conflict veroorzaakt met een ander pakket, het wordt vervangen door een ander pakket of omdat u niet hebt gedefinieerd dat het een afhankelijkheid is.

Ontdek waarom een pakket niet is geïnstalleerd.

```bash
composer why-not client/module-example
```

## Een persoonlijke Composer-opslagplaats hosten

Als u een persoonlijke Composer-opslagplaats wilt gebruiken [Private Packagist](https://packagist.com/) of [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). Niet gebruiken [Satis](https://github.com/composer/satis).

- **Private Packagist** is veilig, kost ongeveer $600 USD per jaar met drie admin-gebruikers en wordt gehost.

- **JFrog Artifactory** begint bij USD 1.176 per jaar. Het wordt niet zo vaak gebruikt als Packagist, maar het ondersteunt meer talen dan PHP.

- **Satis** heeft geen ingebouwde beveiliging, geen automatisering en vereist extra hosting. Het is alleen vrij als je tijd ook vrij is.

## Versiepakketten

Gebruiken [Semantische versie 2.0.0](https://semver.org/spec/v2.0.0.html) zoals beschreven in de Adobe Commerce [versieschema](https://developer.adobe.com/commerce/php/development/versioning/). Het wiel niet opnieuw uitvinden.

Voor Adobe Commerce-moduleafhankelijkheden voert u de [module, versieafhankelijkheden](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) documentatie.

Gebruik de versiedefinitie niet in de `composer.json` bestand. Gebruik in plaats daarvan Git-tags voor versies. Zie [Composerversies en -beperkingen](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Waar moet u modules plaatsen die in een archiefbestand staan en niet via Composer?

Maak een Git-opslagplaats voor modules in een archief en host deze zelf. Elke Adobe Commerce-module heeft een `composer.json` bestand. Nadat u het in Git ontvangt en het met Privé Packagist synchroniseert, kunt u het met Composer installeren.

Wanneer u een nieuwe versie van het pakket ontvangt, uploadt u de code naar Git, codeert u deze en installeert u de nieuwe versie met Composer.

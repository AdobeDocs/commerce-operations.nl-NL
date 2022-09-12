---
title: Installatie van productiesysteem
description: Leer hoe u een productiesysteem instelt voor de toepassing Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Installatie van productiesysteem

Je kunt één productiesysteem hebben. Alle volgende waarden moeten waar zijn:

- Alle code van de Handel is in broncontrole in de zelfde bewaarplaats zoals de ontwikkeling en bouwsystemen
- Controleer of alle volgende elementen aanwezig zijn: _inbegrepen_ bij broncontrole:

   - `app/etc/config.php`
   - `generated` directory (en subdirectory&#39;s)
   - `pub/media` directory
   - `pub/media/wysiwyg` directory (en subdirectory&#39;s)
   - `pub/static` directory (en subdirectory&#39;s)

- Handel 2.2 of later moet worden geïnstalleerd en ingesteld voor [productiemodus](../bootstrap/application-modes.md#production-mode)
- De eigenaar en machtigingen van het bestandssysteem zijn ingesteld zoals beschreven in [Vereiste voor uw ontwikkeling, bouw, en productiesystemen](../deployment/prerequisites.md).

## Een productiemachine instellen

Een productiemachine instellen:

1. Na het installeren van Handel of het trekken van het uit broncontrole, login aan de productieserver als, of schakelaar aan [eigenaar van bestandssysteem](https://glossary.magento.com/magento-file-system-owner).
1. Maken `~/.ssh/.composer/auth.json` als u dat nog niet hebt gedaan.

   Maak de map:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Maken `auth.json` in die map.

   `auth.json` moet uw [verificatietoetsen](../../installation/prerequisites/authentication-keys.md).

   Hieronder volgt een monster:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Sla uw wijzigingen op in `auth.json`.
1. Kopiëren `<Commerce root dir>/app/etc/env.php` van uw ontwikkelingssysteem naar uw productiesysteem.
1. Openen `env.php` in een teksteditor en wijzig de vereiste waarden (bijvoorbeeld gegevens over databaseverbinding).
1. Voer de [`magento config:set`](../cli/set-configuration-values.md) of [`magento config:set-sensitive`](../cli/set-configuration-values.md) bevel om de waarden van om het even welke systeem-specifieke of gevoelige configuratiewaarden, respectievelijk te plaatsen.

   In de volgende sectie ziet u een voorbeeld.

## Configuratiewaarden instellen op uw productiesysteem

In deze sectie wordt besproken hoe u gevoelige waarden op uw productiesysteem kunt instellen met de `magento config:sensitive:set` gebruiken.

Om gevoelige waarden in te stellen:

1. Zoek een waarde die u wilt instellen met de opdracht [verwijzing naar gevoelige waarde](../reference/config-reference-sens.md).
1. Noteer het configuratiepad voor de instelling.
1. Meld u aan bij het productiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Ga naar de installatiemap Handel.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Als u bijvoorbeeld de waarde van de YouTube API-sleutel wilt instellen op `1234`, enter

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   U kunt ook als volgt een of meer waarden interactief instellen:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Voer desgevraagd een waarde in voor elke gevoelige instelling of druk op Enter om een waarde over te slaan en naar de volgende instelling te gaan.

1. Meld u aan bij de beheerder om te controleren of de waarde is ingesteld.
1. Zoek de instelling in Beheer.

   De sleutelinstelling voor de YouTube API bevindt zich bijvoorbeeld in **Winkels** > Instellingen > **Configuratie** > **Catalogus** > **Catalogus** > **Productvideo**.

   De instelling wordt weergegeven in Beheer en kan niet worden bewerkt. In de volgende afbeelding ziet u een voorbeeld.

   ![Gevoelige instelling in de beheerder](../../assets/configuration/sensitive-set.png)

---
title: Installatie van productiesysteem
description: Leer hoe u een productiesysteem instelt voor de Commerce-toepassing.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Installatie van productiesysteem

Je kunt één productiesysteem hebben. Alle volgende waarden moeten waar zijn:

- Alle Commerce-code bevindt zich in de broncontrole in dezelfde opslagplaats als de ontwikkelings- en bouwsystemen
- Zorg ervoor elk van het volgende _inbegrepen_ in broncontrole is:

   - `app/etc/config.php`
   - `generated` map (en submappen)
   - `pub/media` directory
   - `pub/media/wysiwyg` map (en submappen)
   - `pub/static` map (en submappen)

- Commerce 2.2 of later moet worden geïnstalleerd en voor [ productiemodus ](../bootstrap/application-modes.md#production-mode) worden geplaatst
- Het heeft bezit van het dossiersysteem en toestemmingen die zoals in [ worden besproken Vereiste voor uw ontwikkeling, bouwt, en productiesystemen ](../deployment/prerequisites.md).

## Een productiemachine instellen

Een productiemachine instellen:

1. Na het installeren van Commerce of het trekken van het uit broncontrole, login aan de productieserver als, of schakelaar aan, de eigenaar van het dossiersysteem.
1. Maak `~/.ssh/.composer/auth.json` als u dat nog niet hebt gedaan.

   Maak de map:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Maak `auth.json` in die map.

   `auth.json` moet uw [ authentificatietoetsen ](../../installation/prerequisites/authentication-keys.md) bevatten.

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

1. Sla uw wijzigingen op in `auth.json` .
1. Kopieer `<Commerce root dir>/app/etc/env.php` van uw ontwikkelingssysteem naar uw productiesysteem.
1. Open `env.php` in een teksteditor en wijzig de benodigde waarden (bijvoorbeeld gegevens over databaseverbinding).
1. Voer de opdracht [`magento config:set`](../cli/set-configuration-values.md) of [`magento config:set-sensitive`](../cli/set-configuration-values.md) uit om respectievelijk de waarden van systeemspecifieke of gevoelige configuratiewaarden in te stellen.

   In de volgende sectie ziet u een voorbeeld.

## Configuratiewaarden instellen op uw productiesysteem

In deze sectie wordt beschreven hoe u met de opdracht `magento config:sensitive:set` gevoelige waarden op uw productiesysteem instelt.

Om gevoelige waarden in te stellen:

1. Vind een waarde om het gebruiken van de [ gevoelige waardeverwijzing ](../reference/config-reference-sens.md) te plaatsen.
1. Noteer het configuratiepad voor de instelling.
1. Meld u aan bij het productiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Ga naar de Commerce-installatiemap.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Als u bijvoorbeeld de waarde van de YouTube API-sleutel wilt instellen op `1234` , voert u

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

   Bijvoorbeeld, wordt YouTube API zeer belangrijk het plaatsen gevestigd in **Opslag** > Montages > **Configuratie** > **Catalogus** > **Catalogus** > **Video van het Product**.

   De instelling wordt weergegeven in Beheer en kan niet worden bewerkt. In de volgende afbeelding ziet u een voorbeeld.

   ![ Gevoelige het plaatsen in Admin ](../../assets/configuration/sensitive-set.png)

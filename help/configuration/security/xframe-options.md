---
title: Klickjackingexplosies voorkomen
description: Voorkomen dat klikaanvallen worden misbruikt door de header 'X-Frame-Options' te gebruiken om paginaweergaven te beheren.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Klickjackingexplosies voorkomen

Verhinder [ Klikjacking ](https://owasp.org/www-community/attacks/Clickjacking) door [ x-kader-Opties ](https://datatracker.ietf.org/doc/html/rfc7034) HTTP- verzoekkopbal in verzoeken aan uw storefront te omvatten.

Met de header `X-Frame-Options` kunt u als volgt opgeven of een browser een pagina mag weergeven in een `<frame>` , `<iframe>` of `<object>` :

- `DENY`: de pagina kan niet in een kader worden weergegeven.
- `SAMEORIGIN`: (standaard) Pagina kan alleen worden weergegeven in een frame dat zich op dezelfde oorsprong bevindt als de pagina zelf.

>[!WARNING]
>
>De optie `ALLOW-FROM <uri>` is vervangen omdat deze niet meer wordt ondersteund door browsers die door Commerce worden ondersteund. Zie [ Browser verenigbaarheid ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Om veiligheidsredenen raadt Adobe ten zeerste aan de Commerce-winkel niet in een frame uit te voeren.

## Implementeren `X-Frame-Options`

Stel een waarde in voor `X-Frame-Options` in `<project-root>/app/etc/env.php` . De standaardwaarde wordt als volgt ingesteld:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Herdistribueren als wijzigingen in het `env.php` -bestand van kracht worden.

>[!TIP]
>
>Het bewerken van het `env.php` -bestand is veiliger dan het instellen van een waarde in de beheerfunctie.

## Uw instelling voor `X-Frame-Options` controleren

Als u de instelling wilt controleren, geeft u de HTTP-headers op een willekeurige winkelpagina weer. U kunt dit op verschillende manieren doen, bijvoorbeeld met een webbrowsercontrole.

In het volgende voorbeeld wordt curl gebruikt, die u kunt uitvoeren vanaf elke computer die via het HTTP-protocol verbinding kan maken met uw Commerce-server.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Zoek de `X-Frame-Options` -waarde in de kopteksten.

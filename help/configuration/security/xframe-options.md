---
title: Klickjackingexplosies voorkomen
description: Voorkomen dat klikaanvallen worden misbruikt door de header 'X-Frame-Options' te gebruiken om paginaweergaven te beheren.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Klickjackingexplosies voorkomen

Voorkomen [Klikjacking](https://owasp.org/www-community/attacks/Clickjacking) exploiteert door de [X-frame-opties](https://datatracker.ietf.org/doc/html/rfc7034) HTTP- aanvraagkopbal in verzoeken aan uw storefront.

De `X-Frame-Options` kunt u opgeven of een browser een pagina mag weergeven in een `<frame>`, `<iframe>`, of `<object>` als volgt:

- `DENY`: De pagina kan niet in een frame worden weergegeven.
- `SAMEORIGIN`: (standaard) Pagina kan alleen worden weergegeven in een frame dat zich op dezelfde oorsprong bevindt als de pagina zelf.

>[!WARNING]
>
>De `ALLOW-FROM <uri>` Deze optie is vervangen omdat browsers die dit ondersteunen deze niet meer ondersteunen. Zie [Browsercompatibiliteit](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Om veiligheidsredenen raadt de Adobe sterk aan om de handelsafront niet in een kader uit te voeren.

## Implementeren `X-Frame-Options`

Een waarde instellen voor `X-Frame-Options` in `<project-root>/app/etc/env.php`. De standaardwaarde wordt als volgt ingesteld:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Opnieuw implementeren voor wijzigingen in de `env.php` bestand dat van kracht wordt.

>[!TIP]
>
>Het is veiliger om de `env.php` -bestand in te stellen.

## Uw instelling controleren voor `X-Frame-Options`

Als u de instelling wilt controleren, geeft u de HTTP-headers op een willekeurige winkelpagina weer. U kunt dit op verschillende manieren doen, bijvoorbeeld met een webbrowsercontrole.

In het volgende voorbeeld wordt curl gebruikt, die u kunt uitvoeren vanaf elke computer die via het HTTP-protocol verbinding kan maken met de Commerce-server.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Zoek naar `X-Frame-Options` waarde in de kopteksten.

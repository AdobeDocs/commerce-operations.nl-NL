---
title: X-Frame-Options header
description: Gebruik X-Frame-Opties om paginaweergaven te besturen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# X-Frame-Options header

helpen voorkomen [Klikjacking](https://owasp.org/www-community/attacks/Clickjacking) misbruiken, hebben we een optie toegevoegd om de [X-frame-opties](https://datatracker.ietf.org/doc/html/rfc7034) HTTP- aanvraagkopbal in verzoeken aan uw storefront.

De `X-Frame-Options` koptekst biedt u de mogelijkheid op te geven of een browser een pagina in een `<frame>`, `<iframe>`, of `<object>` als volgt:

- `DENY`: De pagina kan niet in een kader worden weergegeven.
- `SAMEORIGIN`: (standaard) Pagina kan alleen worden weergegeven in een kader dat zich op dezelfde oorsprong bevindt als de pagina zelf.

>[!WARNING]
>
>De `ALLOW-FROM <uri>` Deze optie is vervangen omdat browsers die dit ondersteunen deze niet meer ondersteunen. Zie [Browsercompatibiliteit](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Om veiligheidsredenen, adviseert Adobe sterk tegen het runnen van de de opslagplaats van de Handel in een kader.

## Implementeren `X-Frame-Options`

Een waarde instellen voor `X-Frame-Options` in `<magento_root>/app/etc/env.php`. Hier volgt de standaardwaarde:

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>Het is veiliger om de `env.php` -bestand in te stellen.

## Uw instelling controleren voor `X-Frame-Options`

Als u de instelling wilt controleren, geeft u de HTTP-headers op een willekeurige winkelpagina weer. U kunt dit op verschillende manieren doen, bijvoorbeeld met een webbrowsercontrole.

In het volgende voorbeeld wordt curl gebruikt, die u kunt uitvoeren vanaf elke computer die via het HTTP-protocol verbinding kan maken met de Commerce-server.

Gebruik de volgende opdracht:

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Zoek naar `X-Frame-Options` waarde in de kopteksten.

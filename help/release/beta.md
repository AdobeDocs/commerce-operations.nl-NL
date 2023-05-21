---
title: Bèta-releases
description: Leer meer over de bètareleases van Adobe Commerce en hoe u hieraan kunt deelnemen.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Adobe Commerce bèta-releases

Vanaf juni 2023 zal Adobe openbare bèta&#39;s voor patchreleases (bètareleases) publiceren. De bètareleases zijn beschikbaar voor alle Adobe Commerce-klanten en -partners voordat ze algemeen beschikbaar zijn (GA) en omvatten oplossingen voor beveiliging, naleving, prestaties en hoge prioriteit.

>[!IMPORTANT]
>
>Bètareleases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Geen inhoud

Elke Adobe Commerce beta-release bevat alle wijzigingen die op de geplande releasedatum aan de Adobe Commerce Core-code zijn geleverd, inclusief maar niet beperkt tot de volgende functionele gebieden:

- Laatste beveiligingsoplossingen
- Prestatieverbeteringen
- GraphQL-verbeteringen
- Oplossingen voor algemene problemen
- Communautaire bijdragen
- Wijzigingen die vereist zijn ter ondersteuning van compatibiliteit met [Adobe Commerce-services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## Naamgevingsconventie en -schema

Adobe geeft twee keer per jaar bètapatches af. De eerste bètapatch wordt doorgaans drie maanden na de algemene beschikbaarheid van een nieuwe hoofdpatchrelease uitgebracht.

Beta-releasepakketten hebben een `-betaX` achtervoegsel. Voor de release van Adobe Commerce 2.4.7 beta wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-beta1`
- `2.4.7-beta2`

Zie de [releaseplanning](schedule.md) voor de lijst van aanstaande openbare bètareleasedatums.

## Voordelen van deelname

Hoe eerder u de code ziet die wij ontwikkelen, des te sneller kunt u uw technologie en handelaren voorbereiden op de komende upgrade.

Terwijl de dingen kunnen veranderen, zal het in dienst nemen van de bètaversies u toelaten beginnen te begrijpen waar in de codebase veranderingen gebeuren en beginnen met voorbereidingen voorafgaand aan de GA versiedatum.

## Toegang tot bètaversie

Adobe Commerce beta-releases worden op dezelfde manier gedistribueerd als elke andere Adobe Commerce patch-release: als Composer-metapakketten op `https://repo.magento.com`. De broncode is beschikbaar op [GitHub](https://github.com/magento/magento2).

Zie [Snelle start voor installatie van composer](../installation/composer.md) voor meer informatie .

## Melding van problemen

Adobe biedt de standaard Adobe Support Service voor bètareleases niet.

Volg onze [reguliere-uitgifterapporteringsstroom](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) op [GitHub](https://github.com/magento/magento2).

Onze interne teams zullen alle kritieke kwesties controleren die tegen de recentste bètaversie worden gemeld en hen voorrang geven om vóór de GA-releasedatum te worden opgelost.

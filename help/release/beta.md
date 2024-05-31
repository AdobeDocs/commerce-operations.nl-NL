---
title: Bèta-releases
description: Leer meer over de bètareleases van Adobe Commerce en hoe u hieraan kunt deelnemen.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d761bd089fbd2046e993d4652e9e0e2b3c4d2777
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Adobe Commerce bèta-releases

bètaprogramma&#39;s van Adobe Commerce zijn een manier voor handelaren om toegang te krijgen tot pre-releasefuncties en -code, feedback te geven en de toekomst van Adobe Commerce te begeleiden. Er zijn twee typen bètaprogramma&#39;s:

- Openbare bètaprogramma&#39;s zijn beschikbaar voor alle Adobe Commerce-klanten en -partners
- Private bèta: een private bètaprogramma kan goedkeuring vereisen op basis van kwalificatiecriteria om deel te kunnen nemen

>[!IMPORTANT]
>
>Bètareleases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Voordelen van deelname

Het krijgen van vroege toegang tot eigenschappen die de Adobe ontwikkelt verstrekt klanten en partners de capaciteit om terugkoppelen te verstrekken, productontwikkeling te vormen, en zich voor te bereiden om nieuwe mogelijkheden vóór algemene beschikbaarheid aan te nemen.

## Huidige bètaprogramma&#39;s

Zie de volgende secties voor een lijst van actieve bètaprogramma&#39;s.

### IBM Sterling Order Management System Integration (Private Bèta)

Met deze integratieversneller voor IBM Sterling Order Management kunnen Adobe Commerce-klanten aan de slag gaan met geavanceerde mogelijkheden voor orderbeheer, aangedreven door IBM Sterling OMS. Met deze integratie krijgen handelaren:
- Real-time zichtbaarheid in inventarisniveaus en nauwkeurige leveringsdatums voor uw klanten.
- Geautomatiseerde sourcing voor bestellingen op basis van configureerbare regels, zodat u uw uitvoeringsnetwerk en inventaris kunt optimaliseren.
- Een universele weergave van bestellingen tussen kanalen vanaf één dashboard, zodat uw supportteams de uitzonderlijke service kunnen leveren en uitzonderingen snel kunnen identificeren en afhandelen.
- Een getemplitste stroom van het terugkeerbeheer om terugkeerbeheer te vereenvoudigen.

Als u wilt deelnemen aan deze bètaversie, stuurt u een e-mailverzoek naar [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Gegevensverbinding en Audience Activation (openbare bètaversie)

Uitgebreide gegevensuitwisseling tussen Adobe Commerce en Adobe Experience Platform voor krachtigere persoonlijke ervaringen. Met deze mogelijkheid kunnen handelaren:
- Commerce-klantprofielen delen
- Aangepaste kenmerken maken
- Bekijk Commerce-inzichten in Real-Time CDP en Adobe Journey Optimizer
- Meerdere gegevenssets en gegevensstromen ondersteunen

Als u wilt deelnemen aan deze bètaversie, stuurt u een e-mailverzoek naar [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (openbare bètaversie)

Elke bètaversie van Adobe Commerce Foundation bevat alle wijzigingen die tegen de geplande releasedatum aan de Adobe Commerce-kerncode zijn geleverd, inclusief maar niet beperkt tot de volgende functionele gebieden:

- Laatste beveiligingsoplossingen
- Prestatieverbeteringen
- GraphQL-verbeteringen
- Oplossingen voor algemene problemen met kwaliteit
- Communautaire bijdragen
- Wijzigingen die vereist zijn ter ondersteuning van compatibiliteit met [Adobe Commerce-services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Naamgevingsconventie en -schema

Adobe geeft gewoonlijk twee keer per jaar bètapatches uit.

Beta-releasepakketten hebben een `-betaX` achtervoegsel. Voor de release van Adobe Commerce 2.4.7 beta wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-beta1`
- `2.4.7-beta2`

Zie de [releaseplanning](schedule.md) voor de lijst van aanstaande openbare bètareleasedatums.


#### Toegang tot bètaversie

Adobe Commerce beta-releases worden op dezelfde manier gedistribueerd als elke andere Adobe Commerce patch-release: zoals Composer-metapakketten op `https://repo.magento.com`. De broncode is beschikbaar op [GitHub](https://github.com/magento/magento2).

Zie [Snelle start voor installatie van composer](../installation/composer.md) voor meer informatie .

#### Melding van problemen

Adobe biedt de standaard Adobe Support Service voor bètareleases niet.

Volg onze [reguliere-uitgifterapporteringsstroom](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) op [GitHub](https://github.com/magento/magento2).

Onze interne teams zullen alle kritieke kwesties controleren die tegen de recentste bètaversie worden gemeld en hen voorrang geven om vóór de GA-releasedatum te worden opgelost.

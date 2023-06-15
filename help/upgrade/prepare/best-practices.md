---
title: Aanbevolen werkwijzen
description: Gebruik de door de Adobe aanbevolen aanbevolen aanbevolen werkwijze om het upgradeproces voor uw Adobe Commerce- en Magento Open Source-projecten te beheren.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Aanbevolen procedures voor upgraden

Dit onderwerp maakt een lijst van de acties u zou moeten nemen om de ingewikkeldheid van de bevordering van Adobe Commerce en Magento Open Source projecten te beheren. Uw team zou over verbeteringen moeten denken vanaf het ogenblik uw projectontwikkeling begint en door elke versie verdergaat. Door deze beste praktijken te volgen, zal het verbeteringsproces veel gemakkelijker, sneller, en goedkoper zijn.

>[!TIP]
>
>Deze aanbevelingen zijn gebaseerd op beste praktijken die worden ondersteund door bewijs voor de impact en doeltreffendheid ervan van partners, handelaren, Adobe-deskundigen en de gemeenschap.

## Welke gevolgen heeft een upgrade?

Het is belangrijk om de variabelen te begrijpen die de ingewikkeldheid van een verbetering bepalen. U moet deze variabelen aan het begin van elk project-niet enkel overwegen wanneer tijd is om te bevorderen. De ontwikkeling van een project is van essentieel belang om ervoor te zorgen dat toekomstige upgrades soepel zijn en dat u de vereiste inspanning kunt controleren om hen te voltooien.

De mate van moeite om uw Adobe Commerce-exemplaar te upgraden, is afhankelijk van de volgende factoren:

- **Hoe hebt u uw site gemaakt?** De hoeveelheid douanewerk en het aantal geïnstalleerde derdemodules beïnvloeden sterk de ingewikkeldheid van een verbetering. De kwaliteit van het aangepaste werk en de aangepaste modules kan bepalen of een upgrade probleemloos wordt uitgevoerd.

- **Overslaat u meerdere releases?** Door releases over te slaan wordt de volgende upgrade complexer en wordt het proces eenvoudiger en goedkoper.

- **Welk type van verbetering presteert u?** Een upgrade naar een kleine release (bijvoorbeeld van 2.3.x naar 2.4.0) is uitgebreider dan een upgrade tussen patchreleases (bijvoorbeeld van 2.4.2 naar 2.4.3). Beveiligingsupdates zijn het eenvoudigste type dat u kunt implementeren.

## Aanbevolen procedures voor het plannen van upgrades

Als u aan een project werkt dat reeds in productie is, zijn de verbeteringen een kans voor u om de kwaliteit van uw code en aanpassingen te verbeteren, en voor toekomstige verbeteringen te optimaliseren. De tijd die je vandaag investeert, is tijd bespaard op de lange termijn.

Als u meerdere sites beheert voor verschillende handelaren, kunt u het beste een basisinstantie hebben met de belangrijkste functies en aanpassingen die u normaal gebruikt. Gebruik deze basisinstantie als uw testsite voor het voltooien van een upgrade en voer deze op andere locaties uit. Deze praktijk geeft u de flexibiliteit om aangepaste modules voor verschillende klanten opnieuw te gebruiken en verbeteringen over projecten te vereenvoudigen.

Als uw project live is, raden we u aan een controle uit te voeren om de kwaliteit ervan te bepalen en te begrijpen hoe u het kunt verbeteren om upgrades efficiënter te maken.

### Ontwikkelen met upgrades in gedachten

Vanaf het moment dat u aan een project begint te werken, dient u te overwegen wat de gevolgen zullen zijn voor toekomstige upgrades van uw huidige werk. Volg altijd best practices voor Adobe Commerce-ontwikkeling zoals hier beschreven:

- [Best practices voor ontwikkeling](https://developer.adobe.com/commerce/php/best-practices/)
- [Codeerstandaarden](https://developer.adobe.com/commerce/php/coding-standards/)

Begin met het aannemen van het Adobe Commerce Extenability Platform, als u dit nog niet hebt gedaan. Met het platform kunt u processen efficiënt aanpassen, systemen integreren en nieuwe mogelijkheden implementeren terwijl u SaaS-achtige upgradebaarheid behoudt. De volgende functies zijn beschikbaar:

- **UI-uitbreidbaarheid**. Breid en evolueer uw storefront onafhankelijk van uw backend en middleware uit gebruikend [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **API-uitbreidbaarheid**. Gebruiken [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) om Web API laag uit te breiden door het model van grafiekgegevens te evolueren en lambdafuncties direct van de grafieklaag uit te voeren.

- **Adobe I/O middleware en diensten**. Sluit uw systemen aan op Adobe Commerce met behulp van Adobe middleware en een reeks toepassingsverbindingen die zijn gebaseerd op [Adobe I/O](https://www.adobe.io/). Bovendien kunt u de mogelijkheden van het kernplatform uitbreiden door het standaardgedrag met uw eigen bedrijfslogica te beschrijven die op Adobe I/O loopt.

### Upgrade plannen

Aangezien wij de mogelijkheden van Adobe Commerce voortdurend uitbreiden, is het essentieel dat u zich op de recentste beschikbare versie ontwikkelt en een verbeteringsstrategie in uw projectplannen bepaalt. Dit helpt u veilig, volgzaam, en bijgewerkt op de recentste verhogingen blijven die u toestaan om verkoop sneller te groeien, effectiever te werken, en uw concurrentie nu en in de toekomst voor te blijven.

Om u te helpen plannen en budgetteren voor upgrades, moet u onze [releaseplanning](https://devdocs.magento.com/release). De verbeteringstaken van het plan binnen de achterstand van uw team van tevoren. Doel om dit werk met GA te voltooien.

- Gebruik de pre-versieversie om over elke nieuwe versie te leren. De pre-versie is de Algemene code van de Beschikbaarheid die aan de verkopers van Adobe Commerce en alle partners twee weken vóór Algemene Beschikbaarheid beschikbaar is. Als u veelvoudige opslag hebt, gebruik pre-versie op uw basisopslag en verifieer dat uw douanemodules en thema&#39;s met het compatibel zijn.

- Controleer de [Controlelijst voor upgradeplan](https://support.magento.com/hc/en-us/articles/360057968951) voor Adobe Commerce om u te helpen uw upgrade te plannen.

- Plan voor verbeteringen aan het begin van het jaar. U moet een budget en middelen boeken om elke verbetering te voltooien. Herinner me, zou de verbeteringsinspanning van project aan project beduidend kunnen variëren. Gebruik uw ervaringen en kennis om een plan zo accuraat mogelijk te maken.

- Als uw upgrades meer moeite kosten dan wat wij hier beschrijven, adviseren wij u uw project te controleren en aanpassingen in uw milieu aan te brengen om het langetermijnonderhoud te verminderen.

### Upgrade uitvoeren

Upgrades moeten regelmatig en binnen een vooraf bepaalde begroting plaatsvinden. We raden u aan om vooraf goedgekeurde upgrades aan het begin van het jaar te plannen om ervoor te zorgen dat upgrades op tijd worden gepland en voltooid.

Evalueer het werk dat moet worden gedaan voor de upgrade:

- Controleer de [releaseopmerkingen](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) inzicht te krijgen in de reikwijdte en de gevolgen van de nieuwe versie.

- Gebruik de [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) om potentiële problemen te identificeren die in uw douanecode moeten worden opgelost alvorens te proberen om aan een nieuwere versie te bevorderen.

- Als u extensies van derden gebruikt, valideert u de compatibiliteit van deze extensies met de doelversie waarnaar u wilt upgraden.

### Post-upgrade testen

Het testen is de fase van een verbetering die de meeste tijd vereist. Dit proces moet daarom zo geautomatiseerd mogelijk zijn. U kunt profiteren van de belangrijkste testgereedschappen. De [Testhandleiding voor toepassingen](https://developer.adobe.com/commerce/testing/guide/) bevat details.

Gebruik een testomgeving om de upgrade te testen en te valideren voordat u overschakelt naar de productie.

Gebruik van een **onderhoudspagina**. Als u deze pagina vooraf voorbereidt, kunt u communiceren met uw klanten en hen op de hoogte stellen van het werk op de achtergrond. Deze pagina moet een paar minuten zichtbaar zijn, maar als er een probleem is, moet u deze mogelijk langer gebruiken. De juiste inhoud en het juiste ontwerp voor uw onderhoudspagina bieden uw gebruikers een goede ervaring, zelfs als uw winkel niet beschikbaar is.

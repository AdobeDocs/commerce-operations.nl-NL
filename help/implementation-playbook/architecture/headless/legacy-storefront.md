---
title: Gekoppelde opslagarchitectuur
description: Meer weten over wat een gekoppelde winkel betekent in de context van Adobe Commerce-architecturen zonder kop.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Gekoppelde (verouderde) Adobe Commerce-opslagarchitectuur

De huidige standaardimplementatieoptie voor de meeste commerciële klanten omvat:

- 100% functieondersteuning voor B2B en B2C
- Het de verwijzingsthema van de natuur (Luma) dat snel kan worden opgesteld/worden aangepast
- expertise op het gebied van implementatie van Mature SI-partners
- Volledig compatibel met handelsmogelijkheden zoals Page Builder of Staging &amp; Preview
- Brede compatibiliteit met extensies in Adobe Commerce Marketplace

![Diagram met een gekoppelde Adobe Commerce storefront architectuur](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Kons van verouderde opslagplaats

- **Niet zonder kop**—Alle onderdelen van de monolithische Adobe Commerce-toepassing. Geen scheiding van bedrijfslogica en processen tussen het front en het backend.

- **Geen PWA**—Hoewel het thema responsief is, liggen de prestaties van de site ver achter bij de PWA van de beste in-klasse.

- **Front-end architectuur (Adobe Commerce UI-componenten)**—Adobe Commerce/PHP-specialisten om voort te bouwen op verouderde winkels.

Voordat we in eindeloze opties geraken, beginnen we met de meer bekende winkelarchitectuur. Als er geen kop wordt losgekoppeld, zou dit de gekoppelde opslagarchitectuur zijn, die het meest wordt gezien bij onze Luma-demo&#39;s.

Dit is waar de storefront mogelijkheden strak met de kernhandelsdiensten worden geïntegreerd, niet door die laag van GraphQL API worden gescheiden. Er is dus veel bedrijfslogica gekoppeld aan dat thema. Deze aanpak is niet zonder kop, en het is geen PWA.

Dit is momenteel de gemeenschappelijkste optie koopt handelaars omdat het 100% eigenschapsteun met zowel B2B als B2C de mogelijkheden van de Handel heeft. De gemeenschap is er bekend mee, er is een volwassen ecosysteem van deskundigheid rond en het is in ruime mate compatibel met Adobe Commerce Marketplace-extensies.

Het ontbreekt echter aan de voordelen waar we eerder over hebben gesproken. Zonder scheiding van lagen, zijn er vele gebiedsdelen en potentiële punten van mislukking wanneer de veranderingen worden aangebracht. Het is niet zo presterend als een goed geïmplementeerde PWA en als een handelaar geen expertise heeft op het gebied van Adobe Commerce of PHP-ontwikkeling, zullen ze die bronnen moeten vinden.

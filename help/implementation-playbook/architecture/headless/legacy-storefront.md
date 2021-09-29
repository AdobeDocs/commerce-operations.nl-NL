---
title: Gekoppelde opslagarchitectuur
description: Meer informatie over wat een gekoppelde winkel betekent in het kader van Adobe Commerce-architecturen zonder kop.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Opslagarchitectuur gekoppelde (verouderde) Adobe Commerce

The current default deployment option for most commercial customers includes:

- 100% feature support across B2B &amp; B2C
- Het de verwijzingsthema van de natuur (Luma) dat snel kan worden opgesteld/worden aangepast
- Mature SI partner implementation expertise
- Fully compatible with commerce capabilities like Page Builder or Staging &amp; Preview
- Brede compatibiliteit met extensies in Adobe Commerce Marketplace

![Diagram met een gekoppelde Adobe Commerce-opslagarchitectuur](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Cons of legacy storefront

- **Niet zonder kop** - Alle onderdelen van de toepassing van de koophandel van de monolithische Adobe. No separation of business logic and processes between the frontend and the backend.

- **Geen PWA** - hoewel het thema ontvankelijk is, blijven de prestaties van de site ver achter bij de beste PWA.

- **Front-end architecture (Adobe Commerce UI components)**—Adobe Commerce/PHP specialists to build on legacy storefront.

Voordat we in eindeloze opties geraken, moeten we beginnen met de meer bekende archiefront-architectuur. If headless is decoupled, this would be the coupled storefront architecture, most commonly seen with our Luma demos.

This is where the storefront capabilities are tightly integrated with the core commerce services, not separated by that GraphQL API layer. Er is dus veel bedrijfslogica gekoppeld aan dat thema. Deze aanpak is niet zonder kop en is niet PWA.

Dit is momenteel de gemeenschappelijkste optie koopt handelaars omdat het 100% eigenschapsteun met zowel B2B als B2C de mogelijkheden van de Handel heeft. De gemeenschap is er bekend mee, er is een volwassen ecosysteem van deskundigheid om zich heen, en het is in ruime mate compatibel met Adobe Commerce Marketplace-uitbreidingen.

Het ontbreekt echter aan de voordelen waar we eerder over hebben gesproken. Zonder scheiding van lagen, zijn er vele gebiedsdelen en potentiële punten van mislukking wanneer de veranderingen worden aangebracht. It’s not as performant as a well-implemented PWA and if a merchant doesn’t have expertise in Adobe Commerce or PHP development, they will have to go find those resources.

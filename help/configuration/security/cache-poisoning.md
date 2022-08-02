---
title: Cachevergiftiging voorkomen
description: Leer hoe te om paginacachevergiftiging voor uw handels winkel te verhinderen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Cachevergiftiging voorkomen

In dit onderwerp wordt besproken hoe u kunt voorkomen [cachegeheugen](https://glossary.magento.com/cache) vergiftiging als u de Microsoft Internet Information Server (IIS)-webserver gebruikt. _Cachevergiftiging_ is een methode om de inhoud van het cachegeheugen te wijzigen en verschillende pagina&#39;s van dezelfde site op te nemen. Het is bijvoorbeeld mogelijk om een HTTP 404 (Niet gevonden) foutpagina te injecteren in plaats van een goedaardige pagina (bijvoorbeeld de [storefront](https://glossary.magento.com/storefront) homepage), die tot een potentiële ontkenning-van-dienst (Dos) kan leiden. De URL&#39;s van de kwaadaardige pagina worden in het cachegeheugen opgeslagen door Varnish of Redis, vandaar de naam _paginacache vergiftigt_.

Deze typen aanvallen kunnen moeilijk te detecteren zijn omdat ze niet resulteren in fouten in webserverlogbestanden.

Deze oplossing is op de volgende versies van de Handel van toepassing:

- 2.0.10 en hoger
- 2.1.2 en hoger

>[!INFO]
>
>Dit onderwerp is voorgenomen voor ervaren beheerders IIS.

## Beschrijving

De kwestie resulteert als URL herschrijft op de server IIS wordt toegelaten, en om het even welke volgende kopballen van HTTP worden veranderd alvorens het verzoek de Varnish of Redis in het voorgeheugen onderbrengende dienst bereikt:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Als deze koppen worden gewijzigd, worden de resulterende URL en de inhoud in het cachegeheugen opgeslagen, wat resulteert in potentiële kwetsbaarheden.

## Oplossing

Wij verstrekken de optie om de waarden van alle voorafgaande kopballen te verwijderen die op server IIS worden gebaseerd die voor plaatst `Enable_IIS_Rewrites`.

- Indien `Enable_IIS_Rewrites` is ingesteld op `0`, worden de waarden van de kopteksten verwijderd.
- Indien `Enable_IIS_Rewrites` is ingesteld op `1`, blijven de waarden van de kopteksten intact.

>[!WARNING]
>
>Als u `Enable_IIS_Rewrites` tot `1`, moet u niet toestaan dat de waarden van de voorafgaande kopballen worden gewijzigd alvorens het verzoek de IIS Webserver bereikt.

---
title: Cachevergiftiging voorkomen
description: Leer hoe u vergiftiging van de paginacache voor uw Commerce-winkel voorkomt.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Cachevergiftiging voorkomen

Dit onderwerp bespreekt hoe te om geheim voorgeheugenvergiftiging te verhinderen als u de Webserver van de Informatie van Microsoft Internet van de Server (IIS) gebruikt. _Positie van het Geheime voorgeheugen_ is een methode om geheim voorgeheugeninhoud te veranderen om verschillende pagina&#39;s van de zelfde plaats te omvatten. Het is bijvoorbeeld mogelijk om een HTTP 404 (Niet gevonden) foutenpagina in plaats van één of andere goedaardige pagina (bijvoorbeeld, de storefront homepage) te injecteren, die tot een potentiële ontkenning-van-dienst (DoS) kan leiden. De kwaadwillige pagina URLs wordt in het voorgeheugen ondergebracht door Varnish of Redis, vandaar de positie van het naamgeheime voorgeheugen __.

Deze typen aanvallen kunnen moeilijk te detecteren zijn omdat ze niet resulteren in fouten in webserverlogbestanden.

Deze oplossing is van toepassing op de volgende Commerce-versies:

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

Wij verstrekken de optie om de waarden van alle voorafgaande kopballen te verwijderen die op server IIS voor `Enable_IIS_Rewrites` worden gebaseerd.

- Als `Enable_IIS_Rewrites` is ingesteld op `0` , worden de waarden van de kopteksten verwijderd.
- Als `Enable_IIS_Rewrites` is ingesteld op `1` , blijven de waarden van de kopteksten intact.

>[!WARNING]
>
>Als u `Enable_IIS_Rewrites` aan `1` plaatst, moet u niet toestaan dat de waarden van de voorafgaande kopballen worden gewijzigd alvorens het verzoek de IIS Webserver bereikt.

---
title: Effectieve cacheplanning
description: Raadpleeg de aanbevolen benchmarks voor het in cache plaatsen om ervoor te zorgen dat uw site probleemloos wordt geladen.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Efficiënte caching plannen voor succes van e-commerce onder belasting

Voor het aanbieden van een winkelervaring onder druk is een goed geplande caching-strategie vereist. Hoewel in eerste instantie het verzoek van belanghebbenden uit het bedrijfsleven kan zijn om altijd realtime productgegevens aan klanten te presenteren, is dit geen optimaal gebruik van systeembronnen en zouden de gevolgen van de prestaties van de site van de eindgebruiker ruimschoots opwegen tegen de voordelen van het consistent tonen van real-time informatie.

De eerste stap in de caching-strategie moet daarom zijn om met de relevante belanghebbenden een matrix van aanvaardbare tijdstippen voor het in cache plaatsen van de verschillende gebieden van de site te definiëren, bijvoorbeeld:

| Cachegebied | Hoe vaak veranderen? | Effect indien verouderde inhoud wordt aangeboden vanuit cache | Acceptabele tijd-aan-levende (TTL) het in de cache plaatsen? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pagina&#39;s met HTML voor site-inhoud, bijgewerkt via CMS | Vaak | Laag | 1 dag |
| Sjabloonmedia/middelen voor site-inhoud - logo, CSS-ontwerp, afbeeldingen | Vaak | Laag | 1 week |
| Pagina&#39;s met productaanbiedingen (PLP) | Vaak | Medium | 1 dag |
| Pagina met productdetails (PDP) | Soms | Medium | 1 uur |
| Productcategorieën | Vaak | Medium | 1 dag |
| Prijzen | Vaak | Hoog | Geen cache |
| Inventaris/voorraad | Vaak | Hoog | Geen cache |
| Zoeken op site | De meeste gebruikers zijn uniek | Medium | De resultaten van het geheime voorgeheugen van hoogste 100 onderzoeksuitdrukkingen voor 1 dag |
| Afhandeling | Elke unieke gebruiker | Zeer hoog | Geen cache |
| Winkelwagentje | Elke unieke gebruiker | Zeer hoog | Geen cache |
| Betalingspagina&#39;s | Elke unieke gebruiker | Zeer hoog | Geen cache |

Met deze aanvankelijke planning voltooid, kan de technische configuratie beginnen op zijn plaats te worden gebracht om geheime voorgeheugens te vormen die op deze vereisten worden gebaseerd.

Zelfs als de inhoud wordt bijgewerkt en live binnen het caching TTL moet worden gemaakt, is het, in de meeste gevallen, mogelijk om de geheime voorgeheugens voor [ AEM dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) en [ Adobe Commerce ](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) geheim voorgeheugen selectief voor die inhoud te ontruimen, betekenend dat de urgente veranderingen onmiddellijk zullen worden weerspiegeld. Het proces rond handmatige cacheverwerking zou ook vooraf moeten worden gepland en worden getest zodat als er een behoefte is om een update op sommige inhoud manueel te dwingen, dan wordt het gedocumenteerd in een runtime van plaatsverrichtingen en duidelijk hoe en wie moet worden betrokken om dit te doen.

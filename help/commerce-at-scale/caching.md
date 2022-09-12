---
title: Effectieve cacheplanning
description: Raadpleeg de aanbevolen benchmarks voor het in cache plaatsen om ervoor te zorgen dat uw site probleemloos wordt geladen.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Efficiënte caching plannen voor succes van e-commerce onder belasting

Voor het aanbieden van een winkelervaring onder druk is een goed geplande caching-strategie vereist. Hoewel in eerste instantie het verzoek van belanghebbenden uit het bedrijfsleven kan zijn om altijd realtime productgegevens aan klanten te presenteren, is dit geen optimaal gebruik van systeembronnen en zouden de gevolgen van de prestaties van de site van de eindgebruiker ruimschoots opwegen tegen de voordelen van het consistent tonen van real-time informatie.

De eerste stap in de caching-strategie moet daarom zijn om met de relevante belanghebbenden een matrix van aanvaardbare tijdstippen voor het in cache plaatsen van de verschillende gebieden van de site te definiëren, bijvoorbeeld:

| Cachegebied | Hoe vaak veranderen? | Effect indien verouderde inhoud wordt aangeboden vanuit cache | Acceptabele tijd-aan-levende (TTL) het in de cache plaatsen? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pagina&#39;s met HTML voor site-inhoud, bijgewerkt via CMS | Vaak | Laag | 1 dag |
| Sjabloonmedia/middelen voor site-inhoud - logo, CSS-ontwerp, afbeeldingen | Vaak | Laag | 1 week |
| Pagina&#39;s met productaanbiedingen (PLP) | Vaak | Normaal | 1 dag |
| Pagina met productdetails (PDP) | Soms | Normaal | 1 uur |
| Productcategorieën | Vaak | Normaal | 1 dag |
| Prijzen | Vaak | Hoog | Geen cache |
| Inventaris/voorraad | Vaak | Hoog | Geen cache |
| Zoeken op site | De meeste gebruikers zijn uniek | Normaal | De resultaten van het geheime voorgeheugen van hoogste 100 onderzoeksuitdrukkingen voor 1 dag |
| Afhandeling | Elke unieke gebruiker | Zeer hoog | Geen cache |
| Winkelwagentje | Elke unieke gebruiker | Zeer hoog | Geen cache |
| Betalingspagina&#39;s | Elke unieke gebruiker | Zeer hoog | Geen cache |

Met deze aanvankelijke planning voltooid, kan de technische configuratie beginnen op zijn plaats te worden gebracht om geheime voorgeheugens te vormen die op deze vereisten worden gebaseerd.

Zelfs als de inhoud wordt bijgewerkt en live moet worden gemaakt in het cachegeheugen van TTL, is het in de meeste gevallen mogelijk om de caches voor de [AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) en [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) selectief in cache plaatsen voor die inhoud, wat betekent dat urgente wijzigingen onmiddellijk worden doorgevoerd. Het proces rond handmatige cacheverwerking zou ook vooraf moeten worden gepland en worden getest zodat als er een behoefte is om een update op sommige inhoud manueel te dwingen, dan wordt het gedocumenteerd in een runtime van plaatsverrichtingen en duidelijk hoe en wie moet worden betrokken om dit te doen.

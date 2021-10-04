---
title: Adobe Commerce Performance Optimization
description: Bereid uw Adobe Commerce-project voor om Adobe Experience Manager als CMS te gebruiken door sommige standaardmontages te veranderen.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe Commerce-prestatieoptimalisatie

## Geografische ligging van de infrastructuur voor AEM en Adobe handel

Om latentie tussen de AEM uitgever en Adobe te verminderen Commerce GraphQL wanneer het bouwen van pagina&#39;s, de aanvankelijke levering van de twee afzonderlijke infrastructuur binnen het zelfde Gebied van AWS (of van Azure) zou moeten worden ontvangen. De geografische plaats die voor beide wolken wordt gekozen zou ook het dichtst bij de meerderheid van uw klantenbasis moeten zijn, zodat de cliënt zijverzoeken GraphQL van een geografisch dichtbij plaats aan de meerderheid van uw klanten worden gediend.

## GrafiekQL caching in de Handel van de Adobe

Wanneer browser van de gebruiker of AEM uitgever Adobe Commerce GraphQL roept, zullen bepaalde vraag in het voorgeheugen onder worden gebracht
in Fastly. De vragen die in cache worden geplaatst zijn over het algemeen die die niet-persoonlijke gegevens bevatten en waarschijnlijk niet vaak zullen veranderen. Dit zijn bijvoorbeeld: categorieën, categorielijst en producten. Die die uitdrukkelijk niet in de cache worden geplaatst zijn die die regelmatig veranderen en als caching risico&#39;s voor persoonlijke gegevens en plaatsverrichtingen zoals vragen zoals winkelwagentje en customerPaymentTokens zou kunnen veroorzaken.

GraphQL staat u toe om veelvoudige vragen in één enkele vraag te maken. Het is belangrijk om op te merken dat als u zelfs één vraag specificeert die de Handel van de Adobe niet met vele anderen in het voorgeheugen onderbrengt die niet cacheable zijn, de Handel van Adobe het geheime voorgeheugen voor alle vragen in de vraag zal omzeilen. Dit zou door ontwikkelaars moeten worden overwogen wanneer het combineren van veelvoudige vragen om ervoor te zorgen potentieel cacheable vragen niet per ongeluk worden overgeslagen‡.

>[!NOTE]
>
> Voor meer informatie over cacheable en niet cacheable vragen, zie de Adobe Commerce [documentatie voor ontwikkelaars](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Vlakke tabel met catalogi

Het gebruik van platte tabellen voor producten en categorieën wordt afgeraden. Het gebruik van deze verouderde functie kan leiden tot prestatievermindering en indexeringsproblemen. Daarom moet de platte catalogus worden uitgeschakeld via de Adobe Commerce-beheerder in de winkelsectie. Sommige modules en aanpassingen van derden vereisen vlakke lijsten correct te functioneren - het wordt geadviseerd dat een evaluatie wordt gedaan om gevolgen en risico&#39;s te begrijpen verbonden aan het moeten vlakke lijsten gebruiken wanneer het kiezen om deze uitbreidingen of aanpassingen te gebruiken.

## Afscherming van de snelle oorsprong

Standaard is de optie Afscherming van de snelste oorsprong niet ingeschakeld. Het doel van de oorsprongsbescherming van Fastly is om het verkeer rechtstreeks naar de oorsprong van de Adobe Commerce te verminderen: wanneer een aanvraag wordt ontvangen, controleert een locatie met de snelste rand (of een &#39;aanvalspunt&#39; / POP) of inhoud in de cache is opgeslagen en levert deze. Als de inhoud niet in de cache wordt geplaatst, blijft de POP Schild controleren of deze daar in de cache wordt opgeslagen (als de inhoud eerder zelfs van een andere globale POP is aangevraagd, wordt deze in de cache geplaatst). Tot slot als niet cached op het Gebied POP, zal het slechts dan aan de server van de Oorsprong te werk gaan.

De snelle oorsprongsbescherming kan in uw Adobe Commerce admin van de configuratiesteun snel montages worden toegelaten. U zou een schermplaats moeten kiezen die aan uw Adobe Commerce- oorsprongscentrum voor de beste prestaties het dichtst bij is.

## Snelle optimalisatie van afbeeldingen

Als de functie Afbeelding snel afschermen is ingeschakeld, kunt u de functie Afbeelding snel optimaliseren ook activeren. Waar de beelden van de productcatalogus op de Handel van de Adobe worden opgeslagen, geeft deze dienst de capaciteit om al middelintensief middel, de verwerking van de beeldtransformatie van de productcatalogus aan snel en weg van de oorsprong van de Handel van de Adobe te offloaden. De reactietijden van de eindgebruiker zijn ook beter voor de laadtijden van de pagina, aangezien de beelden bij de randplaats worden getransformeerd die latentie elimineert door het aantal verzoeken terug naar de oorsprong van de Adobe Handel terug te verminderen.

U kunt de functie voor het snel optimaliseren van afbeeldingen inschakelen door de functie voor het snel optimaliseren van afbeeldingen in de beheerdersconfiguratie in te schakelen, maar alleen nadat het oorspronkelijke schild is geactiveerd. Meer informatie over configuraties voor Fastly Image optimization is beschikbaar in de [documentatie voor ontwikkelaars](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) van de Handel van de Adobe.

![Screenshot van de instellingen voor snelle optimalisatie van afbeeldingen in de Admin van de Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Ongebruikte modules uitschakelen

Als het runnen van de Koophandel van Adobe hoofdloos, slechts het dienen van verzoeken door het eindpunt GraphQL en geen front-end opslagpagina&#39;s rechtstreeks van de Handel van Adobe worden gediend, dan worden vele modules overtollig en niet gebruikt. Door ongebruikte modules onbruikbaar te maken, wordt uw de codebasis van de Handel van de Adobe kleiner, minder complex en daarom kon prestatiesverbeteringen aanbieden. Het onbruikbaar maken modules op de Handel van Adobe kan worden beheerd gebruikend composer. Welke modules die kunnen worden onbruikbaar gemaakt zouden van de vereisten voor uw plaats afhangen, en zodat kan geen geadviseerde lijst worden gegeven aangezien het voor de implementatie van elke klant van de Handel van Adobe specifiek zou zijn.

## Activering van MySQL- en Redis-verbinding

Standaard worden MySQL- en Redis Slave-verbindingen niet geactiveerd in Adobe Commerce op cloud. Dit komt doordat deze instellingen alleen geschikt zijn voor klanten die zeer hoge belasting verwachten. De Cross-AZ (cross-Availability Zones)-latentie is hoger wanneer slave-verbindingen zijn geactiveerd en deze instelling verlaagt in feite de prestaties van een Adobe Commerce op cloudinstantie als de instantie alleen een normaal laadniveau ontvangt.

Als de instantie van de Handel van de Adobe extreme lading verwacht, dan het activeren van master-slave voor MySQL en Redis zal met prestaties helpen door de lading op het Gegevensbestand MySQL of Redis over verschillende knopen uit te spreiden.

Als richtlijn geldt dat in omgevingen met een normale belasting de prestaties bij Slave Connections met 10-15% worden vertraagd. Maar in clusters met een zware belasting en veel verkeer is er een prestatieverhoging van ongeveer 10-15%. Daarom is het belangrijk om test uw milieu met verwachte verkeersniveaus te laden om te beoordelen of dit het plaatsen voor uw prestatiestijden onder lading nuttig zou zijn.

Als u slave-verbindingen voor mysql en opnieuw wilt in-/uitschakelen, moet u het `.magento.env.yaml`-bestand bewerken en het volgende opnemen:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Voor geschaalde architectuur (gesplitste architectuur - zie hieronder), zouden de slave verbindingen van Redis niet moeten worden toegelaten, aangezien dit fouten zal veroorzaken om te verschijnen. In het geval van een gesplitste architectuur, wordt het geadviseerd in plaats daarvan L2 caching voor Redis uit te voeren.

## Naar een Adobe Commerce op cloudgeschaalde (gesplitste) architectuur

Als na alle bovenstaande configuraties, de resultaten van de ladingstest of de analyse van de prestaties van de levende infrastructuur nog erop wijzen dat de ladingsniveaus aan de Handel van de Adobe van een niveau zijn dat constant cpu en andere systeemmiddelen in kaart brengt, dan zou een beweging aan een geschraapte (gespleten) architectuur moeten worden overwogen.

Met een standaard Pro architectuur, zijn er 3 knopen, elk waarvan een volledige technologiestapel bevat. Door om te zetten in de gespleten rijarchitectuur, verandert dit in een minimum van 6 knopen: 3 waarvan Elasticsearch, MariaDB, Redis en andere kerndiensten; de andere 3 voor de verwerking van webverkeer bevatten phpfm en NGINX. Er zijn meer schaalmogelijkheden met gesplitste lagen: kernknooppunten met databases kunnen verticaal worden geschaald; de Webknopen kunnen horizontaal en verticaal worden geschraapt, die een grote hoeveelheid flexibiliteit geven om infrastructuur op bestelling voor vastgestelde periode van hoge ladingsactiviteit en op knopen uit te breiden waar de extra middelen nodig zijn.

Als het besluit is genomen om over te schakelen op een gesplitste laagarchitectuur vanwege de hoge verwachtingen ten aanzien van de belasting van uw site, moet een gesprek worden gevoerd met uw Customer Success Manager over de stappen om dit mogelijk te maken.

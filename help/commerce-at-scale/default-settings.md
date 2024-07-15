---
title: Optimalisatie van Adobe Commerce-prestaties
description: Bereid uw Adobe Commerce-project voor om Adobe Experience Manager als CMS te gebruiken door enkele standaardinstellingen te wijzigen.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Optimalisatie van Adobe Commerce-prestaties

## Geografische locatie van AEM- en Adobe Commerce-infrastructuur

Om de vertragingen tussen de AEM uitgever en Adobe Commerce GraphQL bij het bouwen van pagina&#39;s te verminderen, zou de aanvankelijke levering van de twee afzonderlijke infrastructuur binnen zelfde AWS (of Azure) Gebied moeten ontvangen. De geografische locatie die voor beide clouds is gekozen, moet zich ook het dichtst bij het merendeel van uw klantenbestand bevinden, zodat GraphQL-verzoeken aan de clientzijde worden bediend vanaf een locatie die geografisch dicht bij de meeste van uw klanten ligt.

## GraphQL caching in Adobe Commerce

Wanneer de browser of AEM uitgever van de gebruiker Adobe Commerce GraphQL roept, zullen bepaalde vraag in het voorgeheugen onder worden gebracht
in Fastly. De vragen die in het voorgeheugen worden opgeslagen zijn over het algemeen die die niet persoonlijke gegevens bevatten en zullen waarschijnlijk niet vaak veranderen. Dit zijn bijvoorbeeld: categorieën, categoryList en producten. Die die uitdrukkelijk niet in de cache worden geplaatst zijn die die regelmatig veranderen en als caching risico&#39;s voor persoonlijke gegevens en plaatsverrichtingen zoals vragen zoals winkelwagentje en customerPaymentTokens zou kunnen veroorzaken.

GraphQL staat u toe om veelvoudige vragen in één enkele vraag te maken. Het is belangrijk om op te merken dat als u zelfs één vraag specificeert die Adobe Commerce niet met vele anderen in het voorgeheugen onderbrengt die niet cacheable zijn, Adobe Commerce het geheime voorgeheugen voor alle vragen in de vraag zal omzeilen. Dit zou door ontwikkelaars moeten worden overwogen wanneer het combineren van veelvoudige vragen om ervoor te zorgen potentieel cacheable vragen niet per ongeluk worden overgeslagen‡.

>[!NOTE]
>
> De verdere informatie over cacheable en niet-cacheable vragen, zie de [ de ontwikkelaarsdocumentatie van Adobe Commerce ](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Vlakke tabel met catalogi

Het gebruik van platte tabellen voor producten en categorieën wordt afgeraden. Het gebruik van deze verouderde functie kan leiden tot prestatievermindering en indexeringsproblemen. Daarom moet de platte catalogus worden uitgeschakeld via de Adobe Commerce-beheerder, in de winkelsectie. Sommige modules en aanpassingen van derden vereisen vlakke lijsten correct te functioneren - het wordt geadviseerd dat een evaluatie wordt gedaan om gevolgen en risico&#39;s te begrijpen verbonden aan het moeten vlakke lijsten gebruiken wanneer het kiezen om deze uitbreidingen of aanpassingen te gebruiken.

## Afscherming van de snelle oorsprong

Standaard is de optie Afscherming van de snelste oorsprong niet ingeschakeld. Het doel van de oorspronkelijke afscherming van Fastly is om het verkeer rechtstreeks naar de Adobe Commerce-oorsprong te reduceren: wanneer een aanvraag wordt ontvangen, controleert een locatie met de snelste rand (of een &#39;aanvalspunt&#39;/POP) op inhoud in de cache en levert deze. Als de inhoud niet in de cache wordt geplaatst, blijft de POP Schild controleren of deze daar in de cache wordt opgeslagen (als de inhoud eerder zelfs van een andere globale POP is aangevraagd, wordt deze in de cache geplaatst). Tot slot als niet cached op het Gebied POP, zal het slechts dan aan de server van de Oorsprong te werk gaan.

De snelle oorsprongsbeveiliging kan worden ingeschakeld in uw Adobe Commerce-beheerinstellingen voor snelle back-endconfiguratie. Kies een schermlocatie die het dichtst bij uw Adobe Commerce-datacenter ligt voor de beste prestaties.

## Snelle optimalisatie van afbeeldingen

Als de functie Afbeelding snel afschermen is ingeschakeld, kunt u de functie Afbeelding snel optimaliseren ook activeren. Wanneer afbeeldingen uit productcatalogi op Adobe Commerce worden opgeslagen, biedt deze service de mogelijkheid om alle hulpbronnenintensieve verwerking van afbeeldingen in productcatalogi snel en van Adobe Commerce af te voeren. De responstijden van de eindgebruiker zijn ook beter voor de laadtijden van de pagina, aangezien afbeeldingen worden getransformeerd op de randlocatie, waardoor latentie wordt voorkomen doordat het aantal aanvragen wordt teruggebracht naar de Adobe Commerce-oorsprong.

U kunt de functie voor het snel optimaliseren van afbeeldingen inschakelen door de functie voor het snel optimaliseren van afbeeldingen in de beheerdersconfiguratie in te schakelen, maar alleen nadat het oorspronkelijke schild is geactiveerd. Meer details op configuraties voor de Snelle optimalisering van het Beeld zijn beschikbaar in de Adobe Commerce [ ontwikkelaarsdocumentatie ](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![ Schermafbeelding van de Snelle instellingen voor beeldoptimalisatie in Adobe Commerce Admin ](../assets/commerce-at-scale/image-optimization.svg)

## Ongebruikte modules uitschakelen

Als het runnen van Adobe Commerce headless, slechts het dienen van verzoeken door het eindpunt van GraphQL en geen front-end opslagpagina&#39;s direct van Adobe Commerce worden gediend, dan worden vele modules overtollig en niet gebruikt. Door ongebruikte modules uit te schakelen, wordt uw Adobe Commerce-codebasis kleiner, minder complex en kan deze daarom prestatieverbeteringen bieden. Het onbruikbaar maken modules op Adobe Commerce kan worden beheerd gebruikend composer. Welke modules die kunnen worden onbruikbaar gemaakt zouden van de vereisten voor uw plaats afhangen, zodat kan geen geadviseerde lijst worden gegeven aangezien het voor de implementatie van elke klant van Adobe Commerce specifiek zou zijn.

## Activering van MySQL- en Redis-verbinding

MySQL- en Redis Slave-verbindingen worden standaard niet geactiveerd in Adobe Commerce in de cloud. Dit komt doordat deze instellingen alleen geschikt zijn voor klanten die zeer hoge belasting verwachten. De Cross-AZ (cross-Availability Zones)-latentie is hoger wanneer slave-verbindingen zijn geactiveerd en deze instelling vermindert de prestaties van een Adobe Commerce op een cloudinstantie voor het geval dat de instantie alleen een normaal laadniveau ontvangt.

Als de instantie van Adobe Commerce extreme lading verwacht, dan zal het activeren van meester-slave voor MySQL en Redis met prestaties helpen door de lading op het Gegevensbestand MySQL of Redis over verschillende knopen uit te spreiden.

Als richtlijn geldt dat in omgevingen met normale belasting, bij het inschakelen van Slave Connections de prestaties met 10-15% afnemen. Maar in clusters met een zware belasting en veel verkeer is er een prestatieverhoging van ongeveer 10-15%. Daarom is het belangrijk om test uw milieu met verwachte verkeersniveaus te laden om te beoordelen of dit het plaatsen voor uw prestatiestijden onder lading nuttig zou zijn.

Als u slave-verbindingen voor mysql en opnieuw wilt in-/uitschakelen, moet u het `.magento.env.yaml` -bestand bewerken en de volgende elementen toevoegen:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Voor geschaalde architectuur (gesplitste architectuur - zie hieronder), zouden de slave verbindingen van Redis niet moeten worden toegelaten, aangezien dit fouten zal veroorzaken om te verschijnen. In het geval van een gesplitste architectuur, wordt het geadviseerd in plaats daarvan L2 caching voor Redis uit te voeren.

## Naar een Adobe Commerce gaan op geschaalde (gesplitste) cloudarchitectuur

Als na alle bovenstaande configuraties de resultaten van de belastingstest of de analyse van de prestaties van de live infrastructuur nog steeds aangeven dat de belastingsniveaus voor Adobe Commerce van een niveau zijn dat de CPU en andere systeembronnen consistent maximaliseert, moet een verschuiving naar een geschaalde (gesplitste) architectuur worden overwogen.

Met een standaard Pro architectuur, zijn er 3 knopen, elk waarvan een volledige technologiestapel bevat. Door om te zetten in gesplitste rijarchitectuur, verandert dit in een minimum van zes knopen: 3 waarvan Elasticsearch, MariaDB, Redis en andere kerndiensten bevatten; de andere 3 voor verwerking van Webverkeer bevatten phpfm en NGINX. Er zijn meer schaalmogelijkheden met gesplitste lagen: kernknooppunten met databases kunnen verticaal worden geschaald; webknooppunten kunnen horizontaal en verticaal worden geschaald, waardoor een grote mate van flexibiliteit wordt geboden om de infrastructuur op aanvraag uit te breiden voor een bepaalde periode van activiteit met hoge belasting en voor knooppunten waar extra bronnen nodig zijn.

Als een besluit is genomen om op een gespleten rijarchitectuur wegens zware ladingsverwachtingen voor uw plaats over te schakelen, dan zou een bespreking met uw Team van de Rekening van de Adobe op de stappen moeten worden betrokken om dit toe te laten.

---
title: Tips voor Adobe Commerce-prestaties die zichzelf hosten
description: Leer over zelf-ontvangende prestatiestips ideeën en concepten en beste praktijken om te overwegen.
landing-page-description: Leer enkele tips over prestaties en zaken die u in overweging kunt nemen wanneer u Adobe Commerce op uw eigen computer host.
short-description: Leer strategieën en prestatietips om zelf Adobe Commerce te hosten.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Tips voor Adobe Commerce-prestaties die zichzelf hosten

Het gebruik van een flexibel en krachtig e-commerceplatform betekent niet dat u prestaties moet opofferen. Sinds de aanvang van Adobe Commerce zijn er talrijke verbeteringen aangebracht in de kerntoepassing. In versie 2.5.4 heeft het technische team van Adobe Commerce een settest uitgevoerd om de toepassing te benchmarken. De testresultaten hebben aangetoond dat Adobe Commerce in staat is om een grote catalogus van meer dan 240 miljoen SKU&#39;s af te handelen, API-aanvraagtijden zijn uitzonderlijk gemiddeld 300 ms, en het aantal per uur geplaatste paginaweergaven en bestellingen is fenomenaal en komt voor in 2 miljoen paginaweergaven en 208.000 bestellingen per uur.

Bekijk de meest recente benchmarkresultaten per kop naar [Experience League - Adobe Commerce - Afspeelboek implementatie - Benchmarks](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Volg deze standaarden wanneer u aanpassingen en extra complexiteit toevoegt aan uw project om de zaken zo optimaal mogelijk te houden.

De volgende secties behandelen onderwerpen en adviseren voor hoe te om uw zelf-ontvangende implementatie te optimaliseren.

## Varnish

Varnish is HTTP reverse-proxy met cache. Hoe gecompliceerd dat ook lijkt, het resultaat is snelle reacties om ervoor te zorgen dat de verzoeken sneller worden teruggegeven dan als het punt van de bron moest halen. Als u een Adobe Commerce-site uitvoert zonder een versie van Varnish, worden de pagina&#39;s langzamer geladen en worden andere belangrijke gegevens gebruikt. Varnish kan een beetje moeilijk zijn om op te zetten en te leiden zelf, nochtans hebben wij dit onderwerp in Experience League [Varnish configureren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} om meer inzicht te krijgen in het gebruik ervan met Adobe Commerce. Een alternatief is het gebruik van een cloudgebaseerde oplossing. Hoewel er veel te overwegen zijn, is Fastly gekozen als de oplossing voor de Adobe Commerce over de cloud. Het is een versie van Fastly, op wolken gebaseerd, die VCLs en vele facetten van vernis gebruikt.

Het vinden van een oplossing die het beste aansluit bij uw toepassing, configuratie, budget en technische vaardigheden is moeilijk. Met een optie op basis van cloud&#39;s verdwijnen alle harde onderdelen, voor zover het beheer, de configuratie, de servers en andere infrastructuurcomponenten in aanmerking worden genomen. Het werd door de Adobe Commerce in het cloudteam gekozen als oplossing vanwege de prestaties, schaalbaarheid, doorvoer en vele andere belangrijke meetgegevens.

Door een goede oplossing voor uw project betreffende Varnish te kiezen, plaatst u opstelling voor de beste prestaties voor uw klanten en bewaart de handelstoepassing van het werken harder dan het moet.

## CDN

Naast Varnish die een waardevol goed voor uw Adobe Commerce-project zijn, is daarna een CDN. Samen met uw Varnish kan een CDN caching instanties voor uw CSS verstrekken, pagina activa zoals beelden helpen bandbreedte verminderen die aan uw toepassing van Adobe Commerce komt. Het kan GraphQL-antwoorden in de cache plaatsen om de voordelen van een Adobe Commerce-site zonder kop te verbeteren. Sommige CDN&#39;s bieden optimalisatie van afbeeldingen, een webtoepassingsfirewall en andere functies.

Adobe Commerce op cloud koos ervoor om Fastly te gebruiken voor de Varnish cache, maar ook als CDN. Deze enkele oplossing biedt een groot aantal functies die een geweldige ervaring bieden voor de Adobe Commerce op cloudklanten. U kunt het Snelle overzicht van de diensten in Experience League lezen [Overzicht van snelle services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Een CDN biedt geoptimaliseerde en veilige leveringsinhoud voor het Adobe Commerce-project. Als dit geen vereist onderdeel voor uw project is, moet u dit in overweging nemen omdat uw site steeds groter wordt en het aantal bezoekers toeneemt. Door een CDN op te geven, kunt u het toevoegen van extra hardware aan de infrastructuur vertragen of de bestaande infrastructuur schalen vanwege de belasting die uit elke aanvraag is verwijderd.

## Modules uitschakelen

Het onbruikbaar maken van een module die ongebruikt is zou moeten worden overwogen, maar niet lichtjes genomen. Deze techniek vermindert sommige overhead en verwerkingstijd voor sommige verzoeken, maar er zijn bijwerkingen die in overweging moeten worden genomen. Er zijn vaak tijden, wanneer een ontwikkelaar veronderstelt dat een module wanneer het creëren van functionaliteit beschikbaar is. Dit is vaak veilig, tenzij ze bepaalde klassen gebruiken die zijn gevonden in een module die is uitgeschakeld.

Het uitschakelen van een module zoals de native nieuwsbrief is een veel voorkomende gebeurtenis. Dit geldt met name wanneer de eigenaar van de winkel een extern bedrijf heeft dat de nieuwsbrief van de eigenaar beheert. Waar dit een kwestie kan zijn wanneer een derdemodule wordt geïnstalleerd en om een bepaalde reden besloten zij om een klasse van nieuwsbrief te gebruiken. Deze toevallige afhankelijkheid zal waarschijnlijk tijdens één of andere aanvankelijke installatie en het testen worden gevangen, maar dan wordt u gedwongen om te beslissen of u deze derdemodule wilt behouden, nieuwsbrief toelaten en dan regressietest de plaats die op om het even welk oneven gedrag zoekt dat wordt geïntroduceerd. Of vindt u een vervanging voor die derdemodule. Beide besluiten hebben risico&#39;s, tijd en mogelijk fouten.

Voordat u ongebruikte modules uitschakelt, moet u ervoor zorgen dat u geen tests zoals eenheidstests hebt, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} load tests, of API verzoeken die kunnen worden beïnvloed.

## Adobe Commerce- en PHP-coderingsstandaarden moeten worden gevolgd voor elke pull-aanvraag

Adobe Commerce heeft een set [Codeerstandaarden](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Deze hulp zorgt ervoor dat een gelijkaardig patroon, een stijl, en een verwacht ontwerp ongeacht het type van softwareontwikkeling worden gevolgd. Dit is een vereiste wanneer we bijdragen aan de Adobe Commerce-codebase. Maar als u ervoor kiest om deze methode voor aangepaste ontwikkeling te volgen, wordt een stevige hoeksteen voor alle ontwikkelaars, zowel de huidige als de toekomstige. Wanneer u alle pull-aanvragen nodig hebt om een codestandaard door te geven, zorgt u ervoor dat iedereen dezelfde consistente ontwikkelingspatronen kan begrijpen en verwachten.

De andere basis die wordt gebruikt bij de Adobe Commerce-coderingsnormen is PHP-basiscoderingsnormen. In de ontwikkelaarsgidsen moet duidelijk worden gedefinieerd welke standaarden u moet volgen en welke afwijkingen acceptabel zijn. Een fallback dient echter plaats te vinden op de algemeen bewaarde gids die te vinden is op [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Een vaste houding ten aanzien van de volgende PSR-1 en PSR-12. Ervoor zorgen dat de ontwikkelaars die aan het project bijdragen deze hulp volgen ervoor zorgen dat er geen vreemd gestructureerde dossiers en patronen zijn. Dit helpt ook ervoor te zorgen dat toekomstige ontwikkelaars de code die zij controleren snel kunnen lezen en begrijpen. Hoe dichter u deze patronen en coderingsnormen volgt, hoe beter leesbaar en sneller de toekomstige ontwikkelingsinspanningen moeten zijn.

## Laadtests uitvoeren na elke implementatie

Het uitvoeren van een belastingtest na elke inzet kan overdreven lijken. Als deze methodologie echter wordt gevolgd, kan de mogelijkheid voor nieuw geïntroduceerde functies die een afname in prestaties veroorzaken, worden gevolgd en beperkt.

Naast het detecteren van de verslechtering van de prestaties van nieuwe code, kan het hebben van een historische referentie van de belangrijkste meetgegevens van uw site u inzicht verschaffen wanneer een nieuw gereedschap of een andere infrastructuur is ingeschakeld. Voordat u bijvoorbeeld het hostingbedrijf betaalt om de grootte van uw omgeving aan te passen en u de verwachte prestatieverhoging krijgt, kunt u een testomgeving instellen met de nieuwe configuraties en een laadtest uitvoeren om te zien wat het werkelijke resultaat zou zijn.

Deze tests kunnen worden geautomatiseerd en een deel van uw I/CD pijpleiding. Daarom kunt u ook regels hebben die de resultaten nemen en de samenvoeging van functies mogelijk blokkeren als er te veel van de norm wordt afgeweken. Het aantal gevallen waarin deze gegevens worden gebruikt, is onbeperkt, maar zonder dit proces te starten, realiseert u mogelijk nooit het potentieel ervan.

Adobe Commerce heeft een goede beschrijving van dit onderwerp in Experience League [Tips voor het testen van prestaties](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}

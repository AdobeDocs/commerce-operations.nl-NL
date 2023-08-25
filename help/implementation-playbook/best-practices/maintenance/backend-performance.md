---
title: Optimaliseer de prestaties van de backend
description: Meer informatie over het optimaliseren van de backendprestaties van Adobe Commerce-sites.
badge: label="Bijgedragen door objectbron" type="Informative" url="https://objectsource.co.uk/" tooltip="objectbron"
role: Admin, User, Developer
feature: Best Practices
source-git-commit: 2416357d8cacb5627fd24f92b16c2d9839f91082
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor het optimaliseren van prestaties in het achterste segment

Dit onderwerp schetst beste praktijken voor het onderzoeken van en het optimaliseren van de achtergrondprestaties van de plaatsen van Adobe Commerce met een nadruk op gegevensbestandoptimalisering en het testen. De ontwikkelaars kunnen deze informatie gebruiken om de unieke context van elk project van de Handel te onderzoeken en kansen te identificeren om backendconfiguratie en verrichtingen te optimaliseren om plaatsprestaties te verbeteren.

>[!NOTE]
>
>Recommendations en voorbeelden zijn geïnspireerd door processen die de objectsource volgt in real-world clientcontracten om geavanceerde Adobe Commerce-sites op schaal te leveren.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## De database optimaliseren voor betere prestaties

De optimalisering van het gegevensbestand is een zeker-brandwijze manier om de gebruikerservaring te verbeteren en verkoop te verhogen. Wanneer u de database optimaliseert, de ruggengraat van een Commerce-site, kunt u langzame websiteprestaties voorkomen en lange laadtijden voorkomen die wrijving voor klanten veroorzaken.

### Stresstests

De periodes van het hoge verkeer zoals de Zwarte Vrijdag eisen dat de plaatsen van de Handel enorme verkeersvolumes behandelen. Ter voorbereiding op dergelijke gebeurtenissen is het van essentieel belang dat stresstests worden uitgevoerd om te begrijpen hoe een site werkt onder exponentiële stijgingen van de belasting.

U kunt GTmetrix gebruiken voor stresstests. Bereidheid van de plaats van de pagina voor ladingsverhogingen door GTmetrix te vormen om normaal bezoekersgedrag en acties te herhalen en te vermenigvuldigen. Dan, stel tests in werking om kwesties te identificeren en op te lossen die prestaties en plaatsbeschikbaarheid tijdens belangrijke het winkelen gebeurtenissen zouden kunnen beïnvloeden.

Meer informatie over het voorbereiden van Commerce-projecten voor periodes met veel verkeer:

- [Gereedheid voor feestdagen](https://experienceleague.adobe.com/docs/events/mbi-webinars-recordings/2021/holiday-readiness.html)
- [Winkelanalyse vakantie](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Toename piekcapaciteit](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Laden testen

U kunt GTmetrix of een gelijkaardig hulpmiddel ook gebruiken om de projecten van de Handel van de test te laden. Als voorloper van stresstests is het testen van de belasting een essentiële praktijk voor grootschalige, grote verkeerslocaties. Vermijd onverwachte uitvallen van de plaats, gefrustreerde klanten, en financiële verliezen door kwesties te voorzien en te verlichten die plaatsprestaties onder pieklasten beïnvloeden.

Gebruik GTmetrix om zwaar verkeer te simuleren en plaatsprestaties te analyseren om duidelijke informatie over plaatscapaciteit te krijgen. Deze analyse helpt knelpunten op te sporen en aan te pakken en mogelijkheden te identificeren om te optimaliseren, zodat handelsplaatsen effectief kunnen werken onder verhoogde belasting.

Meer informatie over het testen van Adobe Commerce-projecten:

- [Testinstructies](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (cloudinfrastructuur)
- [Toepassingen testen](https://developer.adobe.com/commerce/testing/guide/)

### Prestatieproblemen identificeren en oplossen

Prestatieproblemen aanpakken met behulp van verschillende tools, zoals New Relic en Observation voor Adobe Commerce, om knelpunten op te sporen en handelsplaatsen effectief te optimaliseren. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) wordt opgenomen in Adobe Commerce op cloudinfrastructuur, en [Waarneming voor Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) is inbegrepen voor zowel wolk als op-gebouw plaatsingen.

Gebruik deze gereedschappen om de prestaties van de site te analyseren en prestatieproblemen op te sporen met betrekking tot:

- CPU-intensieve functies
- Cachebeheerconfiguratie voor query&#39;s en back-endbewerkingen
- API-aanroepen van derden
- Uitsnede plannen

U kunt bijvoorbeeld transacties nauwkeurig onderzoeken waarbij de nadruk ligt op productdetails en categoriepagina&#39;s. Tijdrovende processen identificeren die kunnen worden geoptimaliseerd om de prestaties te verbeteren. In één client-service zag objectsource een prestatieprobleem op een pagina met productdetails en vond een API-aanroep die 3,5% van de prestatietijd verbruikte. Gebaseerd op dit resultaat, onderzochten zij de hiërarchie van code uitvoering om de kwestie te identificeren en te bevestigen die het knelpunt veroorzaakt.

Meer informatie over het beheren van de siteprestaties:

- [Prestatiebewaking](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (cloudinfrastructuur)
- [Evaluatie voor optimalisatie van prestaties](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [Best practices voor configuratie](/help/performance/configuration.md)
- [Waarneming voor Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### MySQL-prestaties optimaliseren

Het richten van MySQL prestatieskwesties door gegevensbestand het groeperen en vraagoptimalisering uit te voeren is een efficiënte benadering om prestaties vóór en tijdens hoge verkeersperioden zoals Zwarte Vrijdag te verbeteren.

#### Database-clustering implementeren

Websites met veel verkeer hebben vaak te maken met knelpunten in databases, voornamelijk veroorzaakt door het vertrouwen op één MySQL-server. U kunt deze knelpunten aanpakken door gegevensbestand het groeperen uit te voeren, een verdeelde architectuur die prestaties verbetert en hoge beschikbaarheid verzekert.

Het groeperen van het gegevensbestand minimaliseert het effect van op gegevensbestand betrekking hebbende kwesties tijdens piekverkeersperioden door veelvoudige Webknopen toe te laten om met veelvoudige servers te verbinden MySQL. De hulpmiddelen van het gebruik zoals Cluster Galera aan opstellingsgegevensbestand zich groeperen voor de plaatsen van de Handel. Galera Cluster is inbegrepen bij [Adobe Commerce-projecten geïmplementeerd op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### MySQL-query&#39;s optimaliseren

De infrastructuur voor de meeste Adobe Commerce-sites bestaat meestal uit meerdere webknooppunten die zijn verbonden met één MySQL-server.

In deze opstelling, verbindt elk front-end Webknoop met de Cluster Galera, die voor veelvoudige servers MySQL toestaat. Het verhogen van het aantal front-end Webknopen kan toepassingsprestaties verbeteren, maar de enige server MySQL blijft een knelpunt.

Om MySQL serverprestaties te optimaliseren en knelpunten te minimaliseren, is het essentieel om onnodige vragen te identificeren en te verminderen. Bijvoorbeeld, als u 1.000 vragen per seconde verzendt, maar slechts 200 noodzakelijk zijn, kan het optimaliseren, en het verminderen van de vraagtelling prestaties beduidend verbeteren.

Meer informatie over het configureren en optimaliseren van MySQL:

- [Beste praktijken voor gegevensbestandconfiguratie](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Trage replicatie voor Galera DB-replicatie](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Algemene MySQL-richtlijnen](/help/installation/prerequisites/database/mysql.md)
- [MySQL query caching](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Snijtaken effectief beheren: prestaties en timing

Cron-taken spelen een essentiële rol bij het verwerken van de achtergrondtaken van de site, zoals het genereren van rapporten en het indexeren van producten. Voor het optimaliseren van taken voor uitsnijden moet u echter zorgvuldig rekening houden met de invloed ervan op de algehele prestaties. De ontwikkelaars moeten de het plannen frequentie evalueren en de optimale timing bepalen die op specifieke vereisten wordt gebaseerd.

Het in evenwicht brengen van prestaties en gemak, is het vaak raadzaam om kanonnen banen tijdens lage verkeersperiodes te plannen. Het omgaan met klanten in verschillende tijdzones kan echter uitdagingen met zich meebrengen en vraagt om een doordachte aanpak om te zorgen voor een harmonieuze ervaring in verschillende geografische gebieden.

Als u voor het optimaliseren van kroonprestaties en timing verantwoordelijk bent, herzie de huidige kroonconfiguratie van Admin van de Handel, en leer over vestiging en het vormen van kroonbanen voor de projecten van de Handel.

U kunt ook Observatie voor Adobe Commerce gebruiken om aan elkaar gerelateerde prestatie-indicatoren weer te geven. Met dit programma worden loggegevens uit meerdere bronnen gecombineerd, zodat u de prestaties van de Adobe Commerce-site beter kunt beheren en problemen kunt vaststellen.

Meer informatie over Adobe Commerce Cron-implementatie:

- [Uitsnijden (geplande taken)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) in de _Gebruikershandleiding Admin-systemen voor handel_
- [Toepassingsconfiguratie - eigenschap &#39;crons&#39;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (cloudinfrastructuur)
- [Cronnen configureren en uitvoeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (in gebouwen)
- [Waarneming voor Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (Zie de [!UICONTROL Cron] en [!UICONTROL MySQL] tabs.)

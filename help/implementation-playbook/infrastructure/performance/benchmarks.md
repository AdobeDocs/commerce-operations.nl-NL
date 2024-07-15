---
title: Prestatiebenchmarks
description: Bekijk de resultaten van benchmarkprestaties voor Adobe Commerce-implementaties die worden gehost op de Adobe cloud-infrastructuur.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Overzicht van benchmarks

De benchmarkresultaten van Adobe Commerce 2.4.5 weerspiegelen de prestaties zoals gemeten op een Adobe Commerce-instantie die met de volgende infrastructuur en extra onderdelen wordt geïmplementeerd.
- [ Pro wolkenmilieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) met [ geschaalde architectuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [ B2B voor Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [ Adobe Commerce Inventory management ](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [ Adobe Stock ](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Er zijn geen aanvullende aanpassingen.

De volgende informatie geeft een overzicht van de benchmarkresultaten en geeft informatie over de omgeving en de gegevens die tijdens het testen worden gebruikt.

## Belangrijkste prestatiemetingen

In de volgende afbeelding ziet u de Commerce store-configuratie voor de prestatiebenchmark en de belangrijkste prestatiemetriek van de testresultaten.

![ Benchmark JMeter van Prestaties en de Infrastructuur van de Productie ](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Op basis van testcriteria die een B2C-organisatie van een onderneming simuleren, kan het systeem de gevraagde verkeer- en bestelnummers afhandelen tijdens piektijden, bij een standaardlaadstroom.

### Prestatiehooglichten

- **orden** - verwerkte 3.481 orden per minuut terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99e percentiel (99% van de verzoeken werden onderhouden met een reactietijd van minder dan 2 seconden).
- **de meningen van de Pagina** - behandelde meer dan 2 miljoen paginameningen per uur terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99e percentiel.
- **Effectieve SKUs** - het klantenprofiel omvatte 242 miljoen verschillende prijsvariaties (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html"> eSKUs </a>) voor 250.000 producten.
- **GraphQL verzoeken** - Systeem dat aan 10.500 GraphQL uncaching verzoeken per minuut wordt geschaald terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99e percentiel.
- **Gelijktijdige Admin gebruikers** - Systeem dat wordt geschaald om 500 gezamenlijke admin gebruikers te steunen terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99e percentiel.

## Testomgeving

Prestatiebenchmarkresultaten werden verkregen door te testen op een Adobe Commerce 2.4.5-instantie die is geïmplementeerd in een Pro-cloudomgeving met geschaalde architectuur. De instantie had ook de Adobe Commerce B2B-, Inventory management-, en Adobe Stock Integration-modules geïnstalleerd, geconfigureerd en ingeschakeld.

De prestaties testende gegevens voor het testprofiel werden geproduceerd gebruikend <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html"> Toolkit van Prestaties </a>.

Prestatiemetingen zijn gebaseerd op gesimuleerde dagelijkse winkelactiviteiten voor klanten en zakelijke gebruikers. De waarden weerspiegelen een bijna maximumproductie voor elk geval, maar weerspiegelen geen unieke bedrijfsmodellen, zoals privé verkoop of flitsverkoop.

- **LUMA Storefront**
   - 3000 gelijktijdige gebruikers op de winkel
   - Instellen op 30% CDN-cache-raaksnelheid

     Als u de cachelaag op effectieve wijze gebruikt, neemt het aantal paginaweergaven per uur toe.

- **GraphQL API**
   - 250 gelijktijdige threads
   - Instellen op 0% CDN-cache-raaksnelheid

     De responstijden worden aanzienlijk verbeterd met een caching-laag voor GraphQL.

- **Admin Web**
   - 500 gelijktijdige gebruikers
   - Instellen op 0% CDN-cache-raaksnelheid

## Specificaties van de testomgeving

Het laden is voltooid met JMeter-laadprofielen die op de Adobe Commerce-instantie worden uitgevoerd. Tijdens de test werden drie webknooppunten en drie serviceknooppunten gebruikt. In de volgende afbeelding ziet u het ingangspunt van de JMeter- en Productie-infrastructuur.

![ Benchmark JMeter van Prestaties en de Infrastructuur van de Productie ](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495) {width="700" zoomable="yes"}

### Toepassing

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html"> Adobe Commerce 2.4.5 </a> wordt opgesteld op wolkeninfrastructuur met Pro architectuur.

### Infrastructuur

Voor het prestatiesbenchmark, Adobe Commerce 2.4.5 werd opgesteld op a [ scalable infrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) met de volgende capaciteit.

- **de knoopspecificaties van het Web**
   - vCPU 216 (72 x 3 knooppunten)
   - Geheugen 432 GiB (144 x 3 knooppunten)
   - Netwerkbandbreedte 768 Gbps (256 x 3 knooppunten)
   - EBS-bandbreedte 57000 Mbps (19000 x 3 knooppunten)
   - Voorziene opslag 100 GB

- **de knoopspecificaties van de Dienst**
   - vCPU 192 (64 x 3 knooppunten)
   - Geheugen 768 GiB (256 x 3 knooppunten)
   - Netwerkbandbreedte 60 Gbps (20 x 3 knooppunten)
   - EBS-bandbreedte 40800 Mbps (1.3600 x 3 knooppunten)
   - Voorziene opslag 1100 GB

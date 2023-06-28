---
title: Prestatiebenchmarks
description: Resultaten van de prestatiebenchmark bekijken voor Adobe Commerce-implementaties die worden gehost op de Adobe-cloudinfrastructuur.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Overzicht van benchmarks

De benchmarkresultaten van Adobe Commerce 2.4.5 weerspiegelen de prestaties zoals gemeten op een Adobe Commerce-instantie die met de volgende infrastructuur en extra onderdelen wordt geïmplementeerd.
- [Pro-cloudomgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) with [geschaalde architectuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B voor Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Er zijn geen aanvullende aanpassingen.

De volgende informatie geeft een overzicht van de benchmarkresultaten en geeft informatie over de omgeving en de gegevens die tijdens het testen worden gebruikt.

## Belangrijkste prestatiewaarden

Het volgende cijfer toont de de opslagconfiguratie van de Handel voor de prestatiesbenchmark en de belangrijkste prestatiesmetriek van de testresultaten.

![Prestatiebenchmark JMeter en Productie-infrastructuur](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Op basis van testcriteria die een B2C-organisatie van een onderneming simuleren, kan het systeem de gevraagde verkeer- en bestelnummers afhandelen tijdens piektijden, bij een standaardlaadstroom.

### Prestatiehooglichten

- **Orders**—Verwerkte 3.481 orders per minuut met behoud van reactietijden van minder dan 2 seconden gedurende het 99e percentiel (99% van de verzoeken werd behandeld met een reactietijd van minder dan 2 seconden).
- **Paginaweergaven**—Wordt verwerkt door meer dan 2 miljoen paginaweergaven per uur terwijl de responstijden voor het 99e percentiel minder dan 2 seconden bedragen.
- **Effectieve SKU&#39;s**—Het klantenprofiel omvatte 242 miljoen verschillende prijsverschillen (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU&#39;s</a>) voor 250.000 producten.
- **GraphQL-verzoeken**—Systeem geschaald naar 10.500 GraphQL verzoeken zonder caching per minuut terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99ste percentiel.
- **Gelijktijdige beheergebruikers**—Systeem geschaald om 500 gelijktijdige admin gebruikers te steunen terwijl het handhaven van reactietijden van minder dan 2 seconden voor het 99e percentiel.

## Testomgeving

Prestatiebenchmarkresultaten werden verkregen door te testen op een Adobe Commerce 2.4.5-instantie die is geïmplementeerd in een Pro-cloudomgeving met geschaalde architectuur. De instantie had ook de Adobe Commerce B2B-, Inventory management-, en Adobe Stock Integration-modules geïnstalleerd, geconfigureerd en ingeschakeld.

De testgegevens voor de prestaties van het testprofiel zijn gegenereerd met behulp van de <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Prestatiewerkset</a>.

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

![Prestatiebenchmark JMeter en Productie-infrastructuur](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Toepassing

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> geïmplementeerd op cloudinfrastructuur met Pro-architectuur.

### Infrastructuur

Adobe Commerce 2.4.5 werd op een [schaalbare infrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) met de volgende capaciteit.

- **Webknooppuntspecificaties**
   - vCPU 216 (72 x 3 knooppunten)
   - Geheugen 432 GiB (144 x 3 knooppunten)
   - Netwerkbandbreedte 768 Gbps (256 x 3 knooppunten)
   - EBS-bandbreedte 57000 Mbps (19000 x 3 knooppunten)
   - Voorziene opslag 100 GB

- **Specificaties voor serviceknooppunten**
   - vCPU 192 (64 x 3 knooppunten)
   - Geheugen 768 GiB (256 x 3 knooppunten)
   - Netwerkbandbreedte 60 Gbps (20 x 3 knooppunten)
   - EBS-bandbreedte 40800 Mbps (1.3600 x 3 knooppunten)
   - Voorziene opslag 1100 GB

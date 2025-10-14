---
title: Het tabblad [!UICONTROL CDN]
description: Leer meer over het [!UICONTROL CDN] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Het tabblad [!UICONTROL CDN]

Dit tabblad bevat informatie die is gericht op de [!DNL content delivery network (CDN)] . In het geval van Adobe Commerce Cloud is dit de [!DNL Fastly] -service.

## [!UICONTROL HIT rate]

![&#x200B; Tarief van het HIT &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

In het frame **[!UICONTROL HIT rate]** wordt het aantal cacheable-aanvragen weergegeven dat op het laatste moment tot [!UICONTROL HITS] heeft geleid. Dit geeft aan dat caching is gelukt. De pijl naar rechts toont het percentage boven of onder dezelfde tijd een week geleden.

## [!UICONTROL HIT Processing]

![&#x200B; HIT Verwerking &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

In dit vak **[!UICONTROL HIT processing]** ziet u het aantal cacheable-aanvragen dat in [!UICONTROL HITS] in de week heeft geresulteerd.

## [!UICONTROL MISS rate]

![&#x200B; MISS tarief &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

In dit vak **[!UICONTROL MISS rate]** ziet u het aantal mislukte aanvragen op het laatste moment. Een fout is wanneer het verzoek niet in het voorgeheugen ondergebracht is, en het verzoek moet aan de oorsprongserver worden overgegaan om de inhoud te dienen. De waarde aan het recht is de vergelijking van verhoging/daling aan het aantal minuten per minuut één week voorafgaand aan.

## [!UICONTROL MISS time]

![&#x200B; MISS tijd &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![&#x200B; HIT Verhouding &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![&#x200B; Percentage van de Fout &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

In het vak **[!UICONTROL Error Percentage]** wordt de waarde weergegeven van het percentage FOUT bij aanvragen en de relatieve toename/afname ten opzichte van dezelfde tijd een week eerder.

## [!UICONTROL Total Requests]

![&#x200B; Totale Verzoeken &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![&#x200B; Tarief van de Fout &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![&#x200B; de Snelle Gemiddelde Reactie van het Geheime voorgeheugen voor geselecteerde tijdspanne in seconden &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

In dit frame wordt de duur in seconden van de cacheable-aanvragen weergegeven. Als een `cache_response` a [!UICONTROL MISS] is, wordt het gemiddelde voor gemiste cacheantwoorden voor de geselecteerde tijd weergegeven.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![&#x200B; de Snelle Gemiddelde Reactie van het Geheime voorgeheugen voor geselecteerde tijdspanne in seconden die door POP &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png) worden beperkt

*POP* in deze context verwijst naar een Punt van Aanwezigheid (POP) dat aan functie als pool voor geheim voorgeheugenopslag wordt gevormd. Zie [&#x200B; Punten van aanwezigheid &#x200B;](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![&#x200B; Totale Bandbreedte (Alle POPs) tijdens het geselecteerde tijdkader, vergeleken met 1 week geleden (% verhoging/daling) &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![&#x200B; Verzoeken - sinds geselecteerd tijdkader vergeleken met één week geleden &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Dit kader is gelijkaardig aan de summiere doos voor [!UICONTROL Total Requests] bij de bovenkant, maar toont de de verzoektellingen van vorige weken. Dit zijn allemaal aanvragen, niet alleen cacheable aanvragen (waar `is_cacheable` true is).

## [!UICONTROL Response Count]

![&#x200B; Aantal van de Reactie &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![&#x200B; Bandbreedte door POP &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![&#x200B; Hoogste 5 URLs (5xx of 3xx statuscodes) &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

In de weergave **[!UICONTROL Top 5 URLs]** worden de bovenste 5 URL&#39;s weergegeven die een foutreactie van 5 x of 3 x hebben ondergaan. Vanwege de ruimtebeperking moet u de muis boven de URL houden om de specifieke foutcode te zien die aan die URL is gekoppeld. (bijvoorbeeld in het rode vak van de bovenstaande afbeelding).

## [!UICONTROL Top 25 URLs (200 status)]

![&#x200B; Hoogste 25 URLs (200 status) &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

In het frame **[!UICONTROL Top 25 URLs]** worden de URL&#39;s weergegeven die tijdens het geselecteerde tijdframe een 200-status hebben geretourneerd.

## [!UICONTROL Duration by Response Status]

![&#x200B; Duur door de Status van de Reactie &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

In de grafiek **[!UICONTROL Duration by Response Status]** worden de reacties op de fouten weergegeven op aantal tijdens de geselecteerde tijdlijn, afhankelijk van de code voor de foutstatus.

## [!UICONTROL Duration by Response Status, top 25 urls]

![&#x200B; Duur door de Status van de Reactie, hoogste 25 urls &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

In de grafiek **[!UICONTROL Duration by Response Status, top 25 URLs]** worden de bovenste 25 URL&#39;s weergegeven volgens de duur van de reactie in seconden. Mogelijk moet u de muisaanwijzer boven de URL houden om het volledige pad te kunnen zien. Klik ook op die URL om alle URL&#39;s behalve één URL te verwijderen. Vervolgens kunt u andere URL&#39;s toevoegen door er afzonderlijk op te klikken. Als u afzonderlijke URL&#39;s wilt verwijderen, kunt u de toets ingedrukt houden en op elke URL klikken om deze uit de grafiek te verwijderen.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![&#x200B; Duur door de Status van de Reactie, hoogste 25 niet 200 status &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

De grafiek van **[!UICONTROL Duration by Response Status, top 25 non-200 status]** is vergelijkbaar met de laatste grafiek, behalve dat de focus ligt op niet-200 statuscodes of foutstatuscodes. De foutcode en vervolgens de URL worden weergegeven. Mogelijk moet u de muisaanwijzer boven de URL houden om het volledige pad te kunnen zien. Klik ook op die URL om alle URL&#39;s behalve één URL te verwijderen. Vervolgens kunt u andere URL&#39;s toevoegen door er afzonderlijk op te klikken. Als u afzonderlijke URL&#39;s wilt verwijderen, kunt u de toets ingedrukt houden en op elke URL klikken om deze uit de grafiek te verwijderen.

## [!UICONTROL Error Count by POP timeline]

![&#x200B; Aantal van de Fout door de chronologie van de POP &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

In de grafiek van **[!UICONTROL Error Count by POP timeline]** wordt het aantal statussen van fouten weergegeven in de geselecteerde tijdlijn van het tijdframe, afhankelijk van de foutcode.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![&#x200B; Duur door de status van de Reactie, hoogste 25 cliëntIP, niet 200 status &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

De grafiek **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** toont de IP adressen door de gemiddelde duur over het geselecteerde tijdsbestek waar er statusfoutcodes waren.

## [!UICONTROL IP Frequency]

![&#x200B; IP Frequentie &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

Het frame **[!UICONTROL IP Frequency]** telt de statussen (&#39;MISS&#39; en &#39;PASS&#39;) voor elke IP vanuit de logboeken van [!DNL Fastly] . De verzoeken van het Web met deze statussen zullen de oorsprongsserver bereiken en zullen lading aan de server toevoegen. De top 20 van adressen in frequentie worden getoond. Dit kader kan worden gebruikt om IP aanvallen of bronnen van zware lading op een website te ontdekken. Deze grafiek is ook aanwezig op het samenvattingstabblad en wordt hier geplaatst voor een eenvoudige vergelijking met meer details over de loginformatie van [!DNL Fastly] die op dit tabblad wordt weergegeven.

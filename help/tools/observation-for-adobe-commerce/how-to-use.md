---
title: Hoe te om  [!DNL Observation for Adobe Commerce]  zenuwlet te gebruiken
description: Leer hoe te om  [!DNL Observation for Adobe Commerce]  zenuwlet te gebruiken.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# De [!DNL Observation for Adobe Commerce] nerdlet gebruiken

## Algemene benadering van de behandeling van kwesties

Status van omgevingsbronnen controleren:

* Onderzoek het percentage van **[!UICONTROL Storage Free and MySQL % free storage by node]** frames.

   * Volg de koppelingen in de koptekst van het frame als u weinig opslagruimte ziet.

* Onderzoek het percentage van **[!UICONTROL free system memory and Swap memory free in bytes]** frames.

   * Als deze zeer lage geheugenstaten tonen, kunnen zij aan problemen bijdragen.

* Onderzoek het **[!UICONTROL Alerts during the timeframe]** kader.

   * Adobe Commerce on cloud Infrastructure biedt [!DNL Managed alerts] . U kunt op de koppeling in de koptekst klikken om [!DNL Support Knowledge Base] -artikelen te bekijken die u helpen bij het bepalen van handelingen van uw kant voor specifieke waarschuwingen.

* Onderzoek het **[!UICONTROL CPU % by host]** kader: als het hoge gebruik van cpu tentoonstelt, controleer het [!DNL Support Knowledge Base] artikel in de kopbal voor het kader. Controleer ook of de database-import/export of back-ups niet worden uitgevoerd tijdens piekverkeersperiodes.

* Controleer het frame **[!UICONTROL Web Traffic volume compared to one week ago]** : Als het verkeer in dezelfde periode veel hoger is dan in de voorafgaande week, kan dit dan worden uitgelegd (verkoopcampagne of nieuwe producten die bijvoorbeeld op de markt zijn gebracht)?
   * Als een toename in verkeer niet kan worden verklaard, bekijk de Gemiddelde tijd van de Reactie (milliseconden) voor het productiemilieu. Is het hogere verkeer dat aan een reactietijd bijdraagt verschillend dan wat normaal is? Vergroot de tijdlijn om te zien of is het een anomalie.
   * Heeft de toename van het verkeer gevolgen voor webtransacties? Controleer het **[!UICONTROL Response Code]** -frame op fouten. Als de site is ingedrukt, kunt u op de koppeling `Site Down?` in de koptekst van het frame klikken. Het kader zal om het even welke fouten identificeren die voorkomen en hun frequentie.
   * Heeft iemand wijzigingen in uw website geïmplementeerd? Het **[!UICONTROL Deployment Log Entries]** -frame geeft aan of implementaties zijn uitgevoerd tijdens de tijdsperiode van de uitgave. Als het probleem onmiddellijk na plaatsing is, zou het kunnen zijn dat de plaatsingsactiviteiten extra lading aan de plaats (geheime voorgeheugens ontruimd, opnieuw begonnen de diensten, enz.) toevoegen.
   * Heeft zich een vergroting of verkleining voorgedaan? Als uw site tijdelijk is bijgewerkt, is de oorspronkelijke clustergrootte mogelijk hersteld. Als een verzoek is ingediend om de capaciteit van de site te verhogen, kan de site worden vergroot. Controleer het **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** -frame. Dit kader zal soms een stroomonderbreking op één bepaalde knoop ontdekken. Als de grootte afneemt, kan dit wijzen op een probleem met een of meer knooppunten.

* Het tabblad **[!UICONTROL IP Frequency]** geeft de aanvraagfrequentie aan van IP-adressen die op de oorspronkelijke servers zijn ingesteld (wat betekent dat het verzoek niet vanuit [!DNL Fastly] kon worden verzonden omdat het 74 niet in cache was geplaatst).

   * Voor alle [!DNL Fastly] -gerelateerde problemen controleert u het **[!UICONTROL Fastly Cache]** -frame en selecteert u de Error-facet om het percentage aanvragen te zien die fouten zijn. Ze kunnen een &#39;backend&#39;-probleem aangeven als deze samenvallen met andere taken dan het web.
   * Als het laden niet aan Webverkeer schijnt te zijn, kunnen er fouten of een opeenhoping van niet-Web verzoeken, zoals langzame vragen of [!DNL crons] zijn.

* Controleer het **[!UICONTROL Database Errors]** -frame op fouten die kunnen samenvallen met de publicatie-/probleemtijdlijn.
* Controleer het frame **[!UICONTROL Database mysql-slow.log]** om te bepalen welke SQL-instructies plaatsvinden. `INSERT` -, `UPDATE` - en `DELETE` -opdrachten kunnen even duren als de query niet is geoptimaliseerd. Zelfs `SELECT` -instructies zijn erg inefficiënt als ze worden uitgevoerd met grote tabellen.
* **[!UICONTROL PHP States]** en **[!UICONTROL PHP Errors]** frames laten mogelijke problemen met PHP zien. Het frame **[!UICONTROL PHP States]** geeft PHP-proceseindes weer, start en wanneer de service de status ready per node bereikt. Het frame **[!UICONTROL PHP Errors]** kan helpen te isoleren waar het probleem met PHP is, zoals geheugengrootte, workers of het aantal servers.
* Om latentie in transacties te zien, kunnen de Transacties - Avg, Max, Min lijst door kolom worden gesorteerd om de langst lopende transactieduur te tonen. Een overbelaste cluster heeft een latente duur in transacties, maar het zal ook anomalieën tonen die een probleem met een methode of [!DNL cron] zouden kunnen aanwijzen.
* In het frame **[!UICONTROL Cron error]** worden [!DNL cron] locks, SQL-fouten weergegeven die aan [!DNL cron] logs kunnen worden gekoppeld en gedeelde staging [!DNL crons] weergegeven die in productieomgevingen kunnen worden uitgevoerd wanneer er een speciale testomgeving is.
* Het frame [!UICONTROL ElasticSearch Errors] bevat fouten die kunnen duiden op grote problemen met [!DNL Elasticsearch] query&#39;s, gegevens of indexen.

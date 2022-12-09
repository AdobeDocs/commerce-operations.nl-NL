---
title: "Hoe wordt het [!DNL Observation for Adobe Commerce] nerdlet"
description: Leer hoe u de [!DNL Observation for Adobe Commerce] nerdlet.
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Hoe wordt de [!DNL Observation for Adobe Commerce] nerdlet

## Algemene benadering van de behandeling van kwesties

Status van omgevingsbronnen controleren:

* Onderzoek het percentage van **[!UICONTROL Storage Free and MySQL % free storage by node]** frames.

   * Volg de koppelingen in de koptekst van het frame als u weinig opslagruimte ziet.

* Onderzoek het percentage van **[!UICONTROL free system memory and Swap memory free in bytes]** frames.

   * Als deze zeer lage geheugenstaten tonen, kunnen zij aan problemen bijdragen.

* Onderzoek **[!UICONTROL Alerts during the timeframe]** frame.

   * Adobe Commerce on cloud Infrastructure biedt [!DNL Managed alerts]. U kunt op de koppeling in de koptekst klikken om te zien [!DNL Support Knowledge Base] artikelen die u helpen bij het bepalen van handelingen voor specifieke waarschuwingen.

* Onderzoek **[!UICONTROL CPU % by host]** frame: Als het hoge gebruik van cpu tentoonstelt, controleer [!DNL Support Knowledge Base] artikel in de koptekst voor het frame. Controleer ook of de database-import/export of back-ups niet worden uitgevoerd tijdens piekverkeersperiodes.

* Controleer de **[!UICONTROL Web Traffic volume compared to one week ago]** frame: Als het verkeer in dezelfde periode veel groter is dan de voorafgaande week, kan dit dan worden uitgelegd (verkoopcampagne of nieuwe producten die bijvoorbeeld op de markt zijn gebracht)?
   * Als een toename in verkeer niet kan worden verklaard, bekijk de Gemiddelde tijd van de Reactie (milliseconden) voor het productiemilieu. Is het hogere verkeer dat aan een reactietijd bijdraagt verschillend dan wat normaal is? Vergroot de tijdlijn om te zien of is het een anomalie.
   * Heeft de toename van het verkeer gevolgen voor webtransacties? Controleer de **[!UICONTROL Response Code]** frame voor fouten. Als de site niet beschikbaar is, kunt u op de knop `Site Down?` in de koptekst van het frame. Het kader zal om het even welke fouten identificeren die voorkomen en hun frequentie.
   * Heeft iemand wijzigingen in uw website geïmplementeerd? De **[!UICONTROL Deployment Log Entries]** frame zal erop wijzen of om het even welke plaatsingen tijdens de uitgiftetijd zijn gedaan. Als het probleem onmiddellijk na plaatsing is, zou het kunnen zijn dat de plaatsingsactiviteiten extra lading aan de plaats (geheime voorgeheugens ontruimd, opnieuw begonnen de diensten, enz.) toevoegen.
   * Heeft zich een vergroting of verkleining voorgedaan? Als uw site tijdelijk is bijgewerkt, is de oorspronkelijke clustergrootte mogelijk hersteld. Als een verzoek is ingediend om de capaciteit van de site te verhogen, kan de site worden vergroot. Controleer de **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** frame. Dit kader zal soms een stroomonderbreking op één bepaalde knoop ontdekken. Als de grootte afneemt, kan dit wijzen op een probleem met een of meer knooppunten.

* De **[!UICONTROL IP Frequency]** tab identificeert de aanvraagfrequentie van IP-adressen die worden gemaakt op de oorspronkelijke servers (wat betekent dat het verzoek niet kan worden verzonden vanaf [!DNL Fastly] omdat 74 het niet in cache was geplaatst).

   * Voor alle [!DNL Fastly] verwante problemen, controleer de **[!UICONTROL Fastly Cache]** frame en selecteer het facet Fout om het percentage van de aanvragen dat fouten zijn weer te geven. Ze kunnen een &#39;backend&#39;-probleem aangeven als deze samenvallen met andere taken dan het web.
   * Als de lading niet aan Webverkeer schijnt te zijn, kunnen er fouten of een opeenhoping van niet-Web verzoeken, zoals langzame vragen zijn of [!DNL crons].

* Controleer de **[!UICONTROL Database Errors]** frame voor fouten die kunnen samenvallen met de probleem-/probleemtijdlijn.
* Controleer de **[!UICONTROL Database mysql-slow.log]** frame voor het identificeren van SQL-instructies. `INSERT`, `UPDATE`, en `DELETE` opdrachten kunnen even duren als de query niet is geoptimaliseerd. Even `SELECT` instructies kunnen zeer inefficiënt zijn als ze tegen grote tabellen worden uitgevoerd .
* **[!UICONTROL PHP States]** en **[!UICONTROL PHP Errors]** In frames worden mogelijke problemen met PHP weergegeven. De **[!UICONTROL PHP States]** frame zal PHP procesebeëindiging tonen, begint, en wanneer de dienst de klaar staat door knoop bereikt. De **[!UICONTROL PHP Errors]** frame kan helpen te isoleren waar het probleem met PHP is, zoals geheugengrootte, workers of het aantal servers.
* Om latentie in transacties te zien, kunnen de Transacties - Avg, Max, Min lijst door kolom worden gesorteerd om de langst lopende transactieduur te tonen. Een overbelaste cluster heeft een latente tijdsduur in transacties, maar er worden ook anomalieën weergegeven die een probleem met een methode of [!DNL cron].
* De **[!UICONTROL Cron error]** frame wordt weergegeven [!DNL cron] vergrendelingen, SQL-fouten die aan [!DNL cron] logbestanden en gedeelde staging [!DNL crons] die op productieomgevingen kunnen worden uitgevoerd wanneer er een speciale testomgeving is.
* De [!UICONTROL ElasticSearch Errors] frame bevat fouten die kunnen wijzen op grote problemen met [!DNL Elasticsearch] query&#39;s, gegevens of indices.

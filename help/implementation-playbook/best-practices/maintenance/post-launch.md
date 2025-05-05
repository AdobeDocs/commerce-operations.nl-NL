---
title: Ondersteuning en onderhoud na de introductie
description: Zorgen voor optimale prestaties en beveiliging van uw Adobe Commerce-winkel met onze uitgebreide best practices voor ondersteuning en onderhoud na de introductie.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Ondersteuning en onderhoud na de introductie voor Adobe Commerce

Ondersteuning en onderhoud na de introductie zijn van cruciaal belang om ervoor te zorgen dat uw Adobe Commerce-winkel probleemloos functioneert, goed functioneert, veilig blijft en aan uw bedrijfsdoelstellingen blijft voldoen. Deze fase omvat continue bewaking, optimalisatie, foutopsporing, updates en gebruikersondersteuning. De volgende secties onderverdelen **post-lanceringssteun** in zeer belangrijke categorieën:

## Regelmatige plaatscontrole en prestatiesoptimalisering

### Prestatiebewaking

- **de snelheid van de Plaats en lading het testen**: Adobe Commerce kan middel-intensief zijn, zodat is het regelmatige prestatiestoezicht cruciaal.

   - **Hulpmiddelen om** te gebruiken: Alle Adobe Commerce op de projecten van de wolkeninfrastructuur omvat toegang tot New Relic, die hulp in het controleren van prestaties en het onderzoeken van gebeurtenissen binnen de toepassing van Commerce en wolkeninfrastructuur. Extra gereedschappen zijn onder andere Google PageSpeed Insights en GTMetrix.

   - **wat te controleren**: Hier zijn de belangrijkste punten voor Adobe Commerce op wolkeninfrastructuur te controleren:

      - **de berichten van de Gezondheid**: Alarm voor schijfruimte en milieugezondheid.

      - **Waarneming**: Uitgebreide controle die logboekgegevens van veelvoudige bronnen voor efficiënt plaatsbeheer combineren.

      - **de dienst van New Relic**: Controleert prestaties in het opvoeren en productie, het concentreren op zeer belangrijke metriek.

      - **Beheerd alarmbeleid**: De metriek van sporen met vooraf bepaalde drempels om berichten voor infrastructuur of toepassingskwesties teweeg te brengen die prestaties beïnvloeden.

  >[!TIP]
  >
  >Zie [ prestaties controle ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) in de _Gids van de Wolk_.


- **Optimizing gegevensbestandprestaties**: Om gegevensbestandprestaties in Adobe Commerce Cloud te optimaliseren, voer het volgende uit:

   - **Monitor en optimaliseer MySQL vragen**: Identificeer en los langzaam-lopende vragen op, die kunnen worden gedaan gebruikend TOONT het VOLLEDIGE PROCESSLIST van MySQL en EXPLAIN bevelen. Voor complexere montages, Pro kunnen de architectuurgebruikers Toolkit Percona gebruiken om vraaglogboeken voor prestatieskwesties te analyseren.

   - **het beheer van de Index**: Zorg ervoor dat elke lijst een primaire sleutel heeft en verwijder om het even welke dubbele indexen, aangezien deze efficiency kunnen verminderen en tot conflicten tijdens gelijktijdig schrijven leiden.

   - **de baanoptimalisering van de Kroon**: De banen van de Kroon zouden tijdens off-piek uren moeten worden gepland om het effect op prestaties te minimaliseren, vooral als achtergrondtaken zoals het indexeren frequent zijn.

  >[!TIP]
  >
  >Zie [ beste praktijken voor het oplossen van de kwesties van gegevensbestandprestaties ](resolve-database-performance-issues.md).

- **Monitor CDN**: Om de prestaties van CDN in Adobe Commerce Cloud te controleren snel, kunt u de volgende acties nemen:

   - **Hefboomwerking New Relic voor controle**: Adobe Commerce biedt New Relic aan om prestaties en andere metriek op het opvoeren en productiemilieu&#39;s snel te controleren. Dit hulpmiddel verstrekt inzichten in servergezondheid, CDN caching, en netwerkverzoeken in tijd, die hulp patronen identificeert en montages CDN optimaliseert.

   - **de Analyse van de Logboeken van de Fastly**: Voor Adobe Commerce Cloud Pro projecten, kunt u de Logboeken van New Relic gebruiken om snel CDN en het logboekgegevens van WAF te herzien en te analyseren om prestatietrends, veiligheidsgebeurtenissen te volgen, en fouten of latentiekwesties te diagnostiseren.

   - **bevelen van het Gebruik cURL**: De bevelen van de Looppas cURL met Fastly-specifieke kopballen om het geheim voorgeheugenstatus van uw plaats te inspecteren. Belangrijke responsheaders zijn `X-Cache` (HIT/MISS), `Fastly-Module-Enabled` , `Fastly-Magento-VCL-Uploaded` en `Cache-Control` om de status van de cache en module te controleren. Adobe biedt voorbeeld-cURL-opdrachten voor zowel testomgevingen als productieomgevingen.

   - **de kopbalinformatie van de Controle**: De kopballen van Inspect zoals `Cache-Control`, `Pragma`, en `X-Magento-Tags` om aangewezen caching gedrag en markering behandeling op caching inhoud te bevestigen. De juiste kopbalwaarden wijzen erop of de caching configuraties effectief over CDN worden toegepast.

   - **snel het zuiveren en het testen**: De het zuiveren eigenschap van het gebruik van Fastly om kwesties met de tarieven van het geheime voorgeheugenHIT en MISS, caching logica, of onjuiste kopbalreacties te identificeren en problemen op te lossen, die aan configuratiekwesties of misgroepering met verwachte caching regels kunnen richten.

Deze controlestappen helpen optimale CDN-prestaties en adresproblemen te behouden die de snelheid en betrouwbaarheid van de site beïnvloeden.

>[!TIP]
>
>Zie [ het Snelle overzicht van de diensten ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) in de _Gids van de Wolk_.

#### Regelmatige bewaking van de beveiliging

Om regelmatig veiligheidscontrole in Adobe Commerce Cloud te handhaven, adviseert de Adobe een veelzijdige benadering die ononderbroken aftasten, registreren, en pro-actieve veiligheidspraktijken omvat. Hier volgen enkele kernacties om de continuïteit van de beveiliging te garanderen:

- **het aftasten van de Veiligheid van de Veiligheid van het gebruik**: Het hulpmiddel van het Scannen van de Veiligheid van de Adobe om voor bekende kwetsbaarheid en malware over uw plaatsen van Commerce te controleren. Dit hulpmiddel verstrekt alarm voor potentiële veiligheidsrisico&#39;s en nalevingskwesties.

- **Regelmatig flardonderhoud en updateonderhoud**: Pas de veiligheidspatches en updates van de Adobe toe aangezien zij beschikbaar worden. Door een upgrade uit te voeren naar de nieuwste Adobe Commerce-versie, bent u verzekerd van de nieuwste beveiliging tegen bedreigingen.

- **Controle en logboek controle**: De hulpmiddelen van de hefboomwerking zoals Logs van New Relic (beschikbaar voor Pro projecten) om veiligheidslogboeken van zowel het opvoeren als productiemilieu&#39;s te centraliseren en te analyseren, die de zichtbaarheid van potentiële veiligheidskwesties en schendingen verbeteren.

- **Rekening en toegangsbeheer**: Controleer regelmatig gebruiker en admin rekeningen om het even welke onbevoegde of verouderde rekeningen te verwijderen. Verbeter toegangscontroles met multi-factor authentificatie (MFA) voor admingebruikers.

- **de toepassingsfirewall van het Web (WAF)**: Gebruik geïntegreerd snel WAF om bedreigingen van kwaadwillige verkeerspatronen, zoals ongeoorloofde pogingen van de gegevensextractie te ontdekken en te verlichten.

- **de code en uitbreidingsveiligheid van de Douane**: Beveilig om het even welke douanecode of derdeuitbreidingen door regelmatige codecontroles te leiden en uitbreidingen te beperken tot die die door Adobe worden gecontroleerd.

>[!TIP]
>
>Zie [ Veiligheid ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) in de _Gids van Systemen Admin_.

#### Foutenregistratie en -controle

Om foutenregistratie in Adobe Commerce Cloud te controleren, verstrekt de Adobe verscheidene hulpmiddelen en praktijken voor efficiënte het oplossen van problemen en prestatiesbeheer:

- **samenvoeging van het Logboek met New Relic**: New Relic verzamelt en centraliseert logboeken van de toepassingen van Adobe Commerce, met inbegrip van logboeken met betrekking tot infrastructuur, CDN, en WAF. Met deze instelling kunt u fouten gestroomlijnd bijhouden, dashboards maken en logbestanden opvragen voor dieper inzicht in de prestaties en problemen van toepassingen. Met toegang tot New Relic Logs kunt u logbestanden zoeken en filteren op basis van verschillende kenmerken om problemen snel te diagnosticeren.

- **het logboektypes van de Fout**: De zeer belangrijke foutenlogboeken in Adobe Commerce Cloud omvatten `cloud.log`, die plaatsing bevat terugkoppelt, en `cloud.error.log`, die plaatsingswaarschuwingen en fouten registreert. Andere specifieke logboekbestanden voor foutopsporing zijn `debug.log` , `system.log` en `exception.log` , waarbij elke afzonderlijke rol in fout- en gebeurtenistracering wordt uitgevoerd op het Commerce-platform.

- **het registreren van de Douane met Monolog**: Adobe Commerce steunt douaneregistreren via Monolog, die ontwikkelaars toestaat om logboekberichten aan diverse bestemmingen zoals dossiers, gegevensbestanden, en zelfs alarm te leiden. Deze flexibiliteit is nuttig om geavanceerde logboekstrategieën te bouwen die aan verschillende controlebehoeften in ontwikkeling en productiemilieu&#39;s passen.

- **Uitzonderingen die met plaats-brede analysehulpmiddel** controleren: De plaats-brede hulp van de analysehulp controleert en beheert uitzonderingslogboeken, identificerend terugkomende kwesties over plaatsing en toepassingsgebeurtenissen. Dit hulpmiddel benadrukt frequente kwesties, die het gemakkelijker maken om aan kritieke problemen voorrang te geven en te behandelen die prestaties beïnvloeden.

>[!TIP]
>
>Voor meer details bij het registreren en fout het volgen praktijken in Adobe Commerce Cloud, zie [ het logboekbeheer van New Relic ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) en [ uitzondering controle ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Beveiliging en updates

#### Beveiligingspatches en -updates

Om up-to-date te blijven en de veiligheid van uw Adobe Commerce Cloud-systeem te garanderen, volgt u enkele belangrijke procedures voor het controleren van beveiligingspatches en -updates:

- **maak een abonnement op de veiligheidsalarm van Adobe Commerce**: Het blijven geïnformeerd over veiligheidskwetsbaarheid door [ registrerend voor berichten van Adobe ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **de versienota&#39;s van de Controle**: Herzie regelmatig [ de versienota&#39;s van het veiligheidspatch ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), die met &quot;-pN&quot;voor versies (b.v., 2.3.5-p1) worden geëtiketteerd, en bevatten kritieke moeilijke situaties en verbeteringen.

- **pas onmiddellijk veiligheidspatches** toe: Pas veiligheidspatches toe zodra zij beschikbaar zijn. Dit omvat het bijwerken naar de nieuwste versies of het toepassen van specifieke patchbestanden.

- **de wolkenfspatches van het Gebruik**: Voor Adobe Commerce Cloud, kunnen de veiligheidspatches binnen de Reeks van de Hulpmiddelen van de Wolk worden gebundeld. Upgrade de suite of de Commerce-versie om deze oplossingen te ontvangen.

- **Geautomatiseerd flardbeheer**: Overweeg het gebruiken van hulpmiddelen als de gecentraliseerde patcher om [ patches automatisch over veelvoudige opslag te beheren en toe te passen ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Voor verdere details en geleidelijke instructies bij het toepassen van flarden en het handhaven van veiligheid, zie {de opmerkingen van de versie van het 0} veiligheidspatch [&#128279;](../../../release/release-notes/security/overview.md) en [ hoe te om de Patches van de Veiligheid ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) toe te passen. [ U zou ook ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) rapporten van het Hulpmiddel van de Analyse voor de hele Plaats  moeten herzien.

#### PCI-compatibiliteit

Volg de volgende belangrijke procedures om ervoor te zorgen dat de PCI-compatibiliteit in Adobe Commerce Cloud wordt nageleefd:

- **de kaarthoudergegevens van Protect**: Sla nooit kaarthoudergegevens binnen Adobe Commerce op. Als opslag vereist is, gebruik gecodeerde en verdeelde methodes om het te beschermen.

- **Gebruik veilige transmissieprotocollen**: Verzend altijd betalingsgegevens over veilige protocollen zoals TLS, met encryptie en correct zeer belangrijk beheer.

- **Gebruikt de firewall van de Webtoepassing (WAF)**: De snelaangedreven dienst van WAF helpt aan PCI DSS 6.6 vereisten voldoen en tegen gemeenschappelijke kwetsbaarheid beschermen door kwaadwillig verkeer te blokkeren alvorens het uw plaats bereikt. Zie meer informatie [ hier ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) en [ hier ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **de toegang van de grens**: Zorg ervoor dat slechts het gemachtigde personeel toegang tot gevoelige betalingsgegevens heeft, en [ toegangscontrole toepast om het risico van blootstelling ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) te verminderen.

- **Regelmatig veiligheidsaftasten**: Voer regelmatige aftasten PCI ASV uit en [ controleer uw milieu ](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) om potentiële kwetsbaarheid te richten.

>[!TIP]
>
>Voor meer gedetailleerde richtlijnen bij het handhaven van naleving PCI met Adobe Commerce, zie [ beste praktijken voor betalingsverwerking en opslag ](../planning/payment-processing-storage.md).

### Gebruikers- en klantenondersteuning

#### Instellen

- **kanalen van de Steun**: Voer de kanalen van de klantensteun zoals uit:

   - **Levende praatje**: De steun van de aanbieding de levende praatje voor directe hulp. De populaire oplossingen omvatten Zendesk, Intercom, en Tidio.

   - **E-mailsteun**: Gebruik een systeem van de steun het etiketteren zoals Freshdesk of Zoho Desk om klantenonderzoeken effectief te beheren.

   - **de steun van de Telefoon**: Als u een grote klantenbasis hebt, overweeg het aanbieden van telefoonsteun tijdens kantooruren.

#### Gebruikerstraining voor beheerders

- **Interne opleiding**: Leer uw personeel op hoe te om Adobe Commerce Admin te gebruiken, bevelen te verwerken, producten te beheren, en de kwesties van de klantendienst te behandelen.

- **Documentatie**: Handhaaf een interne kennisbasis of een gebruikershandleiding voor vaak gestelde vragen (FAQs), het oplossen van problemen, en gemeenschappelijke taken.

#### Optimalisatie van klantervaring

- **Enquêtes en terugkoppelen**: De onderzoeken van het gebruik om klant te verzamelen terugkoppelen en de klantenervaring te optimaliseren. Adobe Commerce ondersteunt integratie met hulpprogramma&#39;s zoals SurveyMonkey of Google Forms.

- **het beheer van het Overzicht**: Beheer klantenoverzichten en classificaties op uw producten. Moedig klanten met plezier aan om beoordelingen te verlaten en op gepaste wijze op negatieve beoordelingen te reageren.

- **Personalization**: Voer verpersoonlijkingseigenschappen zoals gepersonaliseerde productaanbevelingen of gerichte bevorderingen uit.

### Onderhoud en optimalisatie van de winkel

#### Optimalisatie zoekmachine (SEO)

- **de optimalisering van de Inhoud**: Werk regelmatig productbeschrijvingen, blogberichten, en categoriepagina&#39;s bij om inhoud vers en relevant voor onderzoeksmotoren te houden.

- **controles SEO**: Voer regelmatige controles SEO uit gebruikend hulpmiddelen zoals de Console of het Scheuren van het Onderzoek van Google om SEO kwesties (b.v., gebroken verbindingen, ontbrekende meta-gegevens, dubbele inhoud) te identificeren.

- **structuur URL**: houd een schone, logische structuur URL en zorg ervoor dat er geen gebroken verbindingen of omleidingen zijn.

#### Conversiesnelheid optimaliseren (CRO)

- **het testen A/B**: De tests van A/B van de looppas op verschillende paginaelementen, zoals productpagina&#39;s of controleproces, om omzettingspercentages te verbeteren.

- **Verlaat van de Kaart**: Voer de e-mailcampagnes van de het verlaten van het karretje of uitgang-intent pop-ups uit om verloren verkoop terug te krijgen.

- **optimalisering van de Controle**: Vereenvoudig uw controleproces door het aantal stappen te verminderen en gastcontrole aan te bieden om omzettingen te verbeteren.

#### Marketingintegratie

- **E-mailcampagnes**: Opstelling geautomatiseerde e-mailmarketing stromen voor welkome e-mails, verlaten karretjes e-mails, en post-aankoop follow-ups. Platforms als Adobe Marketo, Mailchimp of Klaviyo integreren goed met Adobe Commerce.

- **sociale media en advertentie integratie**: Integreer met platforms zoals Facebook, Instagram, en Ads van Google om gerichte campagnes en spoorprestaties in werking te stellen.

#### Mobiele optimalisatie

- **Mobiele ontvankelijkheid**: Test regelmatig de mobiele ontvankelijkheid en bruikbaarheid van uw plaats. Aangezien de mobiele handel toeneemt, is een eerste mobiele aanpak van essentieel belang voor een blijvend succes.

- **Mobiele prestaties**: De mobiele-vriendelijke test en prestatieshulpmiddelen van Google gebruiken om uw mobiele winkelervaring te optimaliseren.

### Schalen en nieuwe functies ontwikkelen

- **auto-schrapend voor verkeer behandeling**:

   - Adobe Commerce Cloud ondersteunt automatisch schalen om serverbronnen (bijvoorbeeld webknooppunten) dynamisch aan te passen op basis van realtime-verkeersvereisten, zodat uw winkel grote bezoekersvolumes kan verwerken zonder handmatig ingrijpen. Zie [ autoscaling ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) in de _Gids van de Wolk_.

   - Web en de dienstrijen kunnen onafhankelijk schrapen, toevoegend meer Webknopen voor verhoogd verkeer en het schrapen van gegevensbestand of de dienstknopen voor backendeprestaties tijdens piekperiodes. Zie [ geschaalde architectuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) in de _Gids van de Wolk_.

- **Controle van Prestaties**:

   - Het gebruik **New Relic** om prestatiesmetriek in real time (b.v., het gebruik van cpu, verkeersniveaus) te controleren en aanpassingen zonodig te maken.

   - Test de prestaties in testomgevingen voordat u gaat schalen om productieproblemen te voorkomen.

- **Ontwikkeling van nieuwe eigenschappen**:

   - Integreer geavanceerde eigenschappen zoals **AI-gedreven verpersoonlijking**, **abonnementsbeheer**, en douaneoplossingen.

   - Test en verfijn voortdurend functies in halveringsomgevingen voordat u gaat implementeren naar productie om downtime tot een minimum te beperken.

- **Onlopend plaatsonderhoud**:

   - Herzie regelmatig systeemlogboeken en prestatiesmetriek om gebieden voor verbetering te identificeren.

   - Zorg ervoor dat de infrastructuur schaalbaar en aanpasbaar blijft aan nieuwe bedrijfsvereisten en groei.

>[!TIP]
>
>Voor gedetailleerde begeleiding, zie [ best practices van het onderhoud ](overview.md), [ verpersoonlijking ](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization), en [ eigenschapontwikkeling ](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Rapportage en analyse

- **Adobe Commerce Intelligence:** Commerce Intelligence, een kernvermogen van Adobe Commerce, verstrekt beste praktijkinzichten over veelvoudige gegevensbronnen, toestaand handelaren om wetenschappelijke gegeven-gedreven besluiten te nemen en duidelijke en geïnformeerde acties te nemen. Zie de [_Gids van de Gebruiker van Commerce Intelligence_ ](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics biedt een krachtige oplossing aan spoor, analyseer, en optimaliseer de prestaties van uw online opslag. Adobe Analytics helpt eCommerce-bedrijven dieper inzicht te krijgen in het gedrag van klanten, de productprestaties, de conversietarieven en andere belangrijke meetgegevens, waardoor gegevensgestuurde besluitvorming mogelijk wordt.

- **Googles Analytics:** Googles Analytics van het gebruik om klantengedrag, verkeersbronnen, en omzettingspercentages te volgen.

- **Extra hulpmiddelen van Commerce Intelligence:** Adobe Commerce omvat Geavanceerde Rapportering. Deze eigenschap geeft u toegang tot een reeks van dynamische rapporten die op uw product, orde, en klantengegevens worden gebaseerd, met een gepersonaliseerd dashboard dat aan uw bedrijfsbehoeften wordt aangepast, zie [ geavanceerde rapportering ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) in de _Gids van de Gebruiker Admin_ voor meer informatie.

### Conclusie

Ondersteuning en onderhoud na de introductie zijn voortdurende inspanningen die regelmatige aandacht vereisen om ervoor te zorgen dat uw Adobe Commerce-winkel goed blijft presteren, veilig blijft en zich aanpast aan de behoeften van uw bedrijf. Het implementeren van een gestructureerde aanpak voor het bewaken van sites, klantenondersteuning, optimalisatie en updates is van cruciaal belang voor succes op de lange termijn.

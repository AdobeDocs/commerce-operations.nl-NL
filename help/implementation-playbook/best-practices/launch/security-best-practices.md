---
title: Uw Commerce-site en -infrastructuur beveiligen
description: Behoud beveiliging door best practices voor beveiliging te implementeren wanneer u Adobe Commerce-installaties instelt, configureert en bijwerkt.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Uw Commerce-site en -infrastructuur beveiligen

Het creëren en onderhouden van een veilige omgeving voor Adobe Commerce-projecten die worden geïmplementeerd op cloudinfrastructuur is een verantwoordelijkheid die wordt gedeeld tussen Adobe Commerce-klanten, oplossingspartners en Adobe. De bedoeling van deze handleiding is om beste praktijken voor de kant van de klant van de vergelijking te verstrekken.

Hoewel u niet alle veiligheidsrisico&#39;s kunt elimineren, verhardt het toepassen van deze beste praktijken de veiligheidshouding van de installaties van Commerce. Een veilige plaats en een infrastructuur maken een minder aantrekkelijk doel voor kwaadwillige aanvallen, verzekert de veiligheid van de oplossing en de gevoelige informatie van de klanten, en helpt veiligheid-gerelateerde incidenten minimaliseren die plaatsverstoringen en dure onderzoeken kunnen veroorzaken.

>[!NOTE]
>
>Voor informatie over de rollen en de verantwoordelijkheden om de projecten van Adobe Commerce op wolkeninfrastructuur te beveiligen en te handhaven, zie [ Gedeeld Verantwoordelijkheidsmodel ](https://experienceleague.adobe.com/nl/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)) in de _Gids van de Veiligheid en van de Naleving van Adobe Commerce_.

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Prioritaire aanbevelingen

Adobe beschouwt de volgende aanbevelingen als van de hoogste prioriteit voor alle klanten. Implementeer deze belangrijke best practices voor beveiliging in alle Commerce-implementaties:

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **laat twee-factor authentificatie voor uw Admin en alle verbindingen van SSH** toe

- [ Veiligheid voor Admin van Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=nl-NL)

- [ Veilige verbindingen SSH ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=nl-NL) (wolkeninfrastructuur)

Wanneer MFA op een project wordt toegelaten, moet alle Adobe Commerce op de rekeningen van de wolkeninfrastructuur met de toegang van SSH een authentificatiewerkschema volgen. Voor deze workflow is een tweevoudige verificatie (2FA)-code of een API-token en SSH-certificaat vereist om toegang te krijgen tot de omgeving.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Beveilig Admin**

- [ vorm een niet-gebrek admin URL ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=nl-NL#use-a-custom-admin-url) in plaats van het gebruiken van het gebrek `admin` of een gemeenschappelijke termijn zoals `backend`. Deze configuratie beperkt de blootstelling aan manuscripten die proberen om onbevoegde toegang tot uw plaats te krijgen.

- [ vorm Geavanceerde veiligheidsmontages ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=nl-NL) - voeg een geheime sleutel aan URLs toe, vereisen wachtwoorden om case-sensitive te zijn, en grens de zittingslengte van Admin, het interval van het wachtwoordleven, en het aantal login toegestane pogingen alvorens een Admin gebruikersrekening te sluiten. Voor verhoogde veiligheid, vorm de lengte van toetsenbordinactiviteit alvorens de huidige zitting verloopt, en vereist de gebruikersbenaming en het wachtwoord om case-sensitive te zijn.

- [ laat ReCAPTCHA ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=nl-NL) toe om Admin tegen geautomatiseerde brutekrachtaanvallen te beschermen.

- Volg het beginsel van minste voorrecht wanneer het toewijzen van [ toestemmingen Admin ](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=nl-NL) aan rollen en rollen aan Admin gebruikersrekeningen.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Verbetering aan de recentste versie van Adobe Commerce**

Houd uw code die door [ wordt bijgewerkt bevordert uw project van Commerce aan de recentste versie ](#upgrade-to-the-latest-release) van Adobe Commerce, de Diensten van Commerce, en uitbreidingen, met inbegrip van veiligheidspatches, hotfixes, en andere die flarden door Adobe worden verstrekt.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Veilige gevoelige configuratiewaarden**

Gebruik [ configuratiebeheer ](../../../configuration/cli/set-configuration-values.md) om kritieke configuratiewaarden te sluiten.

Met de opdrachten `lock config` en `lock env` CLI worden omgevingsvariabelen geconfigureerd om te voorkomen dat deze worden bijgewerkt via de beheerfunctie. De opdracht schrijft de waarde naar het `<Commerce base dir>/app/etc/env.php` -bestand. (Voor Commerce op de projecten van de wolkeninfrastructuur, zie [ het Beheer van de Configuratie van de Opslag ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=nl-NL#sensitive-data).)

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **de veiligheidsscans van de Looppas**

Gebruik de [ dienst van het Scannen van de Veiligheid van Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL) om alle plaatsen van Adobe Commerce voor bekende veiligheidsrisico&#39;s en malware te controleren, en zich aan te melden om flardupdates en veiligheidsberichten te ontvangen.

## Beveiliging van extensies en aangepaste code

Wanneer u Adobe Commerce uitbreidt door extensies van derden toe te voegen vanuit de Adobe Commerce Marketplace of door aangepaste code toe te voegen, dient u de beveiliging van deze aanpassingen te garanderen door de volgende aanbevolen procedures toe te passen:

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **kies een partner of oplossingsintegrator (SI) goed in veiligheid** wordt overgestoken - verzeker veilige integratie en veilige levering van douanecode door organisaties te selecteren die veilige ontwikkelingspraktijken volgen en een stevig spoorverslag hebben van het verhinderen van en het richten van veiligheidskwesties.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Gebruik veilige uitbreidingen** - identificeer de meest aangewezen en veilige uitbreidingen voor de plaatsingen van Commerce door met uw oplossingsintegrator of ontwikkelaar en volgende [ beste praktijken van de Uitbreidingen van Adobe te raadplegen ](../planning/extensions.md).

- Alleen bronextensies van de Adobe Commerce Marketplace of via de integrator van de oplossing. Als de extensie via een integrator wordt aangeschaft, moet u ervoor zorgen dat de eigendom van de extensievergunning overdraagbaar is, voor het geval de integrator verandert.

- Verminder risicoblootstelling door het aantal uitbreidingen en verkopers te beperken.

- Controleer indien mogelijk de beveiligingscode van de extensie voordat u deze integreert met de Commerce-toepassing.

- Ervoor zorgen dat ontwikkelaars van PHP-extensies de Adobe Commerce-ontwikkelrichtlijnen, -processen en best practices op het gebied van beveiliging volgen. Concreet moeten ontwikkelaars het gebruik van PHP-mogelijkheden vermijden die tot de uitvoering van een externe code of een zwakke cryptografie kunnen leiden. Zie [ Veiligheid ](https://developer.adobe.com/commerce/php/best-practices/security/) in de *Beste praktijken voor de Gids van de Ontwikkelaars van de Uitbreiding*.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **code van de Controle** - herzie uw server en broncodebewaarplaats voor ontwikkelingsleftovers. Zorg ervoor dat er geen toegankelijke logboekdossiers, openbaar zichtbare.git folders, tunnels zijn om SQL verklaringen, gegevensbestanddumps, php- informatiedossiers, of andere onbeschermde dossiers uit te voeren die niet worden vereist, en die in een aanval zouden kunnen worden gebruikt.

## Upgrade naar de nieuwste versie

Adobe brengt voortdurend bijgewerkte oplossingscomponenten vrij om veiligheid te verbeteren en klanten beter tegen mogelijk compromis te beschermen. De upgrade naar de nieuwste versie van de Adobe Commerce-toepassing, geïnstalleerde services en extensies en het toepassen van huidige patches is de eerste en beste verdedigingslinie tegen beveiligingsrisico&#39;s.

Commerce geeft typisch veiligheidsupdates op een driemaandelijkse basis vrij maar behoudt zich het recht voor om hotfixes voor belangrijke veiligheidsbedreigingen vrij te geven die op prioriteit en andere factoren worden gebaseerd.

Zie de volgende bronnen voor informatie over beschikbare Adobe Commerce-versies, releasecycli en het upgrade- en patchproces:

- [Uitgebrachte versies](../../../release/versions.md)
- [ Beschikbaarheid van het Product ](../../../release/product-availability.md) (de diensten van Adobe Commerce en Adobe-Authored uitbreidingen)
- [Adobe Commerce-levenscyclusbeleid](../../../release/lifecycle-policy.md)
- [Upgradehandleiding](../../../upgrade/overview.md)
- [Patches toepassen](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Krijg de recentste veiligheidsinformatie en verlicht tegen bekende veiligheidskwesties door aan de [ Dienst van het Bericht van de Veiligheid van Adobe ](https://www.adobe.com/subscription/adbeSecurityNotifications.html) in te tekenen.

## Een noodherstelplan ontwikkelen

Als uw Commerce-site in gevaar is, kunt u schade snel beheersen en normale bedrijfsactiviteiten snel herstellen door een uitgebreid herstelplan voor noodsituaties te ontwikkelen en uit te voeren.

Als een klant bij een noodsituatie een Commerce-instantie moet herstellen, kan Adobe de klant back-upbestanden verschaffen. De klant en de oplossingenintegrator, indien van toepassing, kunnen herstellen.

Als deel van een rampenherstelplan, adviseert Adobe hoogst dat de klanten [ hun de toepassingsconfiguratie van Adobe Commerce ](../../../configuration/cli/export-configuration.md) uitvoeren om herplaatsing te verlichten als het voor bedrijfscontinuïteitsdoeleinden wordt vereist. De primaire reden om de configuratie naar het dossiersysteem uit te voeren is dat de systeemconfiguratie belangrijkheid over de gegevensbestandconfiguratie neemt. In een alleen-lezen bestandssysteem moet de toepassing opnieuw worden geïmplementeerd om gevoelige configuratie-instellingen te wijzigen, waardoor een extra laag van beveiliging wordt geboden.

### Aanvullende informatie

**Adobe Commerce die op wolkeninfrastructuur wordt opgesteld**

- [ Steun en rampenterugwinning ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=nl-NL#backup-and-disaster-recovery)

- [ het configuratiebeheer van de opslag voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=nl-NL)

**Adobe Commerce die op gebouw** wordt opgesteld

- [Configuratieinstellingen exporteren](../../../configuration/cli/export-configuration.md)

   - [Configuratieinstellingen importeren](../../../configuration/cli/import-configuration.md)

   - [Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien](../../../installation/tutorials/backup.md)

## Beveiligde site en infrastructuur onderhouden

Deze sectie vat beste praktijken voor het handhaven van plaats en infrastructuurveiligheid voor een installatie van Adobe Commerce samen. Veel van deze beste praktijken richten zich op het beveiligen van de computerinfrastructuur in het algemeen, zodat zouden sommige van de aanbevelingen reeds kunnen worden uitgevoerd.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Blok onbevoegde toegang** - het Werk met uw het ontvangen partner aan opstelling een tunnel van VPN om onbevoegde toegang tot de plaats van Commerce en klantengegevens te blokkeren. Stel een SSH-tunnel in om onbevoegde toegang tot de Commerce-toepassing te blokkeren.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Gebruik een Firewall van de Toepassing van het Web** - analyseer verkeer en ontdek verdachte patronen, zoals creditcardinformatie die naar een onbekend IP adres wordt verzonden door een Firewall van de Toepassing van het Web te gebruiken.

De installaties van Adobe Commerce die op wolkeninfrastructuur worden opgesteld kunnen de ingebouwde diensten van WAF gebruiken beschikbaar met de [ Vaste de dienstenintegratie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=nl-NL)

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **vormt geavanceerde montages van de wachtwoordveiligheid** - opstelling sterke wachtwoorden en verander hen minstens om de 90 dagen, zoals die door de Standaard van de Veiligheid van Gegevens PCI in sectie 8.2.4 worden geadviseerd. Zie [ Admin veiligheidsmontages ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=nl-NL) vormen.

![ Checklist ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Gebruik HTTPS** - als de plaats van Commerce nieuw wordt uitgevoerd, lanceer de volledige plaats gebruikend HTTPS. Niet alleen gebruikt Google HTTPS als een waarderingsfactor, maar veel gebruikers overwegen zelfs niet om van een site aan te schaffen, tenzij deze is beveiligd met HTTPS.

## Beschermen tegen malware

Malware-aanvallen die gericht zijn op e-commercesites, komen maar al te vaak voor en bedreigende actoren ontwikkelen voortdurend nieuwe manieren om creditcard en persoonlijke informatie van transacties te verzamelen.

Adobe heeft echter vastgesteld dat de meeste compromissen tussen sites niet te wijten zijn aan een innovatieve hacker. Eerder, halen de bedreigingsacteurs vaak voordeel uit bestaande, niet gestapelde kwetsbaarheid, slechte wachtwoorden, en zwakke eigendom en toestemmingsmontages in het dossiersysteem.

In de meest algemeen ervaren aanvallen, wordt de kwaadwillige code geïnjecteerd in de absolute kopbal of absolute footer van een klantenopslag. In dat geval verzamelt de code formuliergegevens die een klant in de winkel invoert, waaronder aanmeldingsgegevens van de klant en gegevens van het uitcheckformulier. Vervolgens worden deze gegevens voor kwaadaardige doeleinden naar een andere locatie verzonden in plaats van naar de Commerce-backend. Ook kan malware de Admin in gevaar brengen om code uit te voeren die het originele betalingsformulier vervangt door een nep formulier dat de door de betalingsdienstaanbieder ingestelde bescherming vervangt.

Clientside credit card-skaters zijn een type malware dat code insluit in commerciële website-inhoud die kan worden uitgevoerd in de browser van een gebruiker, zoals in de volgende afbeelding wordt getoond.

![ stroom van Gegevens voor malware aanvallen gericht op e-commercesites ](../../../assets/playbooks/malware-data-flow.svg)

Nadat bepaalde acties plaatsvinden zoals een gebruiker die een formulier verzendt of een veldwaarde wijzigt, serialiseert de skimmer de gegevens en verzendt het naar eindpunten van derden. Deze eindpunten zijn typisch andere gecompromitteerde websites die als relais handelen om de gegevens naar zijn definitieve bestemming te verzenden.


>[!TIP]
>
>Als een plaats van Commerce door een malware aanval wordt beïnvloed, volg de beste praktijken van Adobe Commerce voor [ antwoordend aan een veiligheidsincident ](../maintenance/respond-to-security-incident.md).

### Kennis van de meest voorkomende aanvallen

Hieronder volgt een lijst met gangbare categorieën aanvallen die Adobe alle klanten van Commerce aanbeveelt bewust te zijn van en maatregelen te nemen tegen:

- **plaats deOnder ogen ziet** - een aanvaller beschadigt een website door de visuele verschijning van de plaats te veranderen of hun eigen berichten toe te voegen. Hoewel de toegang tot de site en gebruikersaccounts in gevaar is gebracht, blijven betalingsgegevens vaak veilig.

- **Botnets** - de server van Commerce van de klant wordt deel van een botnet die spame-mail verzendt. Hoewel gebruikersgegevens typisch niet gecompromitteerd zijn, zou de het domeinnaam van de klant door spamfilters kunnen worden gevoegd op lijst van gewenste personen, verhinderend levering van om het even welke e-mail van het domein. Alternatief, wordt de plaats van de klant deel van een botnet die een verdeelde ontkenning van de dienst (DDoS) aanval op een andere plaats/s veroorzaakt. Botnet kan binnenkomend IP verkeer aan de server van Commerce blokkeren, verhinderend klanten om te kunnen winkelen.

- **Directe serveraanvallen** - het Gegevens wordt gecompromitteerd, achterdeuren en malware worden geïnstalleerd, en de plaatsverrichtingen worden beïnvloed. De betalingsinformatie die niet op de server wordt opgeslagen zal minder waarschijnlijk door deze aanvallen worden gecompromitteerd.

- **Silent kaart vangt** - in deze rampzalige aanval, installeren indringers verborgen malware of kaart vangt software, of erger, wijzigen het controleproces om creditcardgegevens te verzamelen. Vervolgens worden de gegevens naar een andere site verzonden en op het donkere web te koop aangeboden. Dergelijke aanvallen kunnen voor een langere periode onopgemerkt blijven en in groot compromis van klantenrekeningen en financiële informatie resulteren.

- **Onmiddellijke keylogging** - de bedreigingsactor installeert zeer belangrijke registrerende code op de klantenserver om Admin gebruikersgeloofsbrieven te verzamelen zodat kunnen zij login en andere aanvallen lanceren zonder worden ontdekt.

### Beschermen tegen aanvallen met wachtwoordschattingen

Het wachtwoord van de brute macht die aanvallen veronderstelt kan in onbevoegde toegang Admin resulteren. Bescherm uw site tegen deze aanvallen door de volgende tips uit te voeren:

- Identificeer en bescherm alle punten waar de installatie van Commerce van de buitenwereld kan worden betreden.

  U kunt toegang tot Admin beveiligen, die over het algemeen de meeste bescherming vereist, door Adobe [ prioritaire aanbevelingen ](#priority-recommendations) te volgen wanneer het vormen van uw project van Commerce.

- De toegang van de controle tot de plaats van Commerce door opstelling een toegangsbeheerlijst die slechts toegang tot gebruikers toestaat die uit een gespecificeerd IP adres of netwerk komen.

  U kunt snel Edge ACL met een codefragment van douaneVCL gebruiken om inkomende verzoeken te filtreren en toegang door IP adres toe te staan. Zie [ Douane VCL voor het toestaan van verzoeken ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=nl-NL).


  >[!TIP]
  >
  >Als u een extern personeel in dienst neemt, zorg ervoor dat de IP adressen van verre werknemers in de lijst van adressen met toestemming om tot de plaats van Commerce toegang te hebben inbegrepen zijn.

### Klikaanvallen voorkomen

Adobe beschermt uw winkel tegen aanvallen door te klikken en biedt de `X-Frame-Options` HTTP-aanvraagheader die u kunt opnemen in aanvragen bij uw winkel. Zie [ verhinderen klikjacking exploiteert ](../../../configuration/security/xframe-options.md) in de *Gids van de Configuratie van Adobe Commerce*.

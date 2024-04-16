---
title: Uw Commerce-site en -infrastructuur beveiligen
description: Behoud beveiliging door best practices voor beveiliging te implementeren wanneer u Adobe Commerce-installaties instelt, configureert en bijwerkt.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '2004'
ht-degree: 0%

---

# Uw Commerce-site en -infrastructuur beveiligen

Het creëren en onderhouden van een veilige omgeving voor Adobe Commerce-projecten die worden geïmplementeerd op cloudinfrastructuur is een verantwoordelijkheid die wordt gedeeld door Adobe Commerce-klanten, oplossingspartners en Adobe. De bedoeling van deze handleiding is om beste praktijken voor de kant van de klant van de vergelijking te verstrekken.

Hoewel u niet alle veiligheidsrisico&#39;s kunt elimineren, verhardt het toepassen van deze beste praktijken de veiligheidshouding van de installaties van Commerce. Een veilige plaats en een infrastructuur maken een minder aantrekkelijk doel voor kwaadwillige aanvallen, verzekert de veiligheid van de oplossing en de gevoelige informatie van de klanten, en helpt veiligheid-gerelateerde incidenten minimaliseren die plaatsverstoringen en dure onderzoeken kunnen veroorzaken.

>[!NOTE]
>
>Voor informatie over de rollen en verantwoordelijkheden voor het beveiligen en onderhouden van Adobe Commerce-projecten op het gebied van cloudinfrastructuur raadpleegt u de [Gids voor gedeelde verantwoordelijkheid](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) in het Adobe Trust Center.

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Prioritaire aanbevelingen

Adobe beschouwt de volgende aanbevelingen als van de hoogste prioriteit voor alle klanten. Implementeer deze belangrijke best practices voor beveiliging in alle Commerce-implementaties:

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Twee-factor verificatie inschakelen voor uw Admin en alle SSH-verbindingen**

- [Beveiliging voor Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [Beveiligde SSH-verbindingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) (cloudinfrastructuur)

Wanneer MFA op een project wordt toegelaten, moet alle Adobe Commerce op de rekeningen van de wolkeninfrastructuur met de toegang van SSH een authentificatiewerkschema volgen. Voor deze workflow is een tweevoudige verificatie (2FA)-code of een API-token en SSH-certificaat vereist om toegang te krijgen tot de omgeving.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **De beheerder beveiligen**

- [Een niet-standaard beheer-URL configureren](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) in plaats van de standaardinstelling `admin` of een gemeenschappelijke term zoals `backend`. Deze configuratie beperkt de blootstelling aan manuscripten die proberen om onbevoegde toegang tot uw plaats te krijgen.

- [Geavanceerde beveiligingsinstellingen configureren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)—Voeg een geheime sleutel aan URLs toe, vereist wachtwoorden om case-sensitive te zijn, en beperk de zittingslengte Admin, het interval van het wachtwoordleven, en het aantal login pogingen toegestaan alvorens een Admin gebruikersrekening te sluiten. Voor verhoogde veiligheid, vorm de lengte van toetsenbordinactiviteit alvorens de huidige zitting verloopt, en vereist de gebruikersbenaming en het wachtwoord om case-sensitive te zijn.

- [ReCAPTCHA inschakelen](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) om de Admin te beschermen tegen geautomatiseerde aanvallen van bloedvergieten.

- Volg het beginsel van minst voorrecht wanneer het toewijzen [Beheerdersmachtigingen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) aan rollen en rollen aan Admin gebruikersrekeningen.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Upgrade naar de nieuwste versie van Adobe Commerce**

Uw code laten bijwerken door [Commerce-project upgraden naar de nieuwste release](#upgrade-to-the-latest-release) van Adobe Commerce, Commerce Services en extensies, waaronder beveiligingspatches, hotfixes en andere patches die door Adobe worden geleverd.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Beveilig gevoelige configuratiewaarden**

Gebruiken [configuratiebeheer](../../../configuration/cli/set-configuration-values.md) om kritieke configuratiewaarden te sluiten.

De `lock config` en `lock env` CLI-opdrachten configureren omgevingsvariabelen om te voorkomen dat deze worden bijgewerkt via de Admin. De opdracht schrijft de waarde naar de `<Commerce base dir>/app/etc/env.php` bestand. (Voor Commerce over infrastructuurprojecten in de cloud gaat u naar [Beheer van winkelconfiguratie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).)

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Beveiligingsscans uitvoeren**

Gebruik de [Commerce Security Scan-service](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) om alle Adobe Commerce-sites te controleren op bekende beveiligingsrisico&#39;s en malware en u aan te melden voor patchupdates en beveiligingsmeldingen.

## Beveiliging van extensies en aangepaste code

Wanneer u Adobe Commerce uitbreidt door extensies van derden toe te voegen vanuit de Adobe Commerce Marketplace of door aangepaste code toe te voegen, dient u de beveiliging van deze aanpassingen te garanderen door de volgende aanbevolen procedures toe te passen:

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Kies een partner of oplossingsintegrator (SI) goed verdraaid in veiligheid**—Zorgen voor veilige integratie en veilige levering van aangepaste code door organisaties te selecteren die veilige ontwikkelingspraktijken volgen en een solide staat van dienst hebben bij het voorkomen en aanpakken van beveiligingsproblemen.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Beveiligde extensies gebruiken**—Identificeer de meest aangewezen en veilige uitbreidingen voor de plaatsingen van Commerce door met uw oplossingsintegrator of ontwikkelaar en volgende te overleggen [Aanbevolen werkwijzen voor extensies voor Adoben](../planning/extensions.md).

- Alleen bronextensies van de Adobe Commerce Marketplace of via de integrator van de oplossing. Als de extensie via een integrator wordt aangeschaft, moet u ervoor zorgen dat de eigendom van de extensievergunning overdraagbaar is, voor het geval de integrator verandert.

- Verminder risicoblootstelling door het aantal uitbreidingen en verkopers te beperken.

- Controleer indien mogelijk de beveiligingscode van de extensie voordat u deze integreert met de Commerce-toepassing.

- Ervoor zorgen dat ontwikkelaars van PHP-extensies de Adobe Commerce-ontwikkelrichtlijnen, -processen en best practices op het gebied van beveiliging volgen. Concreet moeten ontwikkelaars het gebruik van PHP-mogelijkheden vermijden die tot de uitvoering van een externe code of een zwakke cryptografie kunnen leiden. Zie [Beveiliging](https://developer.adobe.com/commerce/php/best-practices/security/) in de *Aanbevolen werkwijzen voor de Handleiding voor ontwikkelaars van extensies*.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Controlecode**—Controleer uw server en broncodeopslagplaats voor ontwikkelingsleftovers. Zorg ervoor dat er geen toegankelijke logboekdossiers, openbaar zichtbare.git folders, tunnels zijn om SQL verklaringen, gegevensbestanddumps, php- informatiedossiers, of andere onbeschermde dossiers uit te voeren die niet worden vereist, en die in een aanval zouden kunnen worden gebruikt.

## Upgrade naar de nieuwste versie

De Adobe geeft voortdurend bijgewerkte oplossingscomponenten vrij om veiligheid te verbeteren en klanten beter tegen mogelijk compromis te beschermen. De upgrade naar de nieuwste versie van de Adobe Commerce-toepassing, geïnstalleerde services en extensies en het toepassen van huidige patches is de eerste en beste verdedigingslinie tegen beveiligingsrisico&#39;s.

Commerce geeft typisch veiligheidsupdates op een driemaandelijkse basis vrij maar behoudt zich het recht voor om hotfixes voor belangrijke veiligheidsbedreigingen vrij te geven die op prioriteit en andere factoren worden gebaseerd.

Zie de volgende bronnen voor informatie over beschikbare Adobe Commerce-versies, releasecycli en het upgrade- en patchproces:

- [Uitgebrachte versies](../../../release/versions.md)
- [Beschikbaarheid van producten](../../../release/product-availability.md) (Adobe Commerce-services en extensies die door de Adobe zijn gemaakt)
- [Adobe Commerce-levenscyclusbeleid](../../../release/lifecycle-policy.md)
- [Upgradehandleiding](../../../upgrade/overview.md)
- [Patches toepassen](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Krijg de recentste veiligheidsinformatie en verlicht tegen bekende veiligheidskwesties door aan te tekenen aan [Service voor beveiligingskennisgeving van Adobe](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Een noodherstelplan ontwikkelen

Als uw Commerce-site in gevaar is, kunt u schade snel beheersen en normale bedrijfsactiviteiten snel herstellen door een uitgebreid herstelplan voor noodsituaties te ontwikkelen en uit te voeren.

Als een klant bij een noodsituatie een Commerce-instantie moet herstellen, kan de Adobe de klant back-upbestanden verschaffen. De klant en de oplossingenintegrator, indien van toepassing, kunnen herstellen.

Als onderdeel van een noodherstelplan raadt Adobe klanten ten zeerste aan [hun Adobe Commerce-toepassingsconfiguratie exporteren](../../../configuration/cli/export-configuration.md) om de herschikking te vergemakkelijken indien dit nodig is voor bedrijfscontinuïteitsdoeleinden. De primaire reden om de configuratie naar het dossiersysteem uit te voeren is dat de systeemconfiguratie belangrijkheid over de gegevensbestandconfiguratie neemt. In een alleen-lezen bestandssysteem moet de toepassing opnieuw worden geïmplementeerd om gevoelige configuratie-instellingen te wijzigen, waardoor een extra laag van beveiliging wordt geboden.

### Aanvullende informatie

**Adobe Commerce geïmplementeerd op cloudinfrastructuur**

- [Back-up en noodherstel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [Configuratiebeheer voor opslag voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce ter plaatse ingezet**

- [Ideeën voor noodherstel](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Back-up en herstel](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Configuratieinstellingen exporteren](../../../configuration/cli/export-configuration.md)

   - [Configuratieinstellingen importeren](../../../configuration/cli/import-configuration.md)

   - [Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien](../../../installation/tutorials/backup.md)

## Beveiligde site en infrastructuur onderhouden

Deze sectie vat beste praktijken voor het handhaven van plaats en infrastructuurveiligheid voor een installatie van Adobe Commerce samen. Veel van deze beste praktijken richten zich op het beveiligen van de computerinfrastructuur in het algemeen, zodat zouden sommige van de aanbevelingen reeds kunnen worden uitgevoerd.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Onbevoegde toegang blokkeren**—Werk met uw het ontvangen partner aan opstelling een tunnel van VPN om onbevoegde toegang tot de plaats en klantengegevens van Commerce te blokkeren. Stel een SSH-tunnel in om onbevoegde toegang tot de Commerce-toepassing te blokkeren.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Een webtoepassingsfirewall gebruiken**—Analyseer verkeer en ontdek verdachte patronen, zoals creditcardinformatie die naar een onbekend IP adres wordt verzonden door een Firewall van de Toepassing van het Web te gebruiken.

Adobe Commerce-installaties die op cloudinfrastructuur worden geïmplementeerd, kunnen gebruikmaken van ingebouwde WAF-services die beschikbaar zijn via de [Snelle integratie van diensten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Geavanceerde beveiligingsinstellingen voor wachtwoorden configureren**—Stel sterke wachtwoorden in en wijzig deze ten minste elke 90 dagen, zoals wordt aanbevolen door de PCI-gegevensbeveiligingsstandaard in sectie 8.2.4. Zie [Beveiligingsinstellingen voor Admin configureren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS gebruiken**—Als de Commerce-site nieuw is geïmplementeerd, start u de hele site met HTTPS. Niet alleen gebruikt Google HTTPS als een waarderingsfactor, maar veel gebruikers overwegen zelfs niet om van een site aan te schaffen, tenzij deze is beveiligd met HTTPS.

## Protect tegen malware

Malware-aanvallen die gericht zijn op e-commercesites, komen maar al te vaak voor en bedreigende actoren ontwikkelen voortdurend nieuwe manieren om creditcard en persoonlijke informatie van transacties te verzamelen.

De Adobe heeft echter vastgesteld dat de meeste compromissen op de site niet te wijten zijn aan een innovatieve hacker. Eerder, halen de bedreigingsacteurs vaak voordeel uit bestaande, niet gestapelde kwetsbaarheid, slechte wachtwoorden, en zwakke eigendom en toestemmingsmontages in het dossiersysteem.

In de meest algemeen ervaren aanvallen, wordt de kwaadwillige code geïnjecteerd in de absolute kopbal of absolute footer van een klantenopslag. In dat geval verzamelt de code formuliergegevens die een klant in de winkel invoert, waaronder aanmeldingsgegevens van de klant en gegevens van het uitcheckformulier. Vervolgens worden deze gegevens voor kwaadaardige doeleinden naar een andere locatie verzonden in plaats van naar de Commerce-backend. Ook kan malware de Admin in gevaar brengen om code uit te voeren die het originele betalingsformulier vervangt door een nep formulier dat de door de betalingsdienstaanbieder ingestelde bescherming vervangt.

Clientside credit card-skaters zijn een type malware dat code insluit in commerciële website-inhoud die kan worden uitgevoerd in de browser van een gebruiker, zoals in de volgende afbeelding wordt getoond.

![De stroom van gegevens voor malware aanvallen die e-handelplaatsen richten](../../../assets/playbooks/malware-data-flow.svg)

Nadat bepaalde acties plaatsvinden zoals een gebruiker die een formulier verzendt of een veldwaarde wijzigt, serialiseert de skimmer de gegevens en verzendt het naar eindpunten van derden. Deze eindpunten zijn typisch andere gecompromitteerde websites die als relais handelen om de gegevens naar zijn definitieve bestemming te verzenden.


>[!TIP]
>
>Als een Commerce-site wordt beïnvloed door een malware-aanval, volgt u de Adobe Commerce best practices voor [reageren op een beveiligingsincident](../maintenance/respond-to-security-incident.md).

### Kennis van de meest voorkomende aanvallen

Hieronder volgt een lijst van gemeenschappelijke categorieën aanvallen die de Adobe alle klanten van Commerce adviseert om zich van bewust te zijn en maatregelen te nemen tegen:

- **Site is defect**—Een aanvaller beschadigt een website door de visuele weergave van de site te wijzigen of eigen berichten toe te voegen. Hoewel de toegang tot de site en gebruikersaccounts in gevaar is gebracht, blijven betalingsgegevens vaak veilig.

- **Botnets**—De Commerce-server van de klant wordt onderdeel van een onderkant die spam-e-mail verzendt. Hoewel gebruikersgegevens typisch niet gecompromitteerd zijn, zou de het domeinnaam van de klant door spamfilters kunnen worden gevoegd op lijst van gewenste personen, verhinderend levering van om het even welke e-mail van het domein. Alternatief, wordt de plaats van de klant deel van een botnet die een verdeelde ontkenning van de dienst (DDoS) aanval op een andere plaats/s veroorzaakt. Botnet kan binnenkomend IP verkeer aan de server van Commerce blokkeren, verhinderend klanten om te kunnen winkelen.

- **Directe serveraanvallen**—Gegevens worden gecompromitteerd, achterdeuren en malware worden geïnstalleerd, en plaatshandelingen worden beïnvloed. De betalingsinformatie die niet op de server wordt opgeslagen zal minder waarschijnlijk door deze aanvallen worden gecompromitteerd.

- **Geluidskaart vastleggen**—In deze meest rampzalige aanval, installeren indringers verborgen malware of kaartvangsoftware, of erger, wijzigen het controleproces om creditcardgegevens te verzamelen. Vervolgens worden de gegevens naar een andere site verzonden en op het donkere web te koop aangeboden. Dergelijke aanvallen kunnen voor een langere periode onopgemerkt blijven en in groot compromis van klantenrekeningen en financiële informatie resulteren.

- **Stil sleutelregistreren**—De bedreigingsactor installeert zeer belangrijke registrerencode op de klantenserver om gebruikersgeloofsbrieven te verzamelen Admin zodat kunnen zij login en andere aanvallen lanceren zonder worden ontdekt.

### Protect tegen aanvallen met een wachtwoord

Het wachtwoord van de brute macht die aanvallen veronderstelt kan in onbevoegde toegang Admin resulteren. Protect uw site van deze aanvallen op de volgende manier:

- Identificeer en bescherm alle punten waar de installatie van Commerce van de buitenwereld kan worden betreden.

  U kunt toegang tot Admin, die over het algemeen de meeste bescherming vereist, beveiligen door de Adobe te volgen [prioritaire aanbevelingen](#priority-recommendations) wanneer u uw Commerce-project configureert.

- De toegang van de controle tot de plaats van Commerce door opstelling een toegangsbeheerlijst die slechts toegang tot gebruikers toestaat die uit een gespecificeerd IP adres of netwerk komen.

  U kunt Snelle Rand ACL met een codefragment van douaneVCL gebruiken om inkomende verzoeken te filtreren en toegang door IP adres toe te staan. Zie [Aangepaste VCL voor het toestaan van aanvragen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >Als u een extern personeel in dienst neemt, zorg ervoor dat de IP adressen van verre werknemers in de lijst van adressen met toestemming om tot de plaats van Commerce toegang te hebben inbegrepen zijn.

### Klikaanvallen voorkomen

De Adobe beschermt uw opslag tegen klikaanvallen door te verstrekken `X-Frame-Options` HTTP- verzoekkopbal die u in verzoeken aan uw winkel kunt omvatten. Zie [Klikaanvallen voorkomen](../../../configuration/security/xframe-options.md) in de *Adobe Commerce-configuratiegids*.

---
title: Overzicht van het upgradeproces
description: Leer hoe u met de upgrade van uw Adobe Commerce- en Magento Open Source-project uw winkel veilig en efficiënt kunt laten werken.
source-git-commit: 517e38aa5b0f413503fdb7ba00be8c605cceb570
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---


# Overzicht van het upgradeproces

Het upgraden van uw Adobe Commerce- of Magento Open Source-project is van essentieel belang om ervoor te zorgen dat uw winkel veilig blijft, voldoet aan PCI en optimaal functioneert. Deze handleiding is ontwikkeld om u door de belangrijkste overwegingen te laten lopen wanneer u zich voorbereidt op een upgrade.

De gids geeft een overzicht van de typische Adobe Commerce/Magento Open Source upgrade-reis en de beste praktijken om die reis te volgen. De documentatie bevat ook technische details van het upgradeproces met een tijdig voorbeeld en stapsgewijze instructies voor de upgrade naar Adobe Commerce/Magento Open Source versie 2.4.4. De patchrelease van 2.4.4 is over het algemeen beschikbaar op 8 maart 2022. Het is daarom belangrijk om vroeg met de voorbereiding van deze upgrade te beginnen, omdat de [Einde levenscyclus (EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) in 2022 komen de datums voor zowel de 2.3-regel als de versies 2.4.0 tot en met 2.4.3 dichterbij. Tot slot verstrekken wij planningsmiddelen en verbeteringshulpmiddelen die uw verbeteringsproces efficiënter maken.

## Voor wie is deze gids?

Het doelpubliek voor deze handleiding is:

### Handelsleiders en technische directeuren

Deze gids helpt klanten in deze rollen de verbeteringsreis begrijpen, het belang van regelmatige bevordering, en hoe te om voor een verbetering het beste te plannen en voor te bereiden.

### Operationele en ontwikkelingsteams

Deze gids helpt deze teams de technische stappen leren die worden vereist om aan 2.4.4 (of om het even welke versie van Adobe Commerce/Magento Open Source) te bevorderen en de hulpmiddelen die zij kunnen gebruiken om het proces gemakkelijker, sneller, en betaalbaarder te maken.

## Upgradeproces uitgelegd

Een van de redenen waarom je hebt gekozen voor Adobe Commerce/Magento Open Source, is waarschijnlijk:

- Brede out-of-the-box functieset
- SaaS-functies die los van de kerncode worden aangeboden
- Robuust aanbod van Marketplace-extensies
- De unieke mogelijkheid om onbeperkte flexibiliteit toe te staan, zodat u uw site zo kunt aanpassen dat deze het best aansluit bij de behoeften van uw bedrijf en klanten.

Het voordeel van een zeer uitbreidbaar en aanpasbaar product, echter, kan potentiële verbeteringskwesties veroorzaken wanneer de aanpassingen niet aan beste praktijken worden gecodeerd, die tot hoger-dan-verwachte verbeteringskosten leiden.

_Dus... waarom een upgrade ?_

Door een upgrade uit te voeren, kunt u uw bedrijf eenvoudig blijven in de snelle en voortdurend veranderende eCommerce-branche en kunt u uw platform altijd compatibel maken met de nieuwste functies die u helpen uw verkoop en conversies te maximaliseren. Het opnemen van upgrades in uw reguliere onderhoudsplannen is ook van essentieel belang om ervoor te zorgen dat uw winkel veilig blijft, voldoet aan PCI en zo efficiënt mogelijk werkt.

### Beveiliging

Veiligheid is één van de belangrijkste redenen om te bevorderen aangezien 83% van veiligheidsincidenten op verouderde software voorkomt. Volgens [IBM](https://www.ibm.com/security/data-breach)De gemiddelde kosten van een inbreuk op gegevens zijn $ 3,86 miljoen, veel hoger dan wat het kost om dit risico te beperken door een upgrade. Adobe biedt twee manieren om uw winkel het hele jaar veilig te houden:

- **Patchreleases**—Neem oplossingen voor beveiligingsproblemen, prestaties, kwaliteit en problemen met hoge prioriteit op.
- **Beveiligingspatchreleases**—Neem correcties en verbeteringen op om uw site veilig te houden en de site is eenvoudiger te implementeren.

### Prestaties

Prestaties zijn een andere belangrijke reden voor een upgrade. Volgens [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), hebben de eerste vijf seconden van de laadtijd een significant effect op de omrekeningskoersen en heeft elke seconde van latentie daarna een effect van -4,4%. Dat, samen met het feit dat paginasnelheid een belangrijke SEO rangschikkingsfactor is, aantoont waarom plaatsprestaties een kritiek element van uw plaats zijn om te handhaven en regelmatig te verbeteren. Elke flardversie omvat prestatiesverbeteringen, zodat steunt het voordeel van nieuwe versies uw groeiplannen en houdt uw zaken concurrerend.

### Kosten van vertraging

De reden voor het uitstellen of uitstellen van platformupgrades is vaak de directe kosten. Nochtans, zijn de echte kosten om een verouderde versie van om het even welke software in werking te stellen veel groter en kunnen een blijvende invloed op een zaken hebben.

Het lijkt misschien contraintuïtief, maar het uitvoeren van regelmatige platformupdates vereist minder algemene inspanningen dan het uitvoeren van niet-frequente updates vanwege het bedrag van de geaccumuleerde technische schuld die het gevolg is van vertragingen. We hebben onlangs samengewerkt met een partner die een detailhandelaar heeft die altijd zelden en inconsistent (jaarlijks of langer) upgrades uitvoerde. Door te transformeren hoe zij verbeteringen en na een Adobe-geadviseerde regelmatige verbeteringsweg in de loop van 12 maanden naderen, kon de partner de cliënt vier weken&#39; waarde van cumulatieve ontwikkelingstijd, inspanning, en bijbehorende kosten besparen, die allen aan initiatieven werden opnieuw gericht die bedrijfsgroei drijven.

Wanneer de updates regelmatig worden uitgevoerd, zijn de veranderingen stijgende en de overeenkomstige verbeteringsinspanning wijst op dit. Wanneer platformupdates gedurende een langere periode worden uitgesteld, kunnen ze een veel meer betrokken proces worden. Bovendien worden de extensies die u gebruikt vanuit de [Marketplace](https://marketplace.magento.com/) en eventuele andere integraties van derden kunnen ook worden beïnvloed. Tot slot duurt het langer om een vertraagde upgrade te onderzoeken, te plannen en uit te voeren, wat vermijdbare inspanningen en kosten met zich meebrengt.

Enkele algemene factoren die van invloed zijn op de mate van inspanning om uw project te upgraden, zijn onder andere:

| Technische complexiteit | Planning en strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Omvang van aanpassingen | Duidelijkheid van vereisten, het nemen van beslissingen en bereik |
| Aantal extensies | Uw upgradfrequentie |
| Aantal integraties met derden (OMS, ERP) | Uw teststrategie |
| Codering naar beste praktijken |  |

De voortdurende groei in de digitale handelruimte heeft verhoogde druk op ondernemingen toegepast om sneller, vaker, en op onvoorspelbare manieren te evolueren. Als de klant zijn aankoopgedrag niet kon bijhouden en niet kon anticiperen, heeft het speelveld zelfs voor de grootste, meest gevestigde merken gelijk gemaakt. U moet robuuste, gepersonaliseerde ervaringen op alle aanraakpunten kunnen bieden, zonder prestatieverlies en uptime. Je moet sneller kunnen innoveren, zonder beperkingen, om voor de mondiale concurrenten te blijven. Door een upgrade uit te voeren, kunt u uw bedrijf in de toekomst controleren en uzelf instellen op betere service en dynamische klantenbehoeften.

## Overzicht van release 2022

Adobe publiceert een [releaseplanning](https://devdocs.magento.com/release/) om het planningsproces van handelaren te vergemakkelijken en raadt u aan elke patchreleasecyclus te upgraden. Om PCI-compatibel te blijven, moeten handelaren op de nieuwste patch of beveiligingspatch zitten. In de volgende tijdlijn ziet u de belangrijkste release- en EOL-gebeurtenissen in 2022.

![](../assets/upgrade-guide/2022-release-timeline.png)

Belangrijke gebeurtenissen die u kunt opmerken zijn:

- 2.3.x de lijn bereikt Einde van Steun (EOS) in September 2022
- 2.4.0 tot 2.4.3 (gebaseerd op PHP 7.4) bereikt EOS in november 2022, toen PHP 7.4 End of Life (EOL) bereikt
- Gebaseerd op deze twee EOS-gebeurtenissen, **het is belangrijk om tegen november 2022 te upgraden naar versie 2.4.4 of hoger**
- In overeenstemming met de Adobe Commerce [levenscyclusbeleid](https://devdocs.magento.com/release/lifecycle-policy.html), versies 2.4.4 en 2.4.5, krijgen tot november 2024 ondersteuning voor kwaliteit en beveiligingspatches


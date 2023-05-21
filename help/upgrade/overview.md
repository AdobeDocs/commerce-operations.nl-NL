---
title: Overzicht van het upgradeproces
description: Leer hoe u uw Adobe Commerce-project kunt upgraden om uw winkel veilig en efficiënt te laten werken.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Overzicht van het upgradeproces

Het upgraden van uw Adobe Commerce-project is van essentieel belang om ervoor te zorgen dat uw winkel veilig blijft, voldoet aan PCI en optimaal functioneert. Deze gids begeleidt u door zeer belangrijke overwegingen wanneer het voorbereiden van een verbetering.

De gids geeft een overzicht van de typische Adobe Commerce upgrade-reis en de beste praktijken om die reis te volgen. Het beschrijft ook technische details van het verbeteringsproces met een geschikte voorbeeld en geleidelijke instructies voor verbetering aan de recentste versie van Adobe Commerce. Het is belangrijk om de Adobe Commerce te beoordelen [releaseplanning](../release/schedule.md) en begin vroegtijdig voor verbeteringen voor te bereiden. Adobe publiceert de releaseplanning jaarlijks om het planningsproces van verkopers te vergemakkelijken en raadt aan elke patchreleasecyclus te upgraden. Om PCI-compatibel te blijven, moeten handelaren op de nieuwste patch of beveiligingspatch zitten.

## Voor wie is deze gids?

Het doelpubliek voor deze handleiding is:

- **Bedrijfsleiders en technisch directeuren van de e-handel**—Begrijp de verbeteringsreis, het belang om regelmatig te verbeteren, en hoe te om op een verbetering te plannen en voor te bereiden.
- **Operationele en ontwikkelingsteams**—Leer de technische stappen die nodig zijn om te upgraden naar de nieuwste versie van Adobe Commerce en de tools die beschikbaar zijn om het proces eenvoudiger, sneller en betaalbaarder te maken.

## Upgradeproces uitgelegd

Een van de redenen die je hebt gekozen voor Adobe Commerce, is waarschijnlijk:

- Brede out-of-the-box functieset
- SaaS-functies die los van de kerncode worden aangeboden
- Robuust aanbod van Marketplace-extensies
- De unieke mogelijkheid om onbeperkte flexibiliteit toe te staan, zodat u uw site zo kunt aanpassen dat deze het beste aansluit bij de behoeften van uw bedrijf en klanten

Het voordeel van een zeer uitbreidbaar en aanpasbaar product, echter, kan potentiële verbeteringskwesties veroorzaken wanneer de aanpassingen niet aan beste praktijken worden gecodeerd, die tot hoger-dan-verwachte verbeteringskosten leiden.

_Dus... waarom een upgrade ?_

Door een upgrade uit te voeren, kunt u uw bedrijf in de razendsnelle en voortdurend veranderende e-commercesector blijven werken en kunt u uw platform compatibel maken met de nieuwste Adobe Commerce-functies die u helpen uw verkoop en conversies te maximaliseren. Het opnemen van upgrades in uw reguliere onderhoudsplannen is van essentieel belang om ervoor te zorgen dat uw winkel veilig blijft, voldoet aan PCI en zo efficiënt mogelijk werkt.

### Beveiliging

Beveiliging is een van de belangrijkste redenen voor een upgrade omdat 83% van de beveiligingsincidenten met verouderde software plaatsvindt. Volgens [IBM](https://www.ibm.com/reports/data-breach)De gemiddelde kosten van een inbreuk op gegevens zijn $ 3,86 miljoen, veel hoger dan wat het kost om dit risico te beperken door een upgrade. Adobe biedt twee manieren om uw winkel het hele jaar veilig te houden:

- **Patchreleases**—Neem oplossingen voor beveiligingsproblemen, prestaties, kwaliteit en problemen met hoge prioriteit op.
- **Beveiligingspatchreleases**—Neem correcties en verbeteringen op om uw site veilig te houden en de site is eenvoudiger te implementeren.

### Prestaties

Prestaties zijn een andere belangrijke reden voor een upgrade. Volgens [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), hebben de eerste vijf seconden van de laadtijd een significant effect op de omrekeningskoersen en heeft elke seconde van latentie daarna een effect van -4,4%. Dat, samen met het feit dat paginasnelheid een belangrijke SEO rangschikkingsfactor is, aantoont waarom plaatsprestaties een kritiek element van uw plaats zijn om te handhaven en regelmatig te verbeteren. Elke flardversie omvat prestatiesverbeteringen, zodat steunt het voordeel van nieuwe versies uw groeiplannen en houdt uw zaken concurrerend.

### Kosten van vertraging

De reden voor het uitstellen of uitstellen van platformupgrades is vaak de directe kosten. Nochtans, zijn de echte kosten om een verouderde versie van om het even welke software in werking te stellen veel groter en kunnen een blijvende invloed op een zaken hebben.

Het lijkt misschien contraintuïtief, maar het uitvoeren van regelmatige platformupdates vereist minder algemene inspanningen dan het uitvoeren van niet-frequente updates vanwege het bedrag van de geaccumuleerde technische schuld die het gevolg is van vertragingen. Adobe heeft onlangs samengewerkt met een partner die een detailhandelaar heeft die vroeger zelden en inconsistent (jaarlijks of langer) upgrades uitvoerde. Door te transformeren hoe zij verbeteringen naderen en een Adobe-geadviseerde regelmatige verbeteringsweg in de loop van 12 maanden te volgen, kon de partner de cliënt vier weken&#39; waarde van cumulatieve ontwikkelingstijd, inspanning, en bijbehorende kosten besparen. Deze kosten zouden dan kunnen worden omgeleid naar initiatieven om de groei van het bedrijfsleven te stimuleren.

Wanneer de updates regelmatig worden uitgevoerd, zijn de veranderingen stijgende en de overeenkomstige verbeteringsinspanning wijst op dit. Wanneer platformupdates gedurende een langere periode worden uitgesteld, kunnen ze een veel meer betrokken proces worden. Bovendien worden de extensies die u gebruikt vanuit de [Adobe Commerce Marketplace](https://marketplace.magento.com/) en andere integratie van derden kan ook worden beïnvloed. Tot slot duurt het langer om een vertraagde upgrade te onderzoeken, te plannen en uit te voeren, wat vermijdbare inspanningen en kosten met zich meebrengt.

Enkele algemene factoren die van invloed zijn op de mate van inspanning om uw project te upgraden, zijn onder andere:

| Technische complexiteit | Planning en strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Omvang van aanpassingen | Duidelijkheid van vereisten, het nemen van beslissingen en bereik |
| Aantal extensies | Uw upgradfrequentie |
| Aantal integraties met derden (OMS, ERP) | Uw teststrategie |
| Codering naar beste praktijken |  |

De voortdurende groei in de digitale handelruimte heeft verhoogde druk op ondernemingen toegepast om sneller, vaker, en op onvoorspelbare manieren te evolueren. Als de klant zijn aankoopgedrag niet kon bijhouden en niet kon anticiperen, heeft het speelveld zelfs voor de grootste, meest gevestigde merken gelijk gemaakt. U moet robuuste, gepersonaliseerde ervaringen op alle aanraakpunten kunnen bieden, zonder prestatieverlies en uptime. Je moet sneller kunnen innoveren, zonder beperkingen, om voor de mondiale concurrenten te blijven. Door een upgrade uit te voeren, kunt u uw bedrijf in de toekomst controleren en uzelf instellen op betere service en dynamische behoeften van klanten.

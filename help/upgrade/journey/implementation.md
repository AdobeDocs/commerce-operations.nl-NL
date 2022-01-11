---
title: Upgrade uitvoeren
description: Leer over de verschillende fasen van verbeteringsimplementatie voor Adobe Commerce en Magento Open Source projecten.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 1%

---


# Upgrade uitvoeren

De implementatie van de upgrade bestaat uit vijf fasen:

- Upgradeanalyse
- Ontwikkeling en kwaliteitsborging
- Gebruikerstoepassingstest (UAT) en voorbereiding op het starten
- Starten
- Na het starten

## Upgradeanalyse

Analyse is waarschijnlijk het belangrijkste onderdeel van het upgradeproces. Een goed uitgevoerde analyse bespaart u tijd en beperkt verrassingen in de toekomst. Het resultaat van deze fase zou een gedetailleerde verbeteringscontrolelijst en document met alle gebiedsdelen moeten zijn.

De volgende punten kunnen u in een grondige analyse willen omvatten:

- **Toepassingsgebied van doelversie**—Documentatie over [Handelsversie DevDocs](https://devdocs.magento.com) en de informatie van de partnerversie webinars verstrekt alle details u over uw doelverbetering moet weten.

- **Resultaten van het gereedschap Compatibiliteit upgraden**—Dit hulpmiddel maakt om het even welke verbetering sneller en gemakkelijker door uw huidige code met de code van de doelversie te vergelijken en een rapport van alle kwesties te produceren die moeten worden behandeld. Zie de [Compatibiliteit upgraden](../upgrade-compatibility-tool/overview.md). Belangrijkste details uit het verslag zijn:

   - Huidige geïnstalleerde versie
   - Doelversie van upgrade
   - Aantal en details van aangetroffen kritieke fouten

- De diensten van de verbetering om doelversie te steunen. Gebruik het volgende lijstmalplaatje om uit in kaart te brengen welke diensten u moet bevorderen. Gebruik de [systeemvereisten](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) om te bepalen wat u aan de _Upgrade uitvoeren naar_ kolom.


   | Service | Huidige versie | Upgrade uitvoeren naar | Notities |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.2.33. | 8,1 |  |
   | Redis | 5,05 | 6,0 |  |
   | KonijnMQ | 3,7 | 3,8 | Momenteel niet gebruikt, maar we moeten overwegen het te gebruiken |
   | MariaDB (cloud) | 10.2.33. | 10,4 |  |
   | MySQL | 8,0 |  |  |
   | Composer | 1.9.2. | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Uitbreidingen en modules van derden**—Gebruik deze tabelsjabloon om u te helpen de status van uw extensies en aanpassingen te begrijpen, zodat u strategische beslissingen kunt nemen en acties kunt definiëren. Dit is een gelegenheid om extensies te vervangen die native zijn voor Adobe Commerce of Magento Open Source om de complexiteit van uw project te minimaliseren. Gebruik de `bin/magento module:status` gebruiken om een lijst met modules en extensies weer te geven.

   | Aantal | Extensie/<br>modulenaam | Composer-pakket | Leverancier | Huidige versie | Functionaliteit | Compatibel met nieuwste<br>Handelsversie? | Problemen | Inheems voor handel? | Handeling | Notities |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Naam en koppeling van extensie | extension/<br>extensionx-magento-2 | Naam leverancier | Versie geïnstalleerd | Bedrijfsvereisten | Ja/Nee | Lijst met geïdentificeerde problemen waarmee deze extensie wordt geconfronteerd | Ja/Nee | Behouden/vervangen/<br>Verwijderen |  |

- **Aangepaste modules**—Vergelijkbaar met de lijst van derdemodules, helpt dit malplaatje u de status en de acties volgen en begrijpen die voor de bevordering van douanemodules worden vereist.

   | Aantal | Modulenaam | Functionaliteit | Vereist? | Inheems voor handel? | Handeling | Notities |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Modulenaam | Bedrijfsvereisten | Ja/Nee | Ja/Nee | Behouden/vervangen/verwijderen |  |

- **Composer-pakketten en afhankelijkheden in composer.json die een update vereisen.**

Daarnaast kunnen partners deelnemen aan de [Adobe Commerce Beta-programma](https://devdocs.magento.com/release/beta-program.html) en gebruik pre-releasemogelijkheden om vroege toegang tot de code voor een aanstaande versie te krijgen. Als ontwikkelaars vroegtijdig toegang krijgen tot de code, kunnen ze zich voorbereiden op voldoende tijd om de upgrade te voltooien op de datum van de algemene beschikbaarheid (GA). De bètacode wordt doorgaans vijf weken vóór de GA-datum vrijgegeven en de pre-releases worden twee weken van tevoren vrijgegeven. Voor versie 2.4.4, begon Adobe bètecode vijf maanden vóór de datum GA (8 Maart, 2022) vrij te geven, zodat kunnen de partners beginnen nu voor die verbetering voor te bereiden [aanmelden voor het programma](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Ontwikkeling en kwaliteitscontrole

Het testen is de fase van een verbetering die de meeste tijd vereist. Dit proces moet daarom zo geautomatiseerd mogelijk zijn. De _[Testhandleiding voor toepassingen](https://devdocs.magento.com/guides/v2.4/test/testing.html)_ Hier vindt u informatie over het instellen en gebruiken van platform- en systeemtestprogramma&#39;s voor snellere kwaliteitscontrole. Gebruik een testomgeving om de upgrade te testen en te valideren voordat u overschakelt naar de productie.

## UAT en voorbereiding voor introductie

UAT is één van de laatste stadia van de verbetering die het herzien en het bevestigen van de plaats vereist. U moet ook beslissen wanneer u wilt implementeren en of u een onderhoudspagina nodig hebt. Plan de processen en berichten van derden.

Aangezien de plaatsingsdatum bijna trekt, is de mededeling essentieel. Als meer mensen weten over de verandering aan de horizon, hoe het hen beïnvloedt, en hoe zij het moeten aanpakken, dan zult u eerder een succesvolle lancering hebben. Wees niet bang om elke stap van de weg over te communiceren - het verhoogt de kans dat revisies van iedereen die betrokken is worden gevergd zodra u live gaat!

## Starten

Voltooi de upgrade door te implementeren naar productie en extensies bij te werken. Zorg ervoor u kritieke wegstromen met gesimuleerde orden test. Bekijk deze [best practices](../prepare/best-practices.md) voor sommige tips over het lanceren met minimale problemen.

Volg uw communicatieplan en zorg ervoor dat alle belanghebbenden op de hoogte zijn van de upgrade en volledig zijn opgeleid om deze te ondersteunen.

Tot slot wil u uw team vragen lessen te leren en valkuilen te bepalen. Deze terugblik helpt u om het proces de volgende keer te verbeteren.

## Na starten

Nadat uw site is gestart, controleert u de analysegegevens, de Google Search Console en andere bronnen om te controleren of er geen onverwachte problemen zijn en of alles werkt zoals u had verwacht.

Het is altijd een goed idee om de prestaties in de gaten te houden door middel van goed ontworpen controlemiddelen. U kunt de prestaties van uw site op veel verschillende manieren controleren, dus kies er een die goed overeenkomt met uw organisatie. We raden Adobe Commerce-klanten die ons beheersysteem voor cloudinfrastructuur gebruiken aan gebruik te maken van services zoals [Nieuw bericht](https://devdocs.magento.com/cloud/project/new-relic.html) om de prestaties van de site te controleren.

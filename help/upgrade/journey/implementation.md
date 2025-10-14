---
title: Upgrade uitvoeren
description: Leer over de verschillende fasen van verbeteringsimplementatie voor de projecten van Adobe Commerce.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
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

- **Reikwijdte van doelversie** - Documentatie op [&#x200B; Experience League &#x200B;](../../release/release-notes/overview.md) en informatie van de webinars van de partnerversie verstrekken alle details u over uw doelverbetering moet weten.

- **[!DNL Upgrade Compatibility Tool]resultaten** - dit hulpmiddel maakt om het even welke verbetering sneller en gemakkelijker door uw huidige code aan de code van de doelversie te vergelijken en een rapport van alle kwesties te veroorzaken die moeten worden behandeld. Zie de [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) . Belangrijkste details uit het verslag zijn:

   - Huidige geïnstalleerde versie
   - Doelversie van upgrade
   - Aantal en details van aangetroffen kritieke fouten

  >[!TIP]
  >
  >Al deze informatie (en meer) is beschikbaar in het Plaats-brede hulpmiddel van de Analyse [&#x200B; dashboard &#x200B;](../../tools/site-wide-analysis-tool/dashboard.md).

- De diensten van de verbetering om doelversie te steunen. Gebruik het volgende lijstmalplaatje om uit in kaart te brengen welke diensten u moet bevorderen. Gebruik de [&#x200B; systeemvereisten &#x200B;](../../installation/system-requirements.md) om te bepalen wat aan de _Verbetering aan_ kolom toe te voegen.


  | Service | Huidige versie | Upgrade uitvoeren naar | Notities |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Momenteel niet gebruikt, maar we moeten overwegen het te gebruiken |
  | MariaDB (cloud) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Composer | 1.9.2. | 2,2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Uitbreidingen en derdemodules** - gebruik dit lijstmalplaatje om u te helpen het statuut van uw uitbreidingen en aanpassingen begrijpen, zodat u strategische besluiten kunt nemen en acties bepalen. Dit is een gelegenheid om extensies te vervangen die native zijn voor Adobe Commerce om de complexiteit van uw project te minimaliseren. Gebruik de opdracht `bin/magento module:status` om een lijst met modules en extensies weer te geven.

  | Aantal | Extension/<br> modulenaam | Composer-pakket | Leverancier | Huidige versie | Functionaliteit | Compatibel met recentste <br> versie van Commerce? | Problemen | Native voor Commerce? | Handeling | Notities |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Naam en koppeling van extensie | extensionx-magento-2<br> | Naam leverancier | Versie geïnstalleerd | Zakelijke vereisten | Ja/Nee | Lijst met geïdentificeerde problemen waarmee deze extensie wordt geconfronteerd | Ja/Nee | Behouden/vervangen/<br> verwijderen |       |

- **modules van de Douane** - Gelijkaardig aan de lijst van derdemodules, helpt dit malplaatje u de status en de acties volgen en begrijpen die voor de bevordering van douanemodules worden vereist.

  | Aantal | Modulenaam | Functionaliteit | Vereist? | Native voor Commerce? | Handeling | Notities |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Modulenaam | Zakelijke vereisten | Ja/Nee | Ja/Nee | Behouden/Vervangen/verwijderen |       |

- **de pakketten en gebiedsdelen van Composer in composer.json die een update vereisen.**

Bovendien kunnen de partners aan [&#x200B; bètaversies van Adobe Commerce &#x200B;](../../release/beta.md) deelnemen en pre-versiemogelijkheden gebruiken om vroege toegang tot de code voor een aanstaande versie te krijgen. Als ontwikkelaars vroegtijdig toegang krijgen tot de code, kunnen ze zich voorbereiden op voldoende tijd om de upgrade te voltooien op de datum van de algemene beschikbaarheid (GA). De Beta-code wordt doorgaans vijf weken voor de GA-datum vrijgegeven en de pre-releases worden twee weken van tevoren vrijgegeven.

## Ontwikkeling en kwaliteitscontrole

Het testen is de fase van een verbetering die de meeste tijd vereist. Dit proces moet daarom zo geautomatiseerd mogelijk zijn. De _[het Testen Gids van de Toepassing &#x200B;](https://developer.adobe.com/commerce/testing/guide/)_ verstrekt details op hoe te opstelling en gebruik platform en systeem testende hulpmiddelen voor snellere QA. Gebruik een testomgeving om de upgrade te testen en te valideren voordat u overschakelt naar de productie.

## UAT en voorbereiding voor introductie

UAT is één van de laatste stadia van de verbetering die het herzien en het bevestigen van de plaats vereist. U moet ook beslissen wanneer u wilt implementeren en of u een onderhoudspagina nodig hebt. Plan de processen en berichten van derden.

Aangezien de plaatsingsdatum bijna trekt, is de mededeling essentieel. Als meer mensen weten over de verandering aan de horizon, hoe het hen beïnvloedt, en hoe zij het moeten aanpakken, dan zult u eerder een succesvolle lancering hebben. Wees niet bang om elke stap van de weg over te communiceren - het verhoogt de kans dat revisies van iedereen die betrokken is worden gevergd zodra u live gaat!

## Starten

Voltooi de upgrade door te implementeren naar productie en extensies bij te werken. Zorg ervoor u kritieke wegstromen met gesimuleerde orden test. Controle uit deze [&#x200B; beste praktijken &#x200B;](../prepare/best-practices.md) voor sommige uiteinden bij lancering met minimale kwesties.

Volg uw communicatieplan en zorg ervoor dat alle belanghebbenden op de hoogte zijn van de upgrade en volledig zijn opgeleid om deze te ondersteunen.

Tot slot wil u uw team vragen lessen te leren en valkuilen te bepalen. Deze terugblik helpt u om het proces de volgende keer te verbeteren.

## Na starten

Nadat uw site is gestart, controleert u de analysegegevens, de Google Search Console en andere bronnen om te controleren of er geen onverwachte problemen zijn en of alles werkt zoals u had verwacht.

Het is altijd een goed idee om de prestaties in de gaten te houden door middel van goed ontworpen controlemiddelen. U kunt de prestaties van uw site op veel verschillende manieren controleren, dus kies er een die goed overeenkomt met uw organisatie. Wij adviseren dat de klanten van Adobe Commerce die ons systeem van het beheer van de wolkeninfrastructuur gebruiken uit de diensten zoals [&#x200B; New Relic &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=nl-NL) voordeel halen om plaatsprestaties te controleren.

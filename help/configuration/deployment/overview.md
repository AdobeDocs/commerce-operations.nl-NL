---
title: Overzicht van implementatie
description: Lees meer over implementatiestrategieën voor de Commerce-toepassing.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Overzicht van implementatie

Deze onderwerpen bespreken het proces om de toepassing van Commerce aan een productiesite voor Adobe Commerce versie 2.2 en later op te stellen. Adobe raadt deze implementatiemethode aan voor iedereen met een grote site die tijdens de implementatie geen downtime wil ervaren.

Als u Commerce op één enkele machine opstelt en wat onderbreking tijdens plaatsing kan tolereren, zie [ enig-machine plaatsing ](../deployment/single-machine.md).

## Implementatie van pijpleidingen

Met versie 2.2 van Commerce, introduceerde Adobe _pijpleidingsplaatsing_ als nieuwe manier om aan productie met minimale onderbreking op te stellen. Dit plaatsingsproces komt op verschillende systemen voor en verstrekt een manier om verenigbare configuraties voor alle systemen van de pijpleidingsplaatsing te handhaven. Het is een eenvoudig maar krachtig model dat u toelaat om gewone configuratiemontages van of systeem-specifieke montages (zoals gastheer en haven) of gevoelige montages (zoals namen en wachtwoorden) te scheiden.

Om pijpleidingsplaatsing te gebruiken, veronderstelt Adobe dat u bent:

- Een ervaren systeemintegrator met uitstekende kennis van Adobe Commerce-configuratieopties.
- Het beheren van een grote Commerce-site (duizenden SKU&#39;s (stock-keeping units)) en de downtime van productiesites tot een minimum beperken.
- Kennelijk van PHP programmeren.
- Ervaren met broncontrolemethoden.
- Uw code bevindt zich in een broncontroleopslagplaats. In deze handleiding gaan we ervan uit dat u een op Git gebaseerde opslagplaats gebruikt.

### Minder downtime

Wanneer u statische elementen implementeert en code compileert op een andere computer dan uw productiesysteem, minimaliseert u de downtime. Downtime op uw productiesysteem is beperkt tot de tijd die nodig is om statische bestanden en gecompileerde code naar de server over te brengen.

## Implementatiesystemen

Wij gebruiken de volgende termijnen om de systemen te beschrijven betrokken bij plaatsing.

- **systeem van de Ontwikkeling** - machine waarop de ontwikkelaars werken om code aan te passen; en uitbreidingen, thema&#39;s, en taalpakketten van Commerce Marketplace te installeren. Bovendien brengt u alle configuratieveranderingen op uw ontwikkelingssysteem aan. U kunt vele ontwikkelingssystemen hebben.

- **bouwt systeem** - één systeem waarop u statische activa opstelt en code voor uw productiesysteem compileert. Omdat u deze middelen bouwt op een systeem dat niet in productie is, wordt de onderbreking van uw productiesysteem geminimaliseerd.

  Commerce hoeft niet op uw constructiesysteem te zijn geïnstalleerd. Er is alleen de Commerce-code voor nodig, maar er is geen databaseverbinding vereist. Ook, te hoeven uw bouwstijlsysteem niet om een fysisch afzonderlijke server te zijn.

- **het Opvoeren systeem** - _Facultatief_. U kunt desgewenst een testsysteem instellen dat wordt gebruikt voor het testen van alle geïntegreerde code, inclusief het testen van gebruikersacceptatie (UAT). Stel een testsysteem in op dezelfde manier als u een productiesysteem instelt. Behalve het feit dat het opvoeren niet uw levende opslag is en geen orden van klanten verwerkt, is het identiek aan productie.

- **systeem van de Productie** - Uw levende opslag. U zou minimale directe configuratieveranderingen hier moeten aanbrengen, en zeker niets dat niet op een het Plaatsen instantie is getest. Indien mogelijk, breng configuratieveranderingen met [ Patches van Gegevens ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) aan die op een het Opvoeren/van de Ontwikkeling instantie zijn getest.

## Andere implementatiemethoden

Naar keuze, kunt u andere plaatsingsmethodes gebruiken, die omvatten:

- Veilig kopiëren met SCP of synchroniseren
- [ Capistrano ](https://capistranorb.com/documentation/overview/what-is-capistrano)
- Het [ hulpmiddel van de Laag ](https://deployer.org/)

## De configuratie beheren

Het modelleren na [ factor 3 in het 12-factor toepassingsontwerp ](https://12factor.net/config), Commerce slaat nu de configuratie voor elk systeem in het systeem zelf op. (De de configuratiemontages van de ontwikkeling worden opgeslagen op het ontwikkelingssysteem, worden de productiemontages opgeslagen op het productiesysteem.)

Wij bieden een manier om de configuratie van uw systemen te synchroniseren:

- **Gedeelde configuratie** - Montages die noch systeem-specifiek noch gevoelig zijn.

  De gedeelde montages zijn montages die u op ontwikkelings en productiesystemen verenigbaar wilt zijn. Plaats de gedeelde configuratie in Admin in uw ontwikkeling (of Adobe Commerce op de integratie van de wolkeninfrastructuur __) systeem.

  Het gedeelde configuratiedossier, `app/etc/config.php`, zou in broncontrole moeten worden omvat zodat kan het tussen ontwikkelings, bouwstijl, en productiesystemen worden gedeeld.

- **systeem-specifieke configuratie** - Montages die door systeem, zoals onderzoekmachine hostnames en havens variëren.

- **Gevoelige configuratie** - Montages die _niet_ in broncontrole zou moeten zijn omdat zij persoonlijk identificeerbare informatie (PII) of montages zoals API sleutels of wachtwoorden blootstellen.

  Het systeem-specifieke configuratiedossier, `app/etc/env.php`, zou _niet_ in broncontrole moeten worden omvat of anders tussen systemen worden gedeeld. In plaats daarvan, gebruik [`magento config:set` en `magento:sensitive:set` bevelen ](../cli/set-configuration-values.md) om waarden voor die montages in uw productiesysteem te verstrekken.

>[!INFO]
>
>Deze nieuwe methoden voor het beheer van uw configuratie zijn optioneel. U hoeft dit niet te doen, maar het wordt sterk aanbevolen om ze te gebruiken.

Meestal kunnen de configuratieopties die u instelt in de gedeelde, systeemspecifieke of gevoelige configuratie niet worden bewerkt in de beheerfunctie. Hierdoor blijven uw instellingen op alle systemen consistent. (U kunt optioneel de opdracht [`magento config:set` ](../cli/set-configuration-values.md) zonder de optie `--lock` gebruiken om instellingen te configureren die kunnen worden bewerkt in Beheer.)

Elke de configuratieoptie van Commerce heeft een uniek _configuratiepad_. Om een waarde voor een configuratieoptie te plaatsen, kunt u of een bevel CLI of een omgevingsvariabele gebruiken om de waarde voor die configuratiepad op een specifiek systeem te plaatsen.

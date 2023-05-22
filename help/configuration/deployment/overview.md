---
title: Overzicht van implementatie
description: Lees over plaatsingsstrategieën voor de toepassing van de Handel.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Overzicht van implementatie

Deze onderwerpen bespreken het proces om de toepassing van de Handel aan een productiesite voor Adobe Commerce versie 2.2 en later op te stellen. Adobe raadt deze implementatiemethode aan voor iedereen met een grote site die tijdens de implementatie geen downtime wil ervaren.

Als u Handel op één enkele machine opstelt en wat onderbreking tijdens plaatsing kan tolereren, zie [Eén computer implementeren](../deployment/single-machine.md).

## Implementatie van pijpleidingen

Met Commerce versie 2.2 is Adobe geïntroduceerd _pijplijnimplementatie_ als een nieuwe manier om op productie met minimale onderbreking te zetten. Dit plaatsingsproces komt op verschillende systemen voor en verstrekt een manier om verenigbare configuraties voor alle systemen van de pijpleidingsplaatsing te handhaven. Het is een eenvoudig maar krachtig model dat u toelaat om gewone configuratiemontages van of systeem-specifieke montages (zoals gastheer en haven) of gevoelige montages (zoals namen en wachtwoorden) te scheiden.

Om pijpleidingsplaatsing te gebruiken, veronderstelt Adobe dat u bent:

- Een ervaren systeemintegrator met uitstekende kennis van Adobe Commerce-configuratieopties.
- Het beheren van een grote plaats van de Handel (duizenden eenheden van de voorraadboekhouding (SKUs)) en wil de onderbreking van de productiesite tot een minimum beperken.
- Kennelijk van PHP programmeren.
- Ervaren met broncontrolemethoden.
- Uw code bevindt zich in een broncontroleopslagplaats. In deze handleiding gaan we ervan uit dat u een op Git gebaseerde opslagplaats gebruikt.

### Minder downtime

Wanneer u statische activa opstelt en code op een machine los van uw productiesysteem compileert, minimaliseert u onderbreking. Downtime op uw productiesysteem is beperkt tot de tijd die nodig is om statische bestanden en gecompileerde code naar de server over te brengen.

## Implementatiesystemen

Wij gebruiken de volgende termijnen om de systemen te beschrijven betrokken bij plaatsing.

- **Ontwikkelingssysteem**—machine waarop ontwikkelaars werken om code aan te passen; en installeer extensies, thema&#39;s en taalpakketten van Commerce Marketplace. Bovendien brengt u alle configuratieveranderingen op uw ontwikkelingssysteem aan. U kunt vele ontwikkelingssystemen hebben.

- **Systeem bouwen**—Één systeem waarop u statische activa opstelt en code voor uw productiesysteem compileert. Omdat u deze middelen bouwt op een systeem dat niet in productie is, wordt de onderbreking van uw productiesysteem geminimaliseerd.

   Uw bouwstijlsysteem moet geen Handel hebben op het worden geïnstalleerd. Het vereist slechts de code van de Handel maar geen gegevensbestandverbinding wordt vereist. Ook, te hoeven uw bouwstijlsysteem niet om een fysisch afzonderlijke server te zijn.

- **Stapelsysteem**—_Optioneel_. U kunt desgewenst een testsysteem instellen dat wordt gebruikt voor het testen van alle geïntegreerde code, inclusief het testen van gebruikersacceptatie (UAT). Stel een testsysteem in op dezelfde manier als u een productiesysteem instelt. Behalve het feit dat het opvoeren niet uw levende opslag is en geen orden van klanten verwerkt, is het identiek aan productie.

- **Productiesysteem**—Je live winkel. U zou minimale directe configuratieveranderingen hier moeten aanbrengen, en zeker niets dat niet op een het Plaatsen instantie is getest. Breng indien mogelijk configuratiewijzigingen aan met [Gegevenspatches](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) die zijn getest op een instantie Staging/Development.

## Andere implementatiemethoden

Naar keuze, kunt u andere plaatsingsmethodes gebruiken, die omvatten:

- Veilig kopiëren met SCP of synchroniseren
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- De [Gereedschap Implementatie](https://deployer.org/)

## De configuratie beheren

Modellering na [factor 3 in het 12-factor toepassingsontwerp](https://12factor.net/config), slaat de Handel nu de configuratie voor elk systeem in het systeem zelf op. (De de configuratiemontages van de ontwikkeling worden opgeslagen op het ontwikkelingssysteem, worden de productiemontages opgeslagen op het productiesysteem.)

Wij bieden een manier om de configuratie van uw systemen te synchroniseren:

- **Gedeelde configuratie**—Instellingen die niet systeemspecifiek of gevoelig zijn.

   De gedeelde montages zijn montages die u op ontwikkelings en productiesystemen verenigbaar wilt zijn. Stel de gedeelde configuratie in de beheerdersconfiguratie in uw ontwikkeling in (of Adobe Commerce in de cloud-infrastructuur) _integratie_).

   Het gedeelde configuratiebestand, `app/etc/config.php`, moet worden opgenomen in broncontrole, zodat deze kan worden gedeeld tussen ontwikkelings-, bouw- en productiesystemen.

- **Systeemspecifieke configuratie**—Instellingen die per systeem variëren, zoals hostnamen en poorten van zoekprogramma&#39;s.

- **Gevoelige configuratie**—Instellingen die moeten _niet_ in broncontrole zijn omdat zij persoonlijk identificeerbare informatie (PII) of montages zoals API sleutels of wachtwoorden blootstellen.

   Het systeemspecifieke configuratiebestand, `app/etc/env.php`moet _niet_ worden opgenomen in broncontrole of anderszins worden gedeeld tussen systemen. Gebruik in plaats daarvan de [`magento config:set` en `magento:sensitive:set` opdrachten](../cli/set-configuration-values.md) om waarden voor die instellingen in uw productiesysteem op te geven.

>[!INFO]
>
>Deze nieuwe methoden voor het beheer van uw configuratie zijn optioneel. U hoeft dit niet te doen, maar het wordt sterk aanbevolen ze te gebruiken.

Meestal kunnen de configuratieopties die u instelt in de gedeelde, systeemspecifieke of gevoelige configuratie niet worden bewerkt in de beheerfunctie. Hierdoor blijven uw instellingen op alle systemen consistent. (U kunt optioneel de opdracht [`magento config:set` command](../cli/set-configuration-values.md) zonder `--lock` om instellingen te configureren die kunnen worden bewerkt in de beheerfunctie.)

Elke de configuratieoptie van de Handel heeft uniek _configuratiepad_. Om een waarde voor een configuratieoptie te plaatsen, kunt u of een bevel CLI of een omgevingsvariabele gebruiken om de waarde voor die configuratiepad op een specifiek systeem te plaatsen.

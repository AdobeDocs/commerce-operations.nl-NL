---
title: Statische inhoudcache
description: Krijg inzicht in het ondertekenen van statische inhoud en hoe u de functie kunt in- of uitschakelen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Statische inhoudcache

Om de prestaties te verbeteren, stelt de Handel `Expires` headers voor statische bronnen, zoals afbeeldingen, JavaScript- en CSS-bestanden.
De instelling `Expires` header op een statische resource vertelt de browser dat de resource op die URL in cache moet worden geplaatst en dat de versie in de cache moet worden verzonden totdat deze verloopt.
Dit is een algemene [beste praktijken](https://developer.yahoo.com/performance/rules.html#expires=) voor het in cache plaatsen van statische bronnen.

Wanneer de browser een statische bron in cache plaatst en die resource op de server verandert, moet u het cachegeheugen van de browser wissen, zodat de nieuwe versie kan worden gedownload.
Het handmatig wissen van de browsercache werkt als u een [website](https://glossary.magento.com/website) beheerder, maar dit is geen aangewezen verzoek om van uw gebruikers te maken wanneer u hen nieuwe versies van een statische middel wilt downloaden.

## Statische ondertekening van inhoud

[Statische inhoud](https://glossary.magento.com/static-content) het ondertekenen is een eigenschap van de Handel die u toestaat om het browser geheime voorgeheugen voor statische middelen ongeldig te maken.
De handel verwezenlijkt dit door een plaatsingsversie aan URL van toe te voegen [statische bestanden](https://glossary.magento.com/static-files).

Hieronder ziet u een voorbeeld van een URL die is ondertekend met een versie:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wanneer u de opdracht uitvoert [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) om statische inhoud op te stellen, verandert de Handel automatisch de plaatsingsversie.
Hierdoor wordt de URL van de statische bestanden gewijzigd en wordt de browser gedwongen de nieuwe versie van de bestanden te laden.

De handel laat deze eigenschap door gebrek toe, en Adobe raadt aan om deze eigenschap te houden die kwesties met betrekking tot browsers te verhinderen die omhoog oude statische middelen dienen.

U kunt de configuratie voor deze functie vinden in [**[!UICONTROL Stores]**> Instellingen > Configuratie >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![Instellingen Statische bestanden](../../assets/configuration/static-files-settings.png)

De status bepalen:

```bash
bin/magento config:show dev/static/sign
```

Ondertekening van statische inhoud in- of uitschakelen:

```bash
bin/magento config:set dev/static/sign <value>
```

Wanneer `<value>` is 1 (ingeschakeld) of 0 (uitgeschakeld).

## Versiehandtekeningen

De handel voegt de versiehandtekening als wegcomponent direct na basisURL van statische meningsdossiers toe om de integriteit van relatieve URLs over statische middelen te bewaren.
Hierdoor wordt de browser ook gedwongen een relatieve URL op te lossen ten opzichte van de correcte ondertekende bron, terwijl de inhoud onafhankelijk blijft van de aanwezigheid/afwezigheid van de handtekeningwaarde.

Wanneer een browser een ondertekende bron opvraagt bij de server, gebruikt de server de URL opnieuw om de handtekeningcomponent van de URL te verwijderen.

## Gebruik tijdens implementaties

Na het bevorderen van of het wijzigen van statische middelen, moet u in werking stellen `setup:static-content:deploy` gebruiken om de versie in te voeren en de statische inhoud bij te werken, die browser dwingt om de bijgewerkte middelen te laden.

Als u code op een afzonderlijke server implementeert en deze naar productie verplaatst met behulp van een code-opslagplaats om downtime te verminderen, moet u ook het bestand toevoegen `pub/static/deployed_version.txt` naar de gegevensopslagruimte.
Dit bestand bevat de nieuwe versie voor de geïmplementeerde statische inhoud.

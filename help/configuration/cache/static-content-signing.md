---
title: Statische inhoudcache
description: Meer informatie over het ondertekenen van statische inhoudcache en het optimaliseren van prestaties in Adobe Commerce. Ontdek hoe u caching-functies kunt inschakelen, uitschakelen en configureren.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Statische inhoudcache

Om de prestaties te verbeteren, stelt Commerce de `Expires` -headers in voor statische bronnen, zoals afbeeldingen, JavaScript- en CSS-bestanden.
Als u de header `Expires` instelt op een statische bron, geeft u de browser de opdracht de bron in de cache bij die URL in te stellen en de versie in de cache te verzenden tot deze is verlopen.
Dit is een gemeenschappelijke [ beste praktijk ](https://developer.yahoo.com/performance/rules.html#expires=) voor het in cache plaatsen van statische middelen.

Wanneer de browser een statische bron in cache plaatst en die resource op de server verandert, moet u het cachegeheugen van de browser wissen, zodat de nieuwe versie kan worden gedownload.
Het handmatig wissen van het cachegeheugen van de browser werkt als u een websitebeheerder bent, maar dit is geen geschikte aanvraag om van uw gebruikers te maken wanneer u ze nieuwe versies van een statische bron wilt downloaden.

## Statische ondertekening van inhoud

Het statische ondertekenen van inhoud is een eigenschap van Commerce die u toestaat om het browser geheime voorgeheugen voor statische middelen ongeldig te maken.
Commerce doet dit door een implementatieversie toe te voegen aan de URL van statische bestanden.

Hieronder ziet u een voorbeeld van een URL die is ondertekend met een versie:

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wanneer u de opdracht [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) uitvoert om statische inhoud te implementeren, wijzigt Commerce automatisch de implementatieversie.
Hierdoor wordt de URL van de statische bestanden gewijzigd en wordt de browser gedwongen de nieuwe versie van de bestanden te laden.

Commerce schakelt deze functie standaard in en Adobe raadt aan deze functie ingeschakeld te houden om problemen te voorkomen die te maken hebben met browsers die oude statische bronnen gebruiken.

De configuratie voor het ondertekenen van statische inhoud vindt u in [**[!UICONTROL Stores]**> Instellingen > Configuratie >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures) .

- **slechts op-gebouw**: Deze configuratie is beschikbaar als uw plaats **niet** op [ wijze van de Productie ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode) is.
- **Wolk**: Deze configuratie is verborgen omdat de wijze van de Productie strikt wordt afgedwongen; daarom moet u de bevellijn zoals hieronder getoond gebruiken.

![ de Statische Montages van Dossiers ](../../assets/configuration/static-files-settings.png)

De status bepalen:

```bash
bin/magento config:show dev/static/sign
```

Ondertekening van statische inhoud in- of uitschakelen:

```bash
bin/magento config:set dev/static/sign <value>
```

Waar `<value>` 1 (ingeschakeld) of 0 (uitgeschakeld) is.

## Versiehandtekeningen

Commerce voegt de versiehandtekening direct na de basis-URL van statische weergavebestanden toe als padcomponent om de integriteit van relatieve URL&#39;s in statische bronnen te behouden.
Hierdoor wordt de browser ook gedwongen een relatieve URL op te lossen ten opzichte van de correcte ondertekende bron, terwijl de inhoud onafhankelijk blijft van de aanwezigheid/afwezigheid van de handtekeningwaarde.

Wanneer een browser een ondertekende bron opvraagt bij de server, gebruikt de server de URL opnieuw om de handtekeningcomponent van de URL te verwijderen.

## Gebruik tijdens implementaties

Nadat u de statische bronnen hebt bijgewerkt of gewijzigd, moet u de opdracht `setup:static-content:deploy` uitvoeren om de versie te implementeren en de statische inhoud bij te werken. Hierdoor wordt de browser gedwongen de bijgewerkte bronnen te laden.

Als u code implementeert op een aparte server en deze verplaatst naar productie met behulp van een code-opslagplaats om downtime te verminderen, moet u ook het bestand `pub/static/deployed_version.txt` toevoegen aan de opslagplaats.
Dit bestand bevat de nieuwe versie voor de geïmplementeerde statische inhoud.

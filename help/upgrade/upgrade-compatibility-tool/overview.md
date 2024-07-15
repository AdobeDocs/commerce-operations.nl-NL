---
title: Overzicht van  [!DNL Upgrade Compatibility Tool]
description: Leer over  [!DNL Upgrade Compatibility Tool]  en hoe het u met uw project van Adobe Commerce kan helpen.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Overzicht van hulplijnen

{{commerce-only}}

Deze handleiding is bedoeld voor beheerders en software-engineers van Adobe Commerce. Het omvat gedetailleerde informatie over installatie van [!DNL Upgrade Compatibility Tool], evenals zijn configuratie en beheer. Hierbij wordt uitgegaan van een basiskennis van de basisconfiguratie en -functionaliteit van Commerce.

## Overzicht van de [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules en kerncode controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar een nieuwere versie van Adobe Commerce uitvoert.

## De [!DNL Upgrade Compatibility Tool] gebruiken

U kunt [!DNL Upgrade Compatibility Tool] gebruiken via:

- Als standalone [ bevel-lijn interface ](../upgrade-compatibility-tool/run.md) hulpmiddel. Voor de volledige lijst van beschikbare bevelen, zie [`bin/uct` verwijzing ](../../tools/reference/uct.md).
- De [!DNL Upgrade Compatibility Tool] wordt geïntegreerd met de [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md) .
- Een looppasconfiguratie binnen de [ Magento PHPStorm stop ](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

In het volgende diagram worden de mogelijke workflows weergegeven wanneer de [!DNL Upgrade Compatibility Tool] wordt uitgevoerd:

![[!DNL Upgrade Compatibility Tool] Diagram ](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

Bekijk deze video voor meer informatie over [!DNL Upgrade Compatibility Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Help de [!DNL Upgrade Compatibility Tool]

Gebruik de volgende bronnen als u informatie nodig hebt of vragen hebt die niet in deze handleiding worden behandeld:

Om met het [!DNL Upgrade Compatibility Tool] team te verbinden, contacteer ons op het kanaal van de Slack van de Techniek [ #upgrade-verenigbaarheid-hulpmiddel ](https://magentocommeng.slack.com/archives/C019Y143U9F). We willen graag uw feedback, problemen en suggesties horen die ons helpen het gereedschap te verbeteren.

[!DNL Upgrade Compatibility Tool] gebruikt regels die binnen onze [ worden bepaald die Normen van de Codering ](https://developer.adobe.com/commerce/php/coding-standards/) om ervoor te zorgen dat uw project de beste praktijken van Adobe Commerce volgt en u te helpen verbeteren en uitbreiden [!DNL Upgrade Compatibility Tool].

Verwijs naar het [ Contribute ](https://developer.adobe.com/commerce/php/coding-standards/contributing/) onderwerp voor meer informatie bij het bijdragen van coderingsnormen.

## Bronnen

Raadpleeg de volgende bronnen voor meer informatie over upgrades voor Adobe Commerce:

- De [ verbeteringsgids ](../overview.md) verstrekt een overzicht van de typische de verbeteringsreis van Adobe Commerce en beste praktijken om langs die reis te volgen.
- De [ aanstaande versie ](https://devdocs.magento.com/release/) pagina verstrekt de data voor geplande en aanstaande versies.
- De [ communautaire middelen ](https://developer.adobe.com/commerce/contributor/community/) pagina moet plaatsen om besprekingen te beginnen, of meer informatie te vinden.
- Controleer de [ verwante hulpmiddelen ](../upgrade-compatibility-tool/related-tools.md) pagina voor nuttige hulpmiddelen in uw typische verbeteringsreis.

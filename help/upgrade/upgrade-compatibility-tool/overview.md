---
title: Overzicht van de [!DNL Upgrade Compatibility Tool]
description: Meer informatie over de [!DNL Upgrade Compatibility Tool] en hoe u hiermee kunt helpen bij uw Adobe Commerce-project.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Overzicht van hulplijnen

{{commerce-only}}

Deze handleiding is bedoeld voor beheerders en software-engineers van Adobe Commerce. Het omvat gedetailleerde informatie over installatie van [!DNL Upgrade Compatibility Tool], alsmede de configuratie en het beheer ervan. Hierbij wordt uitgegaan van een basiskennis van de basisconfiguratie en -functionaliteit van Commerce.

## Overzicht van de [!DNL Upgrade Compatibility Tool]

De [!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules en kerncode controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar een nieuwere versie van Adobe Commerce uitvoert.

## Gebruik de [!DNL Upgrade Compatibility Tool]

U kunt de [!DNL Upgrade Compatibility Tool] via:

- Als zelfstandig [opdrachtregelinterface](../upgrade-compatibility-tool/run.md) gebruiken. Voor de volledige lijst van beschikbare bevelen, zie [`bin/uct` referentie](/help/reference/uct.md).
- De [!DNL Upgrade Compatibility Tool] met de [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Een uitvoeringsconfiguratie binnen de [PHPStorm-plug-in voor Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Het volgende diagram toont de mogelijke werkschema&#39;s wanneer het runnen van [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

Bekijk deze video voor meer informatie over de [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Help de [!DNL Upgrade Compatibility Tool]

Gebruik de volgende bronnen als u informatie nodig hebt of vragen hebt die niet in deze handleiding worden behandeld:

Als u verbinding wilt maken met de [!DNL Upgrade Compatibility Tool] team, contacteer ons op het kanaal van de Slack van de Techniek [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). We willen graag uw feedback, problemen en suggesties horen die ons helpen het gereedschap te verbeteren.

De [!DNL Upgrade Compatibility Tool] gebruikt regels die binnen onze [Codeerstandaarden](https://developer.adobe.com/commerce/php/coding-standards/) om ervoor te zorgen dat uw project de beste praktijken van Adobe Commerce volgt en u te helpen verbeteren en uitbreiden [!DNL Upgrade Compatibility Tool].

Zie de [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) onderwerp voor meer informatie over het bijdragen van coderingsnormen.

## Bronnen

Raadpleeg de volgende bronnen voor meer informatie over upgrades voor Adobe Commerce:

- De [upgradehulplijn](../overview.md) biedt een overzicht van de typische Adobe Commerce upgrade-reis en de beste praktijken om deze reis te volgen.
- De [komende releases](https://devdocs.magento.com/release/) Deze pagina bevat de datums voor geplande en komende releases.
- De [communautaire middelen](https://developer.adobe.com/commerce/contributor/community/) Deze pagina is bedoeld om discussies te starten of om meer informatie te zoeken.
- Controleer de [verwante gereedschappen](../upgrade-compatibility-tool/related-tools.md) pagina voor nuttige hulpmiddelen in uw typisch verbeteringsreis.

---
title: '"Overzicht van de [!DNL Upgrade Compatibility Tool]"'
description: Meer informatie over de [!DNL Upgrade Compatibility Tool] en hoe u hiermee kunt helpen bij uw Adobe Commerce-project.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Overzicht van hulplijnen

{{commerce-only}

Deze handleiding is bedoeld voor beheerders en software-engineers van Adobe Commerce. Het omvat gedetailleerde informatie over installatie van [!DNL Upgrade Compatibility Tool], alsmede de configuratie en het beheer ervan. Het veronderstelt een basisbegrip van de kernconfiguratie en de functionaliteit van de Handel.

## Overzicht van de [!DNL Upgrade Compatibility Tool]

De [!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules en kerncode controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar een nieuwere versie van Adobe Commerce uitvoert.

## Gebruik de [!DNL Upgrade Compatibility Tool]

U kunt de [!DNL Upgrade Compatibility Tool] via:

- Als zelfstandig [opdrachtregelinterface](../upgrade-compatibility-tool/run.md) gebruiken.
- De [!DNL Upgrade Compatibility Tool] met de [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Een uitvoeringsconfiguratie binnen de [Magento PHPStorm-plug-in](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

### Workflow

Het volgende diagram toont de mogelijke werkschema&#39;s wanneer het runnen van [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/uct-diagram-v5.png)

### Help de [!DNL Upgrade Compatibility Tool]

Gebruik de volgende bronnen als u informatie nodig hebt of vragen hebt die niet in deze handleiding worden behandeld:

Als u verbinding wilt maken met de [!DNL Upgrade Compatibility Tool] team, contacteer ons op het kanaal van de Slack van de Techniek [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). We willen graag uw feedback, problemen en suggesties horen die ons helpen het gereedschap te verbeteren.

De [!DNL Upgrade Compatibility Tool] gebruikt regels die binnen onze [Codeerstandaarden](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) om ervoor te zorgen dat uw project de beste praktijken van Adobe Commerce volgt en u te helpen verbeteren en uitbreiden [!DNL Upgrade Compatibility Tool].

Zie de [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) onderwerp voor meer informatie over het bijdragen van coderingsnormen.

### Bronnen

Raadpleeg de volgende bronnen voor meer informatie over upgrades voor Adobe Commerce:

- De [upgradehulplijn](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) biedt een overzicht van de gebruikelijke Adobe Commerce- of Magento Open Source-upgradereis en van de beste praktijken om deze reis te volgen.
- De [komende releases](https://devdocs.magento.com/release/) bevat de datums voor geplande en komende releases.
- De [communautaire middelen](https://developer.adobe.com/commerce/contributor/community/) Deze pagina is bedoeld om discussies te starten of om meer informatie te zoeken.
- Controleer de [verwante gereedschappen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html) pagina voor nuttige hulpmiddelen in uw typisch verbeteringsreis.

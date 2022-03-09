---
title: Overzicht van de [!DNL Upgrade Compatibility Tool]
description: Meer informatie over de [!DNL Upgrade Compatibility Tool] en hoe u hiermee kunt helpen bij uw Adobe Commerce-project.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---


# Overzicht van de [!DNL Upgrade Compatibility Tool]

{{commerce-only}

De [!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat een aangepaste Adobe Commerce-instantie controleert op een specifieke versie door alle daarin geïnstalleerde modules en kerncode te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert. Het identificeert ook potentiële problemen die in uw code moeten worden opgelost alvorens om aan een nieuwere versie van Adobe Commerce te proberen te bevorderen.

De [!DNL Upgrade Compatibility Tool] kunt u identificeren wanneer de veranderingen van de kerncode aan aangepaste eigenschappen zijn aangebracht. Zie de [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor meer informatie.

Het wordt gedistribueerd als een Composer-pakket bij elke release van een Adobe Commerce-versie. Zie de [Ontwikkelaar](../upgrade-compatibility-tool/developer.md) voor meer informatie.

Zie de [Installeren](../upgrade-compatibility-tool/install.md) onderwerp voor de eerste stappen met het [!DNL Upgrade Compatibility Tool].

## Workflow

Het volgende diagram toont het verwachte werkschema wanneer het runnen van [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/mvp-diagram-v3.png)

## De [!DNL Upgrade Compatibility Tool] use case

In het volgende gebruiksgeval wordt het gebruikelijke proces beschreven dat een Adobe Commerce-partner moet doorvoeren om een clientexemplaar te upgraden:

1. Download de [!DNL Upgrade Compatibility Tool] pakket van de [Adobe Commerce-opslagplaats](https://repo.magento.com/). Zie de [Download de [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) voor meer informatie.
1. Voer de [!DNL Upgrade Compatibility Tool] tijdens de [bèta](https://devdocs.magento.com/release/beta-program.html) Nieuwste fase [Adobe Commerce-release](https://devdocs.magento.com/release/).
1. De belangrijkste opdracht is `upgrade:check`. Deze opdracht analyseert uw instantie en controleert op fouten, waarschuwingen en kritieke problemen in de instantie. Resultaten optimaliseren:

   - Optie Toevoegen `--ignore-current-version-compatibility-issues` om alle bekende kritieke problemen, fouten en waarschuwingen voor uw huidige Adobe Commerce-versie te negeren. Alleen resultaten van de gewenste versie worden weergegeven.
   - Optie gebruiken `--min-issue-level` om het minimumniveau van afgifte vast te stellen. Helpt slechts de belangrijkste kwesties met de verbetering voorrang te geven. Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u ook het pad opgeven. Zie de [Het gereedschap uitvoeren](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) voor meer informatie.

1. Genereer een vanilla-instantie voor de specifieke versie van Adobe Commerce die momenteel is geïnstalleerd. Zie de [Handleiding voor contribuanten](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie over het gebruik van de `instance` gebruiken om een vanilleinstallatie te genereren.

   >[!NOTE]
   >
   >Een vanilla-instantie is een schone installatie van een opgegeven versietag of vertakking voor een specifieke releaseversie.

1. De [!DNL Upgrade Compatibility Tool] Identificeert aangepaste verbroken gebieden. De software engineer is in staat de complexiteit te begrijpen en de moeite van de upgrade te schatten. Deze informatie wordt met belanghebbenden gedeeld.
1. Voor de upgrade worden een budget en een tijdschema gedefinieerd.
1. De ingenieurs van de software kunnen dan aan de vereiste codewijzigingen werken om de gebroken modules te bevestigen.
1. De [!DNL Upgrade Compatibility Tool] kan worden uitgevoerd om de voortgang van de upgrade te volgen.
1. Alles wat uitcheckt en technische processen kan de code nu naar een testomgeving verplaatsen waar regressietests bevestigen dat alle tests groen zijn, zodat ze de nieuwste Adobe Commerce-versie kunnen uitbrengen op dezelfde dag dat de Adobe Commerce voor de introductie wordt uitgebracht.

   ![[!DNL Upgrade Compatibility Tool] publiek](../../assets/upgrade-guide/audience-uct-v3.png)

## Help de [!DNL Upgrade Compatibility Tool]

Als u verbinding wilt maken met de [!DNL Upgrade Compatibility Tool] team, contacteer ons op het kanaal van de Slack van de Techniek [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). We willen graag uw feedback, problemen en suggesties horen die ons helpen het gereedschap te verbeteren.

De [!DNL Upgrade Compatibility Tool] gebruikt regels die binnen onze [Codeerstandaarden](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) om ervoor te zorgen dat uw project de beste praktijken van Adobe Commerce volgt en u te helpen verbeteren en uitbreiden [!DNL Upgrade Compatibility Tool].

Zie de [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  onderwerp voor meer informatie over het bijdragen aan dit project.

## Bronnen

We hebben de volgende bronnen ontwikkeld om u te helpen bij het begrijpen van upgrades voor Adobe Commerce:

- [Upgradehulplijn](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Volgende releases](https://devdocs.magento.com/release/)
- [Communautaire middelen](https://devdocs.magento.com/community/resources/resources.html) voor meer informatie.

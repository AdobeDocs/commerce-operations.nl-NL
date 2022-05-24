---
title: Overzicht van de [!DNL Upgrade Compatibility Tool]
description: Meer informatie over de [!DNL Upgrade Compatibility Tool] en hoe u hiermee kunt helpen bij uw Adobe Commerce-project.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Overzicht van hulplijnen

Deze handleiding is bedoeld voor beheerders en software-engineers van Adobe Commerce. Het omvat gedetailleerde informatie over installatie van [!DNL Upgrade Compatibility Tool], alsmede de configuratie en het beheer ervan. Het veronderstelt een basisbegrip van de kernconfiguratie en de functionaliteit van de Handel.

## Overzicht van de [!DNL Upgrade Compatibility Tool]

{{commerce-only}

De [!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat een aangepaste Adobe Commerce-instantie controleert op een specifieke versie door alle daarin geïnstalleerde modules en kerncode te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar een nieuwere versie van Adobe Commerce uitvoert.

Zie [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor meer informatie .

Zie [Installeren](../upgrade-compatibility-tool/install.md) voor de eerste stappen met de [!DNL Upgrade Compatibility Tool].

Zie dit [videozelfstudie](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) voor meer informatie over de [!DNL Upgrade Compatibility Tool].

### Workflow

Het volgende diagram toont de mogelijke werkschema&#39;s wanneer het runnen van [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/uct-diagram-v5.png)

### De [!DNL Upgrade Compatibility Tool] use case

In het volgende gebruiksgeval wordt het gebruikelijke proces beschreven dat een Adobe Commerce-partner moet doorvoeren om een clientexemplaar te upgraden:

1. Download de [!DNL Upgrade Compatibility Tool] pakket van de Adobe Commerce-opslagplaats (`https://repo.magento.com/`). Zie de [Download de [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) voor meer informatie.
1. Voer de [!DNL Upgrade Compatibility Tool] tijdens de [bèta](https://devdocs.magento.com/release/beta-program.html) Nieuwste fase [Adobe Commerce-release](https://devdocs.magento.com/release/).
1. Genereer een vanilla-instantie voor de specifieke versie van Adobe Commerce die momenteel is geïnstalleerd. Zie de [Handleiding voor contribuanten](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie over het gebruik van de `instance` gebruiken om een vanilleinstallatie te genereren.

   >[!NOTE]
   >
   >Een vanilla-instantie is een schone installatie van een opgegeven versietag of vertakking voor een specifieke releaseversie.

1. De [!DNL Upgrade Compatibility Tool] Identificeert verbeteringskwesties die softwareingenieurs zullen helpen de ingewikkeldheid begrijpen en de inspanning van de verbetering schatten.
1. Deze informatie wordt met belanghebbenden gedeeld.
1. Voor de upgrade worden een budget en een tijdschema gedefinieerd.
1. De ingenieurs van de software kunnen dan aan de vereiste codewijzigingen werken om de gebroken modules te bevestigen.
1. De [!DNL Upgrade Compatibility Tool] kan worden uitgevoerd om de voortgang van de upgrade te volgen.
1. Alles wat uitcheckt en technische processen kan de code nu naar een testomgeving verplaatsen waar regressietests bevestigen dat alle tests groen zijn, zodat ze de nieuwste Adobe Commerce-versie kunnen uitbrengen op dezelfde dag dat de Adobe Commerce voor de introductie wordt uitgebracht.

   ![[!DNL Upgrade Compatibility Tool] publiek](../../assets/upgrade-guide/audience-uct-v3.png)

### Help de [!DNL Upgrade Compatibility Tool]

Gebruik de volgende bronnen als u informatie nodig hebt of vragen hebt die niet in deze handleiding worden behandeld:

Als u verbinding wilt maken met de [!DNL Upgrade Compatibility Tool] team, contacteer ons op het kanaal van de Slack van de Techniek [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). We willen graag uw feedback, problemen en suggesties horen die ons helpen het gereedschap te verbeteren.

De [!DNL Upgrade Compatibility Tool] gebruikt regels die binnen onze [Codeerstandaarden](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) om ervoor te zorgen dat uw project de beste praktijken van Adobe Commerce volgt en u te helpen verbeteren en uitbreiden [!DNL Upgrade Compatibility Tool].

Zie de [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  onderwerp voor meer informatie over het bijdragen van coderingsnormen.

### Bronnen

We hebben de volgende bronnen ontwikkeld om u te helpen bij het begrijpen van upgrades voor Adobe Commerce:

- [Upgradehulplijn](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Volgende releases](https://devdocs.magento.com/release/)
- [Communautaire middelen](https://devdocs.magento.com/community/resources/resources.html) voor meer informatie.
- [Gerelateerde gereedschappen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)

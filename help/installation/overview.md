---
title: Overzicht van installatie op locatie
description: Leer over het installatieproces voor plaatsingen op-gebouw van Adobe Commerce en Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Overzicht van installatie op locatie

>[!NOTE]
>
>Het volgende diagram biedt een overzicht op hoog niveau van _**ter plaatse**_ installaties van Adobe Commerce en Magento Open Source:

![Hoe installatie werkt](../assets/installation/install-diagram-24.svg)

De algemene installatiestroom is als volgt:

1. Stel uw serveromgeving in.

   Installeer de vereiste software, waaronder PHP, Apache, MySQL en de zoekmachine. Zie de [systeemvereisten](system-requirements.md) voor meer informatie .

1. Get [verificatietoetsen](prerequisites/authentication-keys.md) aan de Composer van de Handel.

1. Haal de Adobe Commerce- of Magento Open Source-software op.

   * (Aanbevolen) Kies voor de [Composer-pakket](composer.md) om modules en hun gebiedsdelen te beheren.

   * Als u wilt bijdragen aan de Magento Open Source codebase of de toepassing wilt aanpassen, [klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) de gegevensopslagplaats GitHub. Deze methode vereist vertrouwdheid met zowel GitHub als Composer.

1. Installeer de toepassing met de opdrachtregel.

   Als de stap mislukt omdat de vereiste software niet correct is ingesteld, controleert u de [voorwaarden](prerequisites/overview.md).

1. [Verifiëren](next-steps/verify.md) de installatie door uw winkel en Admin te bekijken.


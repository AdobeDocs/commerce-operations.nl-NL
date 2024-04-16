---
title: Overzicht van voorbeeldgegevens
description: Meer informatie over het gebruik van voorbeeldgegevens voor Adobe Commerce-projecten.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Overzicht van voorbeeldgegevens

De gegevens van de steekproef verstrekken een opslag die op het thema van de Luma wordt gebaseerd dat met producten, categorieën, klantenregistratie wordt uitgerust, etc. Het werkt net als een Commerce-winkel en u kunt met de Admin de prijzen, de voorraad en de prijsregels voor speciale acties manipuleren.

>[!NOTE]
>
>Om gegevensbestand en diverse eigenschappen te herzien en te analyseren, overweeg gebruikend echte gegevens in plaats van steekproefgegevens. De gegevens van de steekproef worden ontworpen als pre-geproduceerde opslagsimulatie, om themaontwerp en basisstorefront gedrag aan te tonen. Alle entiteiten met voorbeeldgegevens worden rechtstreeks in de databasetabellen geschreven, terwijl voorbeeldgegevens worden geïnstalleerd.

U kunt voorbeeldgegevens installeren voor of na de installatie van de Commerce-software. Wanneer u klaar bent met de voorbeeldgegevens, kunt u deze verwijderen of de gegevens op de nieuwe manier installeren, zoals beschreven in [Voorbeeldgegevensmodules verwijderen of voorbeeldgegevens bijwerken](remove-or-update.md).

>[!WARNING]
>
>U kunt voorbeeldgegevens niet verwijderen. Gebruik voorbeeldgegevens alleen voor meer informatie over de werking van Adobe Commerce. Vermijd het ontwikkelen van een systeem waarin u voorbeeldgegevens hebt geïnstalleerd.

U kunt optionele voorbeeldgegevens op een van de volgende manieren installeren:

| Installatiemethode | Beschrijving | Vereist vaardigheidsniveau |
|--- |--- |--- |
| Composer gebruiken | [Uitvoeren `magento sampledata:deploy` om de hoofdmap van de toepassing te wijzigen `composer.json`](composer-packages.md) steekproefgegevensmodules in te schakelen. | Hiervoor is Composer-kennis en toegang tot het Commerce-bestandssysteem vereist. |
| Bewaarruimten klonen | [Clone the GitHub repository](git-repositories.md) en de gegevensopslagplaats van de steekproef, dan verbind hen samen. | Alleen voor bijdragende ontwikkelaars. Iedereen anders zou één van de voorafgaande methodes moeten gebruiken. |

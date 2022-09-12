---
title: Overzicht van voorbeeldgegevens
description: Meer informatie over het gebruik van voorbeeldgegevens voor Adobe Commerce- en Magento Open Source-projecten.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Overzicht van voorbeeldgegevens

De gegevens van de steekproef verstrekken een opslag die op het thema van de Luma wordt gebaseerd dat met producten, categorieën, klantenregistratie wordt uitgerust, etc. Het werkt net als een Commerce-winkel en u kunt prijzen, voorraad en promotieprijsregels manipuleren met behulp van Admin.

U kunt voorbeeldgegevens installeren voor of na de installatie van de Commerce-software. Wanneer u klaar bent met de voorbeeldgegevens, kunt u deze verwijderen of de gegevens op de nieuwe manier installeren, zoals beschreven in [Voorbeeldgegevensmodules verwijderen of voorbeeldgegevens bijwerken](remove-or-update.md).

>[!WARNING]
>
>U kunt voorbeeldgegevens niet verwijderen. We raden u aan voorbeeldgegevens alleen te gebruiken voor meer informatie over hoe Adobe Commerce en Magento Open Source werken. Vermijd het ontwikkelen van een systeem waarin u voorbeeldgegevens hebt geïnstalleerd.

U kunt optionele voorbeeldgegevens op een van de volgende manieren installeren:

| Installatiemethode | Beschrijving | Vereist vaardigheidsniveau |
|--- |--- |--- |
| Composer gebruiken | [Uitvoeren `magento sampledata:deploy` om de hoofdmap van de toepassing te wijzigen `composer.json`](composer-packages.md) steekproefgegevensmodules in te schakelen. | Vereist Composer kennis en toegang tot het systeem van het Dossier van de Handel. |
| Bewerkingen klonen | [Clone the GitHub repository](git-repositories.md) en de gegevensopslagplaats van de steekproef, dan verbind hen samen. | Alleen voor bijdragende ontwikkelaars. Iedereen anders zou één van de voorafgaande methodes moeten gebruiken. |

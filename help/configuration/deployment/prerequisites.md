---
title: Vereisten voor implementatie
description: Zie een lijst van eerste vereisten voor het opstellen van Handel in een ontwikkeling, bouwt, of productiesysteem.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Vereisten voor ontwikkeling, bouw, en productiesystemen

Bestandsmachtigingen en eigendom moeten consistent zijn in alle ontwikkelings-, bouw- en productiesystemen. Om dit werk te maken, moet u of:

- Alle volgende kenmerken:

   - Dezelfde instelling [eigenaar van bestandssysteem](https://glossary.magento.com/magento-file-system-owner) gebruikersnaam op alle systemen
   - Zorg ervoor dat de webserver op alle systemen op dezelfde gebruiker wordt uitgevoerd
   - Zorg ervoor dat de eigenaar van het bestandssysteem deel uitmaakt van de webservergroep op alle systemen

- Wijzig desgewenst de machtigingen voor het bestandssysteem en de eigendom van elk systeem met behulp van de volgende richtlijnen:

   - Ontwikkeling en opbouw: [Eigendom en machtigingen vóór de installatie instellen (twee gebruikers)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Productie: [Eigendom en machtigingen van de handel in ontwikkeling en productie](file-system-permissions.md)

>[!INFO]
>
>Als u deze benadering kiest, moet u de toestemmingen en de eigendom van het dossiersysteem plaatsen telkens als u code van uw bouwstijlsysteem trekt (als de eigenaar van het dossiersysteem of de gebruiker van de Webserver op uw bouwstijlsysteem verschillend zijn).

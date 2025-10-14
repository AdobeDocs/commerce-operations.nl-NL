---
title: Vereisten voor implementatie
description: Zie een lijst van eerste vereisten voor het opstellen van Commerce in een ontwikkelings, bouwt, of productiesysteem.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Vereisten voor ontwikkeling, bouw, en productiesystemen

Bestandsmachtigingen en eigendom moeten consistent zijn in alle ontwikkelings-, bouw- en productiesystemen. Om dit werk te maken, moet u of:

- Alle volgende kenmerken:

   - Dezelfde gebruikersnaam voor de eigenaar van het bestandssysteem instellen op alle systemen
   - Zorg ervoor dat de webserver op alle systemen op dezelfde gebruiker wordt uitgevoerd
   - Zorg ervoor dat de eigenaar van het bestandssysteem deel uitmaakt van de webservergroep op alle systemen

- Wijzig desgewenst de machtigingen voor en het eigendom van Commerce-bestandssystemen op elk systeem aan de hand van de volgende richtlijnen:

   - Ontwikkeling en bouwt: [&#x200B; plaats pre-installatiereigenschap en toestemmingen (twee gebruikers) &#x200B;](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Productie: [&#x200B; Commerce eigendom en toestemmingen in ontwikkeling en productie &#x200B;](file-system-permissions.md)

>[!INFO]
>
>Als u deze benadering kiest, moet u de toestemmingen en de eigendom van het dossiersysteem plaatsen telkens als u code van uw bouwstijlsysteem trekt (als de eigenaar van het dossiersysteem of de gebruiker van de Webserver op uw bouwstijlsysteem verschillend zijn).

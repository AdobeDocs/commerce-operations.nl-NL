---
title: Terugdraaien na updatefout module
description: Los uw verbetering van Adobe Commerce na het ontmoeten van een module updatefout problemen op.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Terugdraaien na updatefout module

Als de update van uw module mislukt, worden berichten die lijken op de volgende weergave in het consolelogboek weergegeven:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

In het voorgaande voorbeeld is er geen componentversie die moet worden teruggedraaid. Neem contact op met de leverancier van de component of probeer het probleem zelf op te lossen.

In de tussentijd, kunt u terug naar een vorige versie rollen door **Terugdraaiend** te klikken, die uw gegevens terugkrijgt zelfs als u niet eerder file maakte.

---
title: Terugdraaien na updatefout module
description: Los uw Adobe Commerce of verbetering van de Magento Open Source na het ontmoeten van een fout van de moduleupdate problemen op.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
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

In de tussentijd kunt u teruggaan naar een vorige versie door op **Terugdraaien**, die uw gegevens herstelt, zelfs als u eerder geen back-up hebt gemaakt.
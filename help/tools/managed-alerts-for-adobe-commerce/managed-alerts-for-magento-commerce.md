---
title: Beheerde waarschuwingen voor Adobe Commerce
description: Als u een Adobe Commerce bent voor de klant van de cloudinfrastructuur Pro, kunt u beheerde waarschuwingen gebruiken om de gezondheid van uw site te begrijpen. Als u Adobe Commerce op de klant van de het planarchitectuur van de Aanzet van de wolkeninfrastructuur bent, zult u slechts alarm voor  [!DNL Apdex]  en foutentariefvoorwaarden ontvangen.
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: efb58b920a9b72ac96bbd28aaae6210ede84e24f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Beheerde waarschuwingen voor Adobe Commerce


We hebben belangrijke dashboards en waarschuwingen ingesteld om u te helpen te begrijpen wanneer uw site kritieke opslag en [!DNL Apdex] -niveaus bereikt (tevredenheid van gebruikers over toepassingen en serviceresponstijd). Dit kan u helpen actie te ondernemen voordat u langzame reactietijden of een stroomonderbreking opmerkt. U kunt de waarschuwingen met de onderstaande artikelen oplossen. Voordat u de waarschuwingen kunt gebruiken, moet u eerst meldingskanalen instellen. Gelieve te verwijzen naar [[!DNL New Relic]  vormen de Kanalen van het Bericht ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) in Commerce op de Gids van de Wolk.

>[!NOTE]
>
>Als beheerde waarschuwingen voor het Adobe Commerce-waarschuwingsbeleid niet beschikbaar zijn, kan dit mogelijk komen doordat dit account nieuw is gemaakt of omdat [!DNL New Relic] onlangs is geconfigureerd. Elke dinsdag wordt een proces uitgevoerd om het waarschuwingsbeleid aan deze accounts toe te voegen. Het waarschuwingsbeleid moet u de dag nadat het volgende proces wordt uitgevoerd, ter beschikking staan. Als het beleid nog mist, [ voorlegt een de steunverzoek van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) en omvat uw project identiteitskaart

Zie hieronder in de tabel voor koppelingen naar de KB-artikelen met stappen voor het oplossen van problemen voor deze waarschuwingen:

* Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor CPU
* Beheerde waarschuwingen voor Adobe Commerce: kritieke CPU-waarschuwing
* Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenmeldingen
* Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor essentieel geheugen
* Beheerde waarschuwingen voor Adobe Commerce: [!DNL Apdex] waarschuwingswaarschuwing
* Beheerde waarschuwingen voor Adobe Commerce: [!DNL Apdex] kritieke waarschuwing
* Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor een schijf
* Beheerde waarschuwingen voor Adobe Commerce: kritieke schijf
* Beheerde waarschuwingen over Adobe Commerce: MariaDB-waarschuwingen
* Beheerde waarschuwingen over Adobe Commerce: [!DNL Redis] waarschuwing voor het geheugen
* Beheerde waarschuwingen over Adobe Commerce: [!DNL Redis] kritieke geheugenwaarschuwing

>[!NOTE]
>
>De vastgestelde drempels voor zowel Waarschuwingen als Kritieke Alarm zijn gebaseerd op onderzoek wij het gebruiken van historische prestatiesgegevens over onze klantenbasis, en vertegenwoordigen de recentste inzichten van de teams van de Steun en van de Techniek van Adobe Commerce. Deze drempelwaarden kunnen worden gewijzigd op basis van de meest recente, lopende analyse. De doorsnee waarschuwingsstroom bestaat uit het ontvangen van waarschuwingen die minder ernstig zijn. U ontvangt dus waarschijnlijk een waarschuwingsbericht voordat u een waarschuwing krijgt. Raadpleeg de koppelingen naar artikelen voor het oplossen van problemen.

| Ernst | CPU | Geheugen | Schijf | [!DNL Apdex] | MariaDB | [!DNL Redis] Geheugen | Probleemoplossing voor artikel |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Waarschuwing | ✅ |        |      |       |         |              | [ Beheerde alarm voor Adobe Commerce: De waarschuwingsalarm van CPU ](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Kritiek | ✅ |        |      |       |         |              | [ Beheerde alarm voor Adobe Commerce: Kritieke alarm van CPU ](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Waarschuwing |     | ✅ |      |       |         |              | [ Beheerde alarm voor Adobe Commerce: alarm van de geheugenwaarschuwing ](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Kritiek |     | ✅ |      |       |         |              | [ Beheerde alarm voor Adobe Commerce: geheugen kritieke alarm ](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Waarschuwing |     |        |      | ✅ |         |              | [ Beheerde alarm voor Adobe Commerce: [!DNL Apdex]  waarschuwingsalarm ](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Kritiek |     |        |      | ✅ |         |              | [ Beheerd alarm voor Adobe Commerce: [!DNL Apdex]  kritiek alarm ](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Waarschuwing |     |        | ✅ |       |         |              | [ Beheerde alarm voor Adobe Commerce: de alarm van de schijfwaarschuwing ](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Kritiek |     |        | ✅ |       |         |              | [ Beheerde alarm voor Adobe Commerce: schijf kritieke alarm ](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Waarschuwing en kritiek |     |        |      |       | ✅ |              | [ Beheerd alarm op Adobe Commerce: MariaDB alarm ](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Waarschuwing |     |        |      |       |         | ✅ | [ Beheerde alarm op Adobe Commerce: [!DNL Redis]  alarm van de geheugenwaarschuwing ](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Kritiek |     |        |      |       |         | ✅ | [ Beheerd alarm op Adobe Commerce: [!DNL Redis]  geheugen kritieke alarm ](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

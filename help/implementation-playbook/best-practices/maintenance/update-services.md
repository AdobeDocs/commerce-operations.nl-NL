---
title: Beste werkwijzen voor services bijwerken
description: Leer hoe u uw Adobe Commerce op de technologiestapel voor cloudinfrastructuur up-to-date houdt.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Beste werkwijzen voor services bijwerken

Dit artikel bevat aanbevelingen om uw Adobe Commerce op de technologiestapel van de cloud-infrastructuur up-to-date te houden en bevat koppelingen naar nuttige bronnen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.x en hoger

## Services bijwerken

Upgrade de services en onderdelen die door Adobe Commerce worden gebruikt voordat ze de einddatum bereiken of bijna halen. Dit helpt om gelijke tred te houden met de naleving van PCI en veiligheidskwetsbaarheid te verminderen.

De klanten op de plannen van de Aanzet kunnen zelf-dienen op de dienstverbeteringen. Zie [Serviceversie wijzigen](https://devdocs.magento.com/cloud/project/services.html#change-service-version) voor meer informatie over hoe u dit kunt doen.

Klanten met Pro-plannen kunnen alleen zelf hun eigen upgrades voor services uitvoeren in hun [Integratieomgeving](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Voor services-upgrades op Productie moet u [een ondersteuningsticket indienen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) de upgrade aanvragen.

>[!WARNING]
>
>De verbeteringen van de dienst kunnen niet aan het productiemilieu worden geduwd zonder 48 bedrijfsuren kennisgeving aan ons infrastructuurteam. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken.

U kunt de lijst van de dienstversies en einddatums in het volgende dossier bekijken: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Dit bestand kan niet als één bron van waarheid worden beschouwd. Raadpleeg bij twijfel de officiële websites van leveranciers voor deze technologieën.

## Aanvullende informatie

[Systeemvereisten](../../../installation/system-requirements.md)

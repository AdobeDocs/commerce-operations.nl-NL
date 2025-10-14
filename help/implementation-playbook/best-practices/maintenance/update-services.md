---
title: Beste werkwijzen voor services bijwerken
description: Leer hoe u uw Adobe Commerce op de technologiestapel voor cloudinfrastructuur up-to-date houdt.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Beste werkwijzen voor services bijwerken

Dit artikel bevat aanbevelingen om uw Adobe Commerce op de technologiestapel van de cloud-infrastructuur up-to-date te houden en bevat koppelingen naar nuttige bronnen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.x en hoger

## Services bijwerken

Upgrade de services en onderdelen die door Adobe Commerce worden gebruikt voordat ze de einddatum bereiken of bijna halen. Dit helpt om gelijke tred te houden met de naleving van PCI en veiligheidskwetsbaarheid te verminderen.

De klanten op de plannen van de Aanzet kunnen zelf-dienen op de dienstverbeteringen. Verwijs naar [&#x200B; de dienstversie van de Verandering &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) voor details op hoe te om dit te doen.

De klanten op Pro plannen kunnen op de dienstverbeteringen in hun [&#x200B; milieu van de Integratie slechts zelf-dienen &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html?lang=nl-NL). Voor de dienstverbeteringen op Productie, moet u [&#x200B; een steunkaartje &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) voorleggen die om de verbetering verzoekt.

>[!WARNING]
>
>Service-upgrades kunnen niet naar een productieomgeving worden geduwd zonder dat het infrastructuurteam van Adobe 48 kantooruren hiervan op de hoogte wordt gesteld. Dit is nodig, zodat Adobe ervoor kan zorgen dat een technicus voor infrastructuurondersteuning beschikbaar is om uw configuratie binnen een gewenst tijdsbestek bij te werken met minimale downtime naar uw productieomgeving. Adobe raadt u aan uw site in de onderhoudsmodus te zetten tijdens de upgrade van de service.

U kunt de lijst van de dienstversies en eind-van-leven data in het volgende dossier bekijken: [&#x200B; https://github.com/magento/ece-tools/blob/develop/config/eol.yaml &#x200B;](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Dit bestand kan niet als één bron van waarheid worden beschouwd. Raadpleeg bij twijfel de officiële websites van leveranciers voor deze technologieën.

## Aanvullende informatie

[Systeemvereisten](../../../installation/system-requirements.md)

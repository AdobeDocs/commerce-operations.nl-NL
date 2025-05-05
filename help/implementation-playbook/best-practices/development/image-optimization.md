---
title: Afbeeldingen optimaliseren voor een meer responsieve site
description: Leer de stappen voor het optimaliseren van afbeeldingen en het gebruik van Fastly voor het optimaliseren van de responstijd op uw Adobe Commerce-sites.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Afbeeldingen optimaliseren voor een meer responsieve site

Voor Adobe Commerce op implementaties van cloudinfrastructuren kunt u de responstijd van de site verbeteren door images te optimaliseren voordat u deze uploadt. Gebruik vervolgens de functie voor snelle optimalisatie van de afbeelding om de levering van de afbeelding te versnellen en het onderhoud van sets met afbeeldingsbronnen te vereenvoudigen.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

Adobe Commerce over cloudinfrastructuur


## Afbeeldingen optimaliseren en comprimeren

Voordat u afbeeldingen uploadt naar uw Commerce-sites, optimaliseert en comprimeert u deze om de prestaties in evenwicht te brengen met de weergavekwaliteit. Hierdoor neemt de ruimte toe en nemen de laadtijden van de pagina af.

- De PNG-indeling biedt afbeeldingen van een kleiner formaat voor afbeeldingen met grote gebieden met effen kleuren.

- De JPEG-indeling biedt kleinere afbeeldingen voor alle andere afbeeldingstypen. Gebruik de hoogste compressie (zonder merkbare verslechtering). Dit is meestal 60 tot 80 procent.

## Snelle optimalisatie van afbeeldingen inschakelen en configureren

Nadat u opstelling de Snelle dienst voor uw project van Adobe Commerce Cloud, zie [ Snelle beeldoptimalisering ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) voor instructies om beeldoptimalisering toe te laten en te vormen.

## Aanvullende informatie

- [ Opstelling snel ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [ slecht geoptimaliseerde beelden kunnen tot prestatieskwesties leiden ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=nl-NL)

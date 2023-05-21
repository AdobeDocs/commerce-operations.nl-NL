---
title: Afbeeldingen optimaliseren voor een meer responsieve site
description: Leer de stappen voor het optimaliseren van afbeeldingen en het gebruik van Fastly Image Optimization om de responstijd op uw Adobe Commerce-sites te optimaliseren.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Afbeeldingen optimaliseren voor een meer responsieve site

Voor Adobe Commerce op implementaties van cloudinfrastructuren kunt u de responstijd van de site verbeteren door images te optimaliseren voordat u deze uploadt. Gebruik vervolgens de functie voor snelle optimalisatie van de afbeelding om de levering van de afbeelding te versnellen en het onderhoud van sets met afbeeldingsbronnen te vereenvoudigen.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

Adobe Commerce over cloudinfrastructuur


## Afbeeldingen optimaliseren en comprimeren

Voordat u afbeeldingen uploadt naar uw Commerce-sites, optimaliseert en comprimeert u deze om de prestaties in evenwicht te brengen met de weergavekwaliteit. Hierdoor neemt de ruimte toe en nemen de laadtijden van de pagina af.

- De PNG-indeling biedt afbeeldingen van een kleiner formaat voor afbeeldingen met grote gebieden met effen kleuren.

- De JPEG-indeling biedt kleinere afbeeldingen voor alle andere afbeeldingstypen. Gebruik de hoogste compressie (zonder merkbare verslechtering). Dit is meestal 60 tot 80 procent.

## Snelle optimalisatie van afbeeldingen inschakelen en configureren

Nadat u de snelservice voor uw Adobe Commerce Cloud-project hebt ingesteld, raadpleegt u [Snelle optimalisatie van afbeeldingen](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) voor instructies voor het inschakelen en configureren van optimalisatie van images.

## Aanvullende informatie

- [Snel instellen](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Slecht geoptimaliseerde afbeeldingen kunnen prestatieproblemen veroorzaken](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)

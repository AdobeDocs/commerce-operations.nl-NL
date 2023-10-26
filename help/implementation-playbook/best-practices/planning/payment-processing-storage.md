---
title: Aanbevolen procedures voor betalingsverwerking en -opslag
description: Meer informatie over het veilig verwerken en opslaan van betalingsgegevens
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 1887d7b285008fc98579955274bbc4affb766d0c
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Aanbevolen procedures voor betalingsverwerking en -opslag

Een van de belangrijkste beginselen bij het handhaven van [PCI-compatibiliteit](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) heeft een strategie om creditcardbetalingen correct te verwerken en op te slaan.

Gegevens van kaarthouders opslaan in Adobe Commerce is **strikt verboden** en dit zou een schending van uw verplichtingen als handelaar onder de Norm van de Veiligheid van Gegevens van de Industrie van de Bedrijfs van de Betalingskaart (PCI-DSS) kunnen zijn. Meer informatie over het model van gedeelde verantwoordelijkheid en de richtsnoeren voor handelsverplichtingen is te vinden in de [Adobe Commerce Handleiding voor gedeeld verantwoordelijkheidsmodel](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) op het Adobe Trust Center.

Volg de onderstaande aanbevolen procedures om ervoor te zorgen dat je de betalingsgegevens op je eCommerce-site correct verwerkt. Aanvullende richtlijnen over algemene best practices op het gebied van beveiliging vindt u in onze [Tips voor best practices voor beveiliging voor Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) over het Adobe Vertrouwenscentrum

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

* Adobe Commerce over cloudinfrastructuur
* Adobe Commerce ter plaatse

## Gegevens van kaarthouders beschermen

Als het opslaan van gegevens van kaarthouders nodig is, moeten kaarthoudergegevens buiten Adobe Commerce worden opgeslagen met opslaggaranties. Het bieden van opslagwaarborgen voor betalingsdetails, zoals creditcardgegevens, helpt fraude en andere potentiële veiligheidskwesties te voorkomen. In overeenstemming met andere PCI-normen is het op zijn plaats hebben van bescherming de eerste verdedigingslinie. Sommige voorkeursmethoden om de bescherming van opgeslagen gegevens te verbeteren zijn codering, afkapping, kenisering, one-way hashing en maskeren.

Beschermingen voor cryptografische sleutels zijn van essentieel belang voor gegevensbeschermingsstrategieën. Het is essentieel om ervaren en betrouwbare bewaarnemers te hebben die deze sleutels controleren.

Ten slotte moet een primair rekeningnummer (PAN) tijdens de opslag onleesbaar zijn, bijvoorbeeld met `XXX`. Dit omvat draagbare opslag- en back-upmedia zoals flash drives, USB en externe harde schijven en zelfs auditlogs.

## Verzending van kaarthoudergegevens versleutelen

Het beschermen van gegevens tijdens de transmissie is van essentieel belang voor de bescherming van betalingsinformatie, zoals gegevens van kaarthouders. Wanneer deze informatie over open netwerken wordt overgebracht, kan het kwetsbaarder voor veiligheidskwesties worden.

### Beveiligde transmissieprotocollen gebruiken

Gegevens van kaarthouders verzenden aan de hand van veilige transmissieprotocollen en -praktijken, waaronder:

* Vertrouwde sleutels en certificaten
* Veilige transmissieprotocollen zoals TLS, SSH of VPN
* Asymmetrische algoritmen in versleuteling
* Tokenizatings-, maskeerings- en penetratietests met het verzenden en weergeven van PAN&#39;s
* Toegang tot kaarthoudergegevens beperken
* De toegang tot gevoelige informatie moet op een &quot;need-to-know&quot;-basis worden beperkt en alleen worden verleend aan bevoegd personeel met een zakelijke behoefte

De aanbevolen methode voor het verwerken van gegevens van een kaarthouder is het vergelijken van de gegevens in plaats van deze op te slaan. De kaart samenvoegen met een specifieke betalingsdienstaanbieder en de token, het type kaart en de gecodeerde vervaldatum opslaan. U kunt de token gebruiken als referentie in het bestand voor toekomstig gebruik, aangezien deze alleen voor elke handelaar uniek is. Aangezien het token uniek is en er een beveiligingsprobleem is, is het token ongeldig, waardoor frauduleuze activiteiten worden voorkomen.

## Aanvullende informatie

Als u op zoek bent naar aanbevolen betalingsoplossingen per Adobe, kunt u [Betalingsdiensten Adobe](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).

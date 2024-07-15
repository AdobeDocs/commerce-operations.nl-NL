---
title: Adobe Privacy JavaScript Library
description: Leer hoe u aangepaste gereedschappen kunt gebruiken voor het openen en verwijderen van persoonlijke klantgegevens die door Adobe Commerce zijn verzameld.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe Privacy JavaScript Library

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

De [ Bibliotheek van JavaScript van de Privacy van de Adobe ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) is een reeks hulpmiddelen helpen een proces tot stand brengen om tot privé gegevens toegang te hebben en te schrappen.

De gegevens volgende diensten van Adobe Commerce kunnen privé informatie opslaan van toepassing op privacyverordeningen zoals de [ Algemene Verordening van de Bescherming van Gegevens (GDPR) ](gdpr.md) en [ de Wet van de Privacy van de consument van Californië (CCPA) ](ccpa.md).

Deze bibliotheek biedt een uniforme set functies voor het maken van privacy-gegevensaanvragen, het verzenden van deze naar de implementaties van elk product en het verzamelen van de reacties. Gebruik deze bibliotheek om de gegevens op te halen en te verwijderen die in browser door deze gegevens volgende diensten worden opgeslagen.

## Installatie

Gebruik een van de volgende methoden om het bibliotheekbestand te downloaden:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [ https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Nadat u het bestand hebt geïnstalleerd, moet u het toevoegen aan een aangepaste module of een aangepast thema in uw Adobe Commerce-instantie. Volg de instructies die in het [ worden beschreven onderwerp van de douaneJavaScript van het Gebruik ](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) om deze taak te verwezenlijken.

## Gebruik

De AdobePrivacy JS-bibliotheek bevat verschillende functies voor het beheer van identiteitsgegevens die zijn opgeslagen in de browser.

`retrieveIdentities()`
: Retourneert een array met identiteiten van een service samen met een array met identiteiten die niet in de service zijn gevonden

`removeIdentities()`
: Verwijdert identiteiten uit de browser en retourneert een array van identiteitsobjecten met een Booleaanse eigenschap `isDeleteClientSide` om aan te geven of de gegevens zijn verwijderd.

`retrieveThenRemoveIdentities()`
: Deze functie is vergelijkbaar met `removeIdentities()` in die zin dat deze een array van identiteiten ophaalt en deze uit de browser verwijdert.

Voor meer informatie en voorbeelden om deze functies te gebruiken, zie de [ officiële bibliotheekdocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### Initialisatie

Instantieer een nieuw `AdobePrivacy` -object om de AdobePrivacy JS-bibliotheek te gebruiken in uw implementatiecode.

```js
var adobePrivacy = new AdobePrivacy({});
```

De constructor accepteert een configuratieobject met parameters tijdens het instantiëren.
Verwijs naar de [ officiële bibliotheekdocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) voor een lijst van deze configuratieparameters.

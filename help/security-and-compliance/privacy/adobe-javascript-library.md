---
title: Privacy JavaScript-bibliotheek Adobe
description: Leer hoe u aangepaste gereedschappen kunt gebruiken voor het openen en verwijderen van persoonlijke klantgegevens die door Adobe Commerce zijn verzameld.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Privacy JavaScript-bibliotheek Adobe

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

De [Privacy JavaScript-bibliotheek Adobe](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) Dit is een set gereedschappen waarmee u een proces kunt maken voor het openen en verwijderen van persoonlijke gegevens.

Adobe Commerce-services voor het bijhouden van gegevens kunnen persoonlijke gegevens opslaan die van toepassing zijn op privacyregels zoals de [Algemene verordening inzake gegevensbescherming (GDPR)](gdpr.md) en [California Consumer Privacy Act (CCPA)](ccpa.md).

Deze bibliotheek biedt een uniforme set functies voor het maken van privacy-gegevensaanvragen, het verzenden van deze naar de implementaties van elk product en het verzamelen van de reacties. Gebruik deze bibliotheek om de gegevens op te halen en te verwijderen die in browser door deze gegevens volgende diensten worden opgeslagen.

## Installatie

Gebruik een van de volgende methoden om het bibliotheekbestand te downloaden:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Nadat u het bestand hebt geïnstalleerd, moet u het toevoegen aan een aangepaste module of een aangepast thema in uw Adobe Commerce-instantie. Volg de instructies in de [Aangepast JavaScript gebruiken](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) onderwerp om deze taak te verwezenlijken.

## Gebruik

De AdobePrivacy JS-bibliotheek bevat verschillende functies voor het beheer van identiteitsgegevens die zijn opgeslagen in de browser.

`retrieveIdentities()`
: Retourneert een array met identiteiten van een service samen met een array met identiteiten die niet in de service zijn gevonden

`removeIdentities()`
: Hiermee verwijdert u identiteiten uit de browser en retourneert u een array van identiteitsobjecten met een `isDeleteClientSide` Booleaanse eigenschap om aan te geven of de gegevens zijn verwijderd.

`retrieveThenRemoveIdentities()`
: Deze functie is vergelijkbaar met `removeIdentities()` daarin wordt een array met identiteiten opgehaald en uit de browser verwijderd.

Zie voor meer informatie en voorbeelden over het gebruik van deze functies de [officiële bibliotheekdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### Initialisatie

Instantiëren van nieuwe `AdobePrivacy` -object om de AdobePrivacy JS-bibliotheek in uw implementatiecode te gebruiken.

```js
var adobePrivacy = new AdobePrivacy({});
```

De constructor accepteert een configuratieobject met parameters tijdens het instantiëren.
Zie de [officiële bibliotheekdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) voor een lijst van deze configuratieparameters.

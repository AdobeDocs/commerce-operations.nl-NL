---
title: Adobe Privacy JavaScript-bibliotheek
description: Leer hoe u aangepaste gereedschappen kunt gebruiken om persoonlijke gegevens van klanten die zijn verzameld door Adobe Commerce en Magento Open Source, te openen en te verwijderen.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Adobe Privacy JavaScript-bibliotheek

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

De [Adobe Privacy JavaScript-bibliotheek](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) Dit is een set gereedschappen waarmee u een proces kunt maken voor het openen en verwijderen van persoonlijke gegevens.

Adobe Commerce en Magento Open Source data tracking kunnen persoonlijke gegevens opslaan die van toepassing zijn op privacyregels zoals [Algemene verordening inzake gegevensbescherming (GDPR)](gdpr.md) en [California Consumer Privacy Act (CCPA)](ccpa.md).

Deze bibliotheek biedt een uniforme set functies voor het maken van privacy-gegevensaanvragen, het verzenden van deze naar de implementaties van elk product en het verzamelen van de reacties. Gebruik deze bibliotheek om de gegevens op te halen en te verwijderen die in browser door deze gegevens volgende diensten worden opgeslagen.

## Installatie

Gebruik een van de volgende methoden om het bibliotheekbestand te downloaden:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Nadat u het bestand hebt, moet u het toevoegen aan een aangepaste module of thema dat is geïnstalleerd in uw Adobe Commerce- en Magento Open Source-exemplaar. Volg de instructies in de [Aangepast JavaScript gebruiken](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) onderwerp om deze taak te verwezenlijken.

## Gebruik

De AdobePrivacy JS-bibliotheek bevat verschillende functies voor het beheer van identiteitsgegevens die zijn opgeslagen in de browser.

`retrieveIdentities()`
: Retourneert een array met identiteiten van een service samen met een array met identiteiten die niet in de service worden gevonden

`removeIdentities()`
: Verwijdert identiteiten uit de browser en retourneert een array van identiteitsobjecten met een `isDeleteClientSide` Booleaanse eigenschap om aan te geven of de gegevens zijn verwijderd.

`retrieveThenRemoveIdentities()`
: Deze functie is vergelijkbaar met `removeIdentities()` daarin wordt een array met identiteiten opgehaald en uit de browser verwijderd.

Zie voor meer informatie en voorbeelden over het gebruik van deze functies de [officiële bibliotheekdocumentatie](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Initialisatie

Instantiëren van een nieuwe `AdobePrivacy` -object om de AdobePrivacy JS-bibliotheek in uw implementatiecode te gebruiken.

```js
var adobePrivacy = new AdobePrivacy({});
```

De constructor accepteert een configuratieobject met parameters tijdens het instantiëren.
Zie de [officiële bibliotheekdocumentatie](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) voor een lijst van deze configuratieparameters.

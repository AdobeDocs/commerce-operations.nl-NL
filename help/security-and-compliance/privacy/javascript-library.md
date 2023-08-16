---
title: Privacy JavaScript-bibliotheek
description: Leer hoe u aangepaste gereedschappen kunt gebruiken voor het openen en verwijderen van persoonlijke gegevens van klanten die zijn verzameld door Adobe Commerce en Magento Open Source.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript-bibliotheek

De Privacy JavaScript Bibliotheek is een reeks hulpmiddelen helpen tot een proces leiden voor de toegang tot van en het schrappen van privé gegevens die door Adobe Commerce en Magento Open Source worden verzameld.

De diensten van de gegevenspracking van de handel kunnen privé informatie opslaan die op privacyverordeningen zoals [Algemene verordening inzake gegevensbescherming (GDPR)](gdpr.md) en [California Consumer Privacy Act (CCPA)](ccpa.md).

Deze bibliotheek bevat een set functies voor het maken van verzoeken om privacygegevens en het verzamelen van de reacties. Met deze bibliotheek kunt u de gegevens ophalen die door Adobe Commerce in de browser zijn opgeslagen en de services voor het bijhouden van gegevens Magento Open Sourcen.

>[!NOTE]
>
>Indien [Modus Cookie-beperking](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) wordt toegelaten, verzamelt de Handel geen gedragsgegevens tot de verkoopster goedkeurt. Indien [!UICONTROL **Modus Cookie-beperking**] is uitgeschakeld, verzamelt Commerce standaard gedragsgegevens.

## Installatie

De Privacy JavaScript-bibliotheek van de Privacy is beschikbaar op de volgende CDN-locatie: `commerce.adobe.net/magentoprivacy.js`

Nadat u het bestand hebt geïnstalleerd, moet u het toevoegen aan een aangepaste module of een aangepast thema in uw Adobe Commerce- of Magento Open Source-exemplaar. Volg de instructies in de [Aangepast JavaScript gebruiken](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) onderwerp om deze taak te verwezenlijken.

### Initialisatie

Een nieuwe versie importeren en instantiëren `MagentoPrivacy` object of gebruik de `window` -object voor toegang tot de JavaScript-functies Privacy.

Voorbeeld met `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Voorbeeld met `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Gebruik

De Privacy JS Library biedt verschillende functies voor het beheer van identiteitsgegevens die in de browser zijn opgeslagen.

`retrieveIdentity()`
: Retourneert een JavaScript-promise voor een identiteitsobject van een service in de browser.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Hiermee verwijdert u de identiteitsgegevens uit een service in de browser.
Deze functie retourneert een JavaScript-promise voor een identiteitsobject met een `isDeleted` Booleaanse eigenschap om aan te geven of de gegevens zijn verwijderd.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```

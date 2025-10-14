---
title: Privacy JavaScript Library
description: Leer hoe u aangepaste gereedschappen kunt gebruiken voor het openen en verwijderen van persoonlijke klantgegevens die door Adobe Commerce zijn verzameld.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript Library

De Privacy JavaScript Library is een set hulpmiddelen waarmee u een proces kunt maken voor het openen en verwijderen van privégegevens die door Adobe Commerce zijn verzameld.

De gegevens volgende diensten van Commerce kunnen privé informatie opslaan van toepassing op privacyverordeningen zoals de [&#x200B; Algemene Verordening van de Bescherming van Gegevens (GDPR) &#x200B;](gdpr.md) en [&#x200B; de Wet van de Privacy van de consument van Californië (CCPA) &#x200B;](ccpa.md).

Deze bibliotheek bevat een set functies voor het maken van verzoeken om privacygegevens en het verzamelen van de reacties. Met deze bibliotheek kunt u de gegevens ophalen die in de browser zijn opgeslagen door Adobe Commerce-services voor het bijhouden van gegevens.

>[!NOTE]
>
>Als [&#x200B; de Wijze van de Beperking van het Koekje &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=nl-NL) wordt toegelaten, verzamelt Commerce geen gedragsgegevens tot de verkoopster toestemmingen. Als [!UICONTROL **de Wijze van de Beperking van het Koekje**] gehandicapt is, verzamelt Commerce gedragsgegevens door gebrek.

## Installatie

De Privacy JavaScript Library is beschikbaar op de volgende CDN-locatie: `commerce.adobe.net/magentoprivacy.js`

Nadat u het bestand hebt geïnstalleerd, moet u het toevoegen aan een aangepaste module of een aangepast thema in uw Adobe Commerce-instantie. Volg de instructies die in het [&#x200B; worden beschreven onderwerp van de douaneJavaScript van het Gebruik &#x200B;](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) om deze taak te verwezenlijken.

### Initialisatie

Importeer en instantieer een nieuw `MagentoPrivacy` -object of gebruik het `window` -object om toegang te krijgen tot de Privacy JavaScript-functies.

Voorbeeld met `import` :

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Voorbeeld met `window` :

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
Deze functie retourneert een JavaScript-belofte voor een identiteitsobject met een Booleaanse eigenschap `isDeleted` om aan te geven of de gegevens zijn verwijderd.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```

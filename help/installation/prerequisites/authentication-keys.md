---
title: Uw verificatietoetsen ophalen
description: Ga als volgt te werk om referenties op te halen voor toegang tot Adobe Commerce Composer-pakketten op repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Uw verificatietoetsen ophalen

De `repo.magento.com` -opslagplaats is waar Adobe Commerce- en andere Composer-pakketten worden opgeslagen en waarvoor verificatie is vereist. Gebruik uw rekening van de Commerce Marketplace om een paar 32 karakter *authentificatietoetsen* te produceren om tot de bewaarplaats toegang te hebben.

Voor toegangsrechten voor Adobe Commerce-pakketten moet u sleutels gebruiken die zijn gekoppeld aan een MAGEID die toegang heeft gekregen tot die pakketten. De MAGEID is doorgaans de primaire contactpersoon op de Adobe Commerce-account en is mogelijk niet altijd de projecteigenaar van de Adobe Commerce voor het infrastructuurproject in de cloud.

>[!TIP]
>
>Als u [ fouten ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=nl-NL) ontmoet, kunt u geen toestemming hebben om tot het pakket toegang te hebben, of de toegangsrechten zijn verlopen toe te schrijven aan een opmerkelijke factuur op uw rekening.
>
>* Als je de primaire contactpersoon voor de account bent, zorg er dan voor dat er geen openstaande factuur op de account wordt vermeld.
>* Als de sleutels die door het Primaire Contact worden verstrekt niet werken en er geen uitstaande facturen op de rekening zijn, zou het Primaire Contact [ Steun van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) voor hulp moeten contacteren.

Zo maakt u verificatietoetsen:

1. Login aan de [ Commerce Marketplace ](https://commercemarketplace.adobe.com/). Als u geen rekening hebt, klik **Register**.

1. Klik uw rekeningsnaam in het hoogste recht van de pagina en selecteer **Mijn Profiel**.

1. Klik **Sleutels van de Toegang** in het lusje van de Marketplace.

   ![ krijgt uw veilige toegangstoetsen op Commerce Marketplace ](../../assets/installation/cloud_access-key.png)

1. Klik **creeer een Nieuwe Sleutel van de Toegang**. Ga een specifieke naam voor de sleutels (bijvoorbeeld, de naam van de ontwikkelaar in die de sleutels ontvangt) en klik **O.K.**.

1. Nieuwe openbare en persoonlijke sleutels zijn nu gekoppeld aan uw account waarop u kunt klikken om te kopiëren. Sla deze gegevens op of open de pagina wanneer u met uw project werkt. Gebruik **Openbare sleutel** als uw gebruikersbenaming en **Privé sleutel** als uw wachtwoord.

## De verificatietoetsen beheren

U kunt verificatietoetsen ook uitschakelen of verwijderen. U kunt bijvoorbeeld toetsen uit veiligheidsoverwegingen uitschakelen of verwijderen nadat iemand uw organisatie heeft verlaten.

* Om sleutels onbruikbaar te maken: Klik **onbruikbaar maken**. U kunt dit doen als u het gebruik van uw sleutels wilt onderbreken.
* Om een eerder gehandicapte sleutel toe te laten: Klik **laat** toe.
* Om sleutels te schrappen: klik **Schrapping**.

### SSH-toegangstoken beheren

Als u Adobe Commerce-releases wilt downloaden met behulp van SSH, moet u een Toegangstoken voor downloads genereren. Een token genereren:

1. Login aan uw [ magento.com rekening ](https://account.magento.com/customer/account/login).
1. Klik **Mijn Rekening** bij de bovenkant van de pagina.
1. Klik **de Montages van de Rekening** > **het Token van de Toegang van Downloads**.

   ![ heb toegang tot uw sleutels ](../../assets/installation/connect_keys1.png)

1. Klik **produceer nieuw teken** om een bestaand teken te vervangen en onbruikbaar te maken.

U moet uw MAGEID plus uw token gebruiken om een release te downloaden. Je GEID wordt linksboven op je rekeningpagina weergegeven.

Bijvoorbeeld:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Gebruik uw verificatietoetsen om:

* [Haal het pakket metapakketten op (integrators, packagers)](../composer.md)
* [ Kloon de bewaarplaats GitHub ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (bijdragende ontwikkelaars slechts)
* [Modules upgraden en beheren](../../upgrade/modules/upgrade.md)

---
title: Meerdere websites instellen, weergaven opslaan en opslaan in de beheerfunctie
description: Configureer aanvullende websites, winkels en sla weergaven op in Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Meerdere weergaven instellen in Beheer

Voor deze taak moet u een hoofdcategorie (en desgewenst extra categorieën) voor elke winkel maken. De taken die in dit onderwerp worden besproken verstrekken één manier aan opstelling veelvoudige opslag. Raadpleeg de volgende bronnen in de Commerce User Guide voor meer informatie:

- [ Categorieën ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories)
- [ toevoegend Websites ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [ opslag URLs ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls)
- [ Inhoud ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/content-menu)

>[!INFO]
>
>Alleen voor de doeleinden gebruiken we in dit onderwerp een Franse website met websitecode `french` . Voor geleidelijke leerprogramma&#39;s, zie [ Leerprogramma: Opstelling veelvoudige websites met Apache ](ms-apache.md) en [ Leerprogramma: Opstelling veelvoudige websites met nginx ](ms-nginx.md)

## Stap 1: Hoofdcategorieën maken

Het maken van een hoofdcategorie is optioneel, maar in deze zelfstudie wordt getoond hoe u dit kunt doen als u wilt dat elke website een unieke hoofdcategorie heeft. U kunt desgewenst extra categorieën maken.

Een hoofdcategorie maken:

1. Meld u aan bij de beheerder als een gebruiker die geautoriseerd is om categorieën te maken.
1. Klik **Catalogus** > **Categorieën**.
1. Klik **toevoegen de Categorie van de Wortel**.
1. Op het **gebied van de Naam van de Categorie 0&rbrace; &lbrace;, ga een unieke naam in om deze categorie te identificeren.**
1. Zorg ervoor dat laat Categorie toe wordt geplaatst aan **ja**.

   Voor informatie over de andere opties op deze pagina, zie [ de Categorieën van de Wortel ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-root).

   In de volgende afbeelding ziet u een voorbeeld.

   ![ creeer en laat een wortelcategorie ](../../assets/configuration/add-root-category.png) toe

1. Klik **sparen**.
1. Herhaal deze taken zo vaak als nodig om wortelcategorieën voor uw opslag tot stand te brengen.

## Stap 2: Websites maken

Een website maken:

1. Meld u aan bij de beheerder als een gebruiker die geautoriseerd is om websites te maken, weergaven op te slaan en op te slaan.
1. Klik **Opslag** > **Montages** > **Alle Opslag**.
1. Op de _pagina van Opslag_, klik **creeer Website**.

   - **Naam** - ga een naam in om de website te identificeren.
   - **Code** - ga een unieke code in; bijvoorbeeld, als u een Franse opslag hebt, kunt u `french` ingaan
   - **de Orde van de Sortering** - ga een facultatieve numerieke soortorde in.

   In de volgende afbeelding ziet u een voorbeeld.

   ![ voeg een website ](../../assets/configuration/multi-site-website.png) toe

1. Klik **sparen Website**.
1. Herhaal deze taken zo vaak als nodig is om uw websites te maken.

## Stap 3: Opslagruimten maken

Een winkel maken:

1. In het _Admin_ paneel, klik **Opslag** > **Montages** > **Alle Opslag**.
1. Op de _pagina van Opslag_, klik **creeer Opslag**.

   - **Website** - klik de naam van de website waarmee om deze opslag te associëren.
   - **Naam** - ga een naam in om de opslag te identificeren.
   - **Code** - ga een unieke code in om de opslag te identificeren.
   - **Categorie van de Wortel** - klik de naam van de wortelcategorie voor deze opslag.

   In de volgende afbeelding ziet u een voorbeeld.

   ![ voeg een opslag ](../../assets/configuration/multi-site-store.png) toe

1. Klik **sparen Opslag**.
1. Herhaal deze taken zo vaak als nodig is om uw winkels te maken.

## Stap 4: Winkelweergaven maken

Een winkelweergave maken:

1. In het _Admin_ paneel, klik **Opslag** > **Montages** > **Alle Opslag**.
1. Voor de pagina van Winkels, klik **creeer de Mening van de Opslag**.

   - **opslag** - klik de naam van de opslag waarmee om deze archiefmening te associëren.
   - **Naam** - ga een naam in om deze opslagmening te identificeren.
   - **Code** - ga een unieke naam in om deze opslagmening te identificeren.
   - **Status** - Uitgezochte **Toegelaten**.

   In de volgende afbeelding ziet u een voorbeeld.

   ![ voeg een opslag ](../../assets/configuration/multi-site-storeview.png) toe

1. Klik **sparen Mening van de Opslag**.
1. Herhaal deze taken zo vaak als nodig is om uw winkelweergaven te maken.

## Stap 5: de URL van de websitebasis wijzigen

Als u toegang wilt tot een website met een unieke URL, zoals `http://french.magento.mg` , moet u de basis-URL voor elke site wijzigen in Beheer.

De URL van de websitebasis wijzigen:

1. In het _Admin_ paneel, klik **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Web**.
1. Van de **lijst van de Mening van de Opslag** bij de bovenkant van de pagina, klik de naam van één van uw websites aangezien het volgende cijfer toont.

   ![ selecteer een werkingsgebied ](../../assets/configuration/multi-site-scope.png)

1. In de juiste ruit, breid **Basis URLs** uit.
1. In de _sectie van 0&rbrace; Basis URLs &lbrace;, ontruim **het systeemwaarde van het Gebruik**._
1. Ga `http://french.magento.mg` URL in de **Basis URL** en **van de Verbinding URL van de Basis** gebieden in.

1. Herhaal de vorige stap in de _Basis URLs (Veilig)_ sectie.

   >[!INFO]
   >
   >Als u een basis-URL instelt voor de implementatie van Adobe Commerce op een cloudinfrastructuur, moet u de eerste periode vervangen door drie streepjes. Als de basis-URL bijvoorbeeld `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` is, voert u `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` in. Gebruik een punt als u een basis-URL instelt voor lokale tests.

1. Klik **sparen Config**.

1. Herhaal deze taken voor andere websites.

## Stap 6: Voeg de winkelcode toe aan de basis-URL

Commerce biedt u de mogelijkheid om de winkelcode toe te voegen aan de URL van het sitebasis, waardoor het instellen van meerdere winkels eenvoudiger wordt. Als u deze optie gebruikt, hoeft u geen mappen in het Commerce-bestandssysteem te maken om `index.php` en `.htaccess` op te slaan.

Zo voorkomt u dat `index.php` en `.htaccess` in toekomstige upgrades niet meer synchroon raken met de Commerce-codebase.

Zie de [ Gids van de Gebruiker van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls).

U voegt als volgt de code van de winkel toe aan de basis-URL:

1. In het _Admin_ paneel, klik **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Web**.
1. Van de **lijst van de Mening van de Opslag** bij de bovenkant van de pagina, klik **Standaard Config** aangezien het volgende cijfer toont.

   ![ selecteer het gebrek config werkingsgebied ](../../assets/configuration/multi-site-default.png)

1. In de juiste ruit, breid **Opties Url** uit.
1. Wis het **systeemwaarde van het Gebruik** checkbox naast _toevoegen de Code van de Opslag aan Urls_.
1. Van _voeg de Code van de Opslag aan Urls_ lijst toe, klik **ja**.

   ![ voeg de opslagcode aan de opslagbasis URL ](../../assets/configuration/multi-site-add-store-url.png) toe

1. Klik **sparen Config**.
1. Maak de cache leeg als daarom wordt gevraagd. (**Systeem** > **Beheer van het Geheime voorgeheugen**).

## Stap 7: Wijzig de standaard-URL van de winkelweergave

U moet deze stap als laatste uitvoeren omdat u toegang tot Admin zult verliezen; uw toegangswinst nadat u opstelling virtuele gastheren zoals die in de web-server-specifieke onderwerpen worden besproken.

De standaard basis-URL van de winkelweergave wijzigen:

1. In het _Admin_ paneel, klik **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Web**.

1. Van de _lijst van de Mening van de Opslag_ bij de bovenkant van de pagina, klik **Standaard Config**.

   ![ selecteer het gebrek config werkingsgebied ](../../assets/configuration/multi-site-default.png)

1. In de juiste ruit, breid **Basis URLs** uit.
1. In de _sectie van 0&rbrace; Basis URLs &lbrace;, ontruim **het systeemwaarde van het Gebruik**._
1. Ga `http://magento.mg` URL in de **Basis URL** en **van de Verbinding URL van de Basis** gebieden in.

1. Herhaal de vorige stap in de **Basis URLs (Veilig)** sectie.

   >[!INFO]
   >
   >Als u een basis-URL voor Adobe Commerce instelt op cloudinfrastructuur, moet u de eerste punt vervangen door drie streepjes. Als de basis-URL bijvoorbeeld `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` is, voert u `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` in.

1. Klik **sparen Config**.

>[!INFO]
>
>De website-, opslag- en winkelweergavecode kan alleen letters (a-z of A-Z), getallen (0-9) en onderstrepingstekens (_) bevatten. Het eerste teken moet ook een letter zijn. Als hoofdletters of hoofdletters worden gebruikt, is de overeenkomst intern niet hoofdlettergevoelig voor overschrijvingen van configuratie-instellingen via omgevingsvariabelen. Zie [ het omgevingsvariabelen van het Gebruik om configuratiemontages ](../reference/override-config-settings.md#environment-variables) met voeten te treden.
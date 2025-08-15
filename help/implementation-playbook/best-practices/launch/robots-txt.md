---
title: Aanbevolen procedures voor het configureren van webcrawlers
description: Leer hoe u instructies over uw Adobe Commerce-site doorgeeft aan webcrawlers met de bestanden 'robots.txt' en 'sitemap.xml'.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Aanbevolen procedures voor het configureren van webcrawlers

Dit artikel biedt tips en trucs voor het gebruik van `robots.txt` - en `sitemap.xml` -bestanden in Adobe Commerce, inclusief configuratie en beveiliging. Deze bestanden geven webcrawlers (meestal robots met zoekmachines) de opdracht door pagina&#39;s op een website te bladeren. Door deze bestanden te configureren, kunt u de prestaties van de site verbeteren en de zoekmachine optimaliseren.

>[!NOTE]
>
>Deze best practices zijn alleen van toepassing op projecten die gebruikmaken van de native Adobe Commerce-winkel. Ze zijn niet van toepassing op Adobe Commerce-projecten die andere opslagoplossingen gebruiken (bijvoorbeeld Adobe Experience Manager, zonder kop).

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Adobe Commerce over cloudinfrastructuur

Een standaard Adobe Commerce-project bevat een hiërarchie die één website, winkel en opslagweergave bevat. Voor complexere implementaties, kunt u extra websites tot stand brengen, opslag, en opslagmeningen voor a _multi-site_ opslag.

### Single-site winkelefronts

Volg de onderstaande tips en trucs bij het configureren van `robots.txt` - en `sitemap.xml` -bestanden voor Single-Site-winkels:

- Zorg ervoor dat uw project [`ece-tools` ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) versie 2002.0.12 of later gebruikt.
- Gebruik de beheertoepassing om inhoud toe te voegen aan het `robots.txt` -bestand.

  >[!TIP]
  >
  >Bekijk het automatisch gegenereerde `robots.txt` bestand voor uw winkel op `<domain.your.project>/robots.txt` .

- Gebruik de beheertoepassing om een `sitemap.xml` -bestand te genereren.

  >[!IMPORTANT]
  >
  >Vanwege het alleen-lezen bestandssysteem op Adobe Commerce voor projecten met cloudinfrastructuur moet u het `pub/media` -pad opgeven voordat u het bestand genereert.

- Gebruik een aangepast, snel VCL-fragment om van de hoofdmap van uw site naar de `pub/media/` -locatie voor beide bestanden om te leiden:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Test de omleiding door de bestanden weer te geven in een webbrowser. Bijvoorbeeld `<domain.your.project>/robots.txt` en `<domain.your.project>/sitemap.xml` . Zorg ervoor u de wortelweg gebruikt die u omleiding voor en niet een verschillende weg vormde.

>[!INFO]
>
>Zie [ plaatskaart en onderzoekmachine robots ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) voor gedetailleerde instructies toevoegen.


### Meerdere winkelvoorkeuren

U kunt meerdere winkels instellen en uitvoeren met één Adobe Commerce-implementatie op een cloudinfrastructuur. Zie [ Opstelling veelvoudige websites of opslag ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

De zelfde beste praktijken voor het vormen van de `robots.txt` en `sitemap.xml` dossiers voor [ enig-plaats opslagefronts ](#single-site-storefronts) zijn op multi-site storefronts met twee belangrijke verschillen van toepassing:

- Zorg ervoor dat de bestandsnamen `robots.txt` en `sitemap.xml` de namen van de overeenkomende sites bevatten. Bijvoorbeeld:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Gebruik een enigszins aangepast VCL-fragment dat snel kan worden aangepast om de hoofdmap van uw sites om te leiden naar de locatie `pub/media` voor beide bestanden op uw sites:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce ter plaatse

Gebruik de toepassing Admin om de `robots.txt` en `sitemap.xml` dossiers te vormen om bots te verhinderen onnodige inhoud (zie [ Robots van de Motor van het Onderzoek ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=nl-NL#search-engine-robots)) af te tasten en te indexeren.

>[!TIP]
>
>Voor implementaties op locatie, waarbij u de bestanden schrijft, is afhankelijk van de manier waarop u Adobe Commerce hebt geïnstalleerd. Schrijf de bestanden naar `/path/to/commerce/pub/media/` of `/path/to/commerce/media` , afhankelijk van wat voor de installatie geschikt is.

## Beveiliging

Maak het beheerpad niet zichtbaar in uw `robots.txt` -bestand. Het blootstellen van het Admin-pad is een kwetsbaarheid voor het hacken van sites en mogelijk gegevensverlies. Verwijder het beheerpad uit het `robots.txt` -bestand.

Voor stappen om het `robots.txt` dossier uit te geven en alle ingangen van de weg te verwijderen Admin, zie [ de Gids van de Gebruiker van de Marketing > SEO en Onderzoek > de Robots van de Motor van het Onderzoek ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=nl-NL#search-engine-robots).

>[!TIP]
>
>Als u hulp nodig hebt, [ voorleggen een kaartje van de Steun van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket).

## Aanvullende informatie

- [ Begrip websites, opslag, en opslagmeningen ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [ Toevoegend websites ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [ Gebruik snel om kwaadwillig verkeer voor uw plaatsen van Adobe Commerce te blokkeren ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [ robots.txt geeft een fout 404 in Adobe Commerce op wolkeninfrastructuur 2.3.x ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html?lang=nl-NL)

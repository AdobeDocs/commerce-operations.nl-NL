---
title: Aanbevolen procedures voor het configureren van de bestanden "robots.txt" en "sitemap.xml"
description: Leer hoe u instructies over uw Adobe Commerce-site doorgeeft aan webcrawlers.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Aanbevolen procedures voor het configureren `robots.txt` en `sitemap.xml` bestanden

Dit artikel biedt tips en trucs voor het gebruik van `robots.txt` en `sitemap.xml` bestanden in Adobe Commerce, inclusief configuratie en beveiliging. Met deze bestanden wordt aan webrobots (meestal robots met zoekmachines) uitgelegd hoe u door pagina&#39;s op een website kunt bladeren. Door deze bestanden te configureren, kunt u de prestaties van de site verbeteren en de zoekmachine optimaliseren.

>[!NOTE]
>
>Deze best practices zijn alleen van toepassing op projecten die gebruikmaken van de native Adobe Commerce-winkel. Ze zijn niet van toepassing op Adobe Commerce-projecten die andere opslagoplossingen gebruiken (bijvoorbeeld Adobe Experience Manager, zonder kop).

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Adobe Commerce over cloudinfrastructuur

Een standaard Adobe Commerce-project bevat een hiërarchie die één website, winkel en opslagweergave bevat. Voor complexere implementaties kunt u aanvullende websites, winkels en winkelweergaven maken voor een _meerdere sites_ storefront.

### Single-site winkelefronts

Volg deze beste praktijken wanneer het vormen van `robots.txt` en `sitemap.xml` bestanden voor één site-winkels:

- Zorg ervoor dat uw project gebruikt [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versie 2002.0.12 of hoger.
- Gebruik de beheertoepassing om inhoud toe te voegen aan de `robots.txt` bestand.

  >[!TIP]
  >
  >De automatisch gegenereerde weergave weergeven `robots.txt` bestand voor je winkel op `<domain.your.project>/robots.txt`.

- Gebruik de beheertoepassing om een `sitemap.xml` bestand.

  >[!IMPORTANT]
  >
  >Vanwege het alleen-lezen bestandssysteem op Adobe Commerce voor cloud-infrastructuurprojecten moet u de `pub/media` pad voordat het bestand wordt gegenereerd.

- Een aangepast VCL-fragment snel gebruiken om van de hoofdmap van uw site naar de `pub/media/` locatie voor beide bestanden:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Test de omleiding door de bestanden weer te geven in een webbrowser. Bijvoorbeeld: `<domain.your.project>/robots.txt` en `<domain.your.project>/sitemap.xml`. Zorg ervoor u de wortelweg gebruikt die u omleiding voor en niet een verschillende weg vormde.

>[!INFO]
>
>Zie [Robots voor site-toewijzing en zoekprogramma&#39;s toevoegen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) voor gedetailleerde instructies.


### Meerdere winkelcentra

U kunt meerdere winkels instellen en uitvoeren met één Adobe Commerce-implementatie op een cloudinfrastructuur. Zie [Meerdere websites of winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Dezelfde aanbevolen procedures voor het configureren van de `robots.txt` en `sitemap.xml` bestanden voor [één-plaatsopslag](#single-site-storefronts) is van toepassing op meerdere winkelcentra met twee belangrijke verschillen:

- Zorg ervoor dat de `robots.txt` en `sitemap.xml` bestandsnamen bevatten de namen van de overeenkomstige sites. Bijvoorbeeld:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Gebruik een enigszins gewijzigd VCL-fragment van het type Fastly om van de hoofdmap van uw sites om te leiden naar de `pub/media` locatie voor beide bestanden op uw sites:

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

Gebruik de beheertoepassing om de `robots.txt` en `sitemap.xml` bestanden om te voorkomen dat bones onnodige inhoud scannen en indexeren (zie [Zoekmachinekrobots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Voor implementaties op locatie, waarbij u de bestanden schrijft, is afhankelijk van de manier waarop u Adobe Commerce hebt geïnstalleerd. Bestanden schrijven naar `/path/to/commerce/pub/media/` of `/path/to/commerce/media`, afhankelijk van wat voor installatie geschikt is.

## Beveiliging

Maak het beheerpad niet zichtbaar in uw `robots.txt` bestand. Het blootstellen van het Admin-pad is een kwetsbaarheid voor het hacken van sites en mogelijk gegevensverlies. Het beheerpad verwijderen uit het dialoogvenster `robots.txt` bestand.

Voor stappen om de `robots.txt` bestand en alle items van het beheerpad verwijderen, raadpleegt u [Handleiding voor marketinggebruikers > SEO en zoeken > Zoekmachine-robots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Als u hulp nodig hebt, [een Adobe Commerce-ondersteuningsticket verzenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Aanvullende informatie

- [Werken met websites, winkels en winkelweergaven](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Websites toevoegen](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Gebruik Fastly om kwaadwillig verkeer voor uw plaatsen van Adobe Commerce te blokkeren](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt geeft een fout van 404 in Adobe Commerce op wolkeninfrastructuur 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)

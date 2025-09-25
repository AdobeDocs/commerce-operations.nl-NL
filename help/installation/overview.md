---
title: Overzicht van installatie op locatie
description: Leer meer over het installatieproces voor een Adobe Commerce-uitrol op locatie.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 9ad18dac76f171ad0f90330e1a1347baa056403b
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 2%

---


# Overzicht van installatie op locatie

Deze pagina biedt een overzicht van het installeren van Adobe Commerce op uw eigen infrastructuur. Het installatieproces omvat het instellen van de serveromgeving, het verkrijgen van de vereiste software en referenties en het uitvoeren van de installatieopdracht.

U kunt de Adobe Commerce-software op locatie in ongeveer 30 tot 60 minuten installeren. De tijd die nodig is om uw serveromgeving in te stellen voordat de installatie wordt uitgevoerd, is echter afhankelijk van uw ervaring en de technologieën die u selecteert.

>[!TIP]
>
>U zou tussenliggende technische kennis en servertoegang moeten hebben om met succes te werk te gaan.

De installatie leidt tot een volledig functionele opslag van Adobe Commerce met zowel a [ klant-onder ogen ziet storefront ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/storefront/storefront) als een [ administratief paneel ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/admin/admin). U moet uw gegevensbestandgeloofsbrieven, domeininformatie, en authentificatietoetsen klaar hebben alvorens met het proces te beginnen.

## Handelstaken

Met Adobe Commerce op locatie kunt u uw eigen infrastructuur hosten en beheren, waaronder servers, hostomgevingen en systeemonderhoud. Adobe biedt specifieke ondersteuning voor de belangrijkste Commerce-toepassing, waaronder:

- Toegang tot productupdates en oplossingen
- Beveiligingspatches om kwetsbaarheden te verhelpen
- Uitgebreide documentatie die u helpt bij het beheren en optimaliseren van uw zelfgehoste oplossing

U hebt volledige controle over uw omgeving, zodat u meer aanpassingen en flexibiliteit kunt maken, maar u bent verantwoordelijk voor de prestaties, beveiliging en schaalbaarheid van de infrastructuur. U bent bijvoorbeeld verantwoordelijk voor het volgende:

- Het ontwerp, de implementatie, de configuratie, het onderhoud, het oplossen van problemen en de prestatietests van alle Adobe Commerce op gebouwsystemen.
   - Servers, besturingssysteem, databases, [!DNL PHP], zoeken, in cache plaatsen, volledige paginacache en netwerk voor het leveren van inhoud. Algemene thema&#39;s kunnen (maar niet beperkt tot) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] en alle gebruikte [!DNL CDN] elementen bevatten.
- Capaciteitsplanning, automatische schaling, clustering, back-ups, noodherstel
- Alle product en klantengegevens, ontwerp, configuratie en opstelling, toepassing en gegevensbestandonderhoud, codeplaatsing, versieverbeteringen, en flardtoepassing
- Bewaking en waarschuwingen via APM/loggen/waarschuwen (bijvoorbeeld [!DNL New Relic], [!DNL Datadog], [!DNL ELK] )
- Beveiligingspatches voor besturingssysteem, [!DNL PHP], database, hardware-harding en -updates

## Workflow

In het volgende diagram worden de belangrijkste stappen geïllustreerd die nodig zijn voor de installatie van Adobe Commerce voor omgevingen op locatie:

![ hoe de installatie ](../assets/installation/on-premises-install.drawio.svg) werkt

### De serveromgeving instellen

Installeer en vorm PHP, Webserver, gegevensbestand, en onderzoeksmotor volgens de [ eerste vereisten ](prerequisites/overview.md).

### Verificatietoetsen ophalen

Produceer nieuwe [ authentificatietoetsen ](prerequisites/authentication-keys.md) (of kopieer bestaande sleutels) van Commerce Marketplace om tot de pakketten van de Composer van Adobe Commerce toegang te hebben.

### De Adobe Commerce-software ophalen

Download gebruikend [ Composer ](prerequisites/commerce.md) (geadviseerd) of kloon van GitHub voor ontwikkelingsbijdragen.

Als u aan de codebase van Magento Open Source wilt bijdragen of de toepassing aanpassen, [ kloon ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) de bewaarplaats GitHub. Deze methode vereist vertrouwdheid met zowel GitHub als Composer.

### De toepassing installeren

Voer de installatieopdracht uit met uw specifieke configuratie. Zie het [ snelle begin ](composer.md) voor volledige voorbeelden.

>[!NOTE]
>
>Als de stappen ontbreken omdat de in de eerste plaats vereiste software niet correct opstelling is, herzie de [ eerste vereisten ](prerequisites/overview.md).

### De installatie controleren

[ Test ](next-steps/verify.md) uw storefront en admin paneel om alles te verzekeren werkt correct.

## Algemene installatieproblemen

- **de fouten van de Toestemming**: Zorg de juiste eigendom en de toestemmingen van het dossiersysteem
- **de verbindingsmislukkingen van het Gegevensbestand**: Verifieer gegevensbestandgeloofsbrieven en netwerkconnectiviteit
- **de zeer belangrijke fouten van de Authentificatie**: Bevestig dat uw sleutels van Commerce Marketplace geldig en actief zijn
- **de grenzen van het Geheugen**: Zorg voldoende PHP geheugentoewijzing (geadviseerde minimum 2GB)

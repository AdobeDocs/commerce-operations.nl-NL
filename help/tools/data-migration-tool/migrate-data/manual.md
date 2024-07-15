---
title: Gegevens die handmatige migratie vereisen
description: Meer informatie over gegevens die handmatig moeten worden gemigreerd tijdens een Magento 1 naar Magento 2-gegevensmigratie en over hoe u dit kunt doen.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Gegevens die handmatige migratie vereisen

Er zijn vier soorten gegevens die handmatig moeten worden gemigreerd:

* Media

* Storefront-ontwerp

* Gebruikersaccounts voor beheerders

* Access Control Lists (ACL&#39;s)

## Media

In deze sectie wordt beschreven hoe u mediabestanden handmatig kunt migreren.

### In de database opgeslagen mediabestanden

>[!WARNING]
>
>De opslagmethode voor databasemedia wordt vanaf Magento 2.4.3 afgekeurd.


Deze sectie is op u *slechts* van toepassing als u media dossiers in het gegevensbestand van het Magento opslaat. Deze stap zou vóór [ migratie van gegevens ](data.md) moeten worden uitgevoerd:

1. Meld u als beheerder aan bij het deelvenster Beheer Magento 1.

1. Klik **Systeem** > **Configuratie** > GEAVANCEERD > **Systeem**.

1. In de juiste ruit, rol aan **Configuratie van de Opslag voor Media**.

1. Van de **Uitgezochte Lijst van het Gegevensbestand van Media**, klik de naam van uw gegevensbestand van de media opslag.

1. Klik **synchroniseren**.

Herhaal vervolgens dezelfde stappen in het deelvenster Beheer van Magento 2.

### Mediabestanden in het bestandssysteem

Alle mediabestanden (afbeeldingen voor producten, categorieën, de WYSIWYG-editor, enzovoort) moeten handmatig van `<your Magento 1 install dir>/media` naar `<your Magento 2 install dir>/pub/media` worden gekopieerd.

Nochtans, kopieer ** niet de `.htaccess` dossiers die in Magento 1 `media` worden gevestigd omslag. Magento 2 heeft een eigen `.htaccess` die behouden moet blijven.

## Storefront-ontwerp

* Het ontwerp in bestanden (CSS, JS, sjablonen, XML-lay-outs) is gewijzigd qua locatie en indeling

* Layout Updates opgeslagen in de database. Geplaatst via Magento 1 Admin in CMS-pagina&#39;s, CMS-widgets, categoriepagina&#39;s en productpagina&#39;s

## Access Control Lists (ACL&#39;s)

U moet alle handmatig opnieuw maken:

* referenties voor webservice-API&#39;s (SOAP, XML-RPC en REST)

* administratieve gebruikersrekeningen en associeer hen met toegangsvoorrechten

>[!NOTE]
>
>U kunt de tijdzone voor een database-entiteit aanpassen met de handler `\Migration\Handler\Timezone` . Zie de [ follow-up ](follow-up.md) sectie voor meer details.

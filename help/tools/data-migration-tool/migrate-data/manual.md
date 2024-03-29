---
title: Gegevens die handmatige migratie vereisen
description: Meer informatie over gegevens die handmatig moeten worden gemigreerd tijdens een Magento 1 naar Magento 2-gegevensmigratie en over hoe u dit kunt doen.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '278'
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


Deze sectie is op u van toepassing *alleen* als u mediabestanden opslaat in de database Magento. Deze stap moet worden uitgevoerd vóór [migratie van gegevens](data.md):

1. Meld u als beheerder aan bij het deelvenster Beheer Magento 1.

1. Klikken **Systeem** > **Configuratie** > GEAVANCEERD > **Systeem**.

1. Blader in het rechterdeelvenster naar **Opslagconfiguratie voor media**.

1. Van de **Mediabase selecteren** klikt u op de naam van de database voor mediaopslag.

1. Klikken **Synchroniseren**.

Herhaal vervolgens dezelfde stappen in het deelvenster Beheer van Magento 2.

### Mediabestanden in het bestandssysteem

Alle mediabestanden (afbeeldingen voor producten, categorieën, de WYSIWYG-editor, enzovoort) moeten handmatig worden gekopieerd van `<your Magento 1 install dir>/media` tot `<your Magento 2 install dir>/pub/media`.

Maar *niet* kopieer de `.htaccess` bestanden in Magento 1 `media` map. Magento 2 heeft zijn eigen `.htaccess` dat moet worden gehandhaafd .

## Storefront-ontwerp

* Het ontwerp in bestanden (CSS, JS, sjablonen, XML-lay-outs) is gewijzigd qua locatie en indeling

* Layout Updates opgeslagen in de database. Geplaatst via Magento 1 Admin in CMS-pagina&#39;s, CMS-widgets, categoriepagina&#39;s en productpagina&#39;s

## Access Control Lists (ACL&#39;s)

U moet alle handmatig opnieuw maken:

* referenties voor webservice-API&#39;s (SOAP, XML-RPC en REST)

* administratieve gebruikersrekeningen en associeer hen met toegangsvoorrechten

>[!NOTE]
>
>U kunt de tijdzone voor een databaseentiteit aanpassen met de `\Migration\Handler\Timezone` handler. Zie de [follow-up](follow-up.md) voor meer informatie.

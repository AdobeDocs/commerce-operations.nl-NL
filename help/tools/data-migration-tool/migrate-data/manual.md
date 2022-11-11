---
title: Gegevens die handmatige migratie vereisen
description: Meer informatie over gegevens die handmatig moeten worden gemigreerd tijdens een gegevensmigratie van Magento 1 tot en met Magento 2 en over hoe u dit kunt doen.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Gegevens die handmatige migratie vereisen

Er zijn vier soorten gegevens die handmatig moeten worden gemigreerd:

* Media

* [Storefront](https://glossary.magento.com/storefront) ontwerp

* [Beheer](https://glossary.magento.com/admin) gebruikersaccounts

* Access Control Lists (ACL&#39;s)

## Media

In deze sectie wordt beschreven hoe u mediabestanden handmatig kunt migreren.

### In de database opgeslagen mediabestanden

>[!WARNING]
>
>De opslagmethode voor databasemedia wordt vanaf Magento 2.4.3 afgekeurd.


Deze sectie is op u van toepassing *alleen* als u mediabestanden opslaat in de Magento-database. Deze stap moet worden uitgevoerd vóór [migratie van gegevens](data.md):

1. Meld u als beheerder aan bij het deelvenster Beheer Magento 1.

1. Klikken **Systeem** > **Configuratie** > GEAVANCEERD > **Systeem**.

1. Blader in het rechterdeelvenster naar **Opslagconfiguratie voor media**.

1. Van de **Mediabase selecteren** Klik op de naam van uw [media-opslag](https://glossary.magento.com/media-storage) database.

1. Klikken **Synchroniseren**.

Herhaal vervolgens dezelfde stappen in het deelvenster Beheer Magento 2.

### Mediabestanden in het bestandssysteem

Alle mediabestanden (afbeeldingen voor producten, categorieën, [WYSIWYG](https://glossary.magento.com/wysiwyg) editor, enzovoort) moet u handmatig kopiëren van `<your Magento 1 install dir>/media` tot `<your Magento 2 install dir>/pub/media`.

Maar *niet* kopiëren `.htaccess` bestanden in de Magento 1 `media` map. Magento 2 heeft zijn eigen `.htaccess` dat moet worden gehandhaafd .

## Storefront-ontwerp

* Ontwerp in bestanden (CSS, JS, sjablonen, [XML](https://glossary.magento.com/xml) lay-outs) zijn locatie en indeling gewijzigd

* [Layout](https://glossary.magento.com/layout) Updates die zijn opgeslagen in de database. Geplaatst via Magento 1 Admin [CMS](https://glossary.magento.com/cms) Pagina&#39;s, CMS-widgets, [Categorie](https://glossary.magento.com/category) Pagina&#39;s en productpagina&#39;s

## Access Control Lists (ACL&#39;s)

U moet alle handmatig opnieuw maken:

* referenties voor webservice-API&#39;s (SOAP, XML-RPC en REST)

* administratieve gebruikersrekeningen en associeer hen met toegangsvoorrechten

>[!NOTE]
>
>U kunt de tijdzone voor een databaseentiteit aanpassen met de `\Migration\Handler\Timezone` handler. Zie de [follow-up](follow-up.md) voor meer informatie.

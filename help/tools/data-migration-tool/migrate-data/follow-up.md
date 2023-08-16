---
title: Follow-up gegevensmigratie
description: Leer hoe u kunt controleren of de gegevensmigratie tussen Magento 1 en Magento 2 is gelukt en of alle functionaliteit naar behoren functioneert.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Follow-up gegevensmigratie

Sommige gedragingen en logica van Magento 1 zijn in Magento 2 anders geïmplementeerd. De [!DNL Data Migration Tool] zorgt ervoor. Er zijn enkele migratieaspecten die u bekend moet maken, en soms moet u kleine stappen nemen om sommige functies na migratie probleemloos te laten werken.

## Informatie

### Gesplitste database niet ondersteund

De [!DNL Data Migration Tool] ondersteunt geen gesplitste databases.

### Groepsprijzen geconverteerd naar Tier-prijzen

Alle groepsprijzen worden tijdens de migratie automatisch omgezet in Tier-prijzen.

### Nieuwe nummering voor verkoopentiteiten

Referentienummers voor bestellingen, facturen, verzendingen, creditmemo&#39;s en RMA migreren naar de huidige vorm. Na de migratie zijn de nieuwe Magento 2 regels voor nummertoewijzing van toepassing. De nummering voor de nieuwe verkoopeenheden is anders.

## Stappen

### Klantsegmenten opnieuw opslaan [Alleen Adobe Commerce]

Na de migratie moeten de segmenten van de Klant van het Admin Comité worden opnieuw bewaard om hen op en in werking te stellen.

### Tijdzone configureren

Het hulpmiddel migreert timezone geen montages, zodat moet u de timezone na migratie manueel vormen bij **Winkels** > **Configuratie** > **Landinstellingen** > **Tijdzone**.

Door gebrek, slaat het Magento tijdgegevens in UTC-0 streek in het gegevensbestand op en toont het volgens de huidige tijdzonemontages. Als de tijdgegevens al in het gegevensbestand in een andere streek dan UTC-0 zijn opgeslagen, moet u de bestaande tijd in UTC-0 omzetten gebruikend [!DNL Data Migration Tool]s `\Migration\Handler\Timezone` handler.

In het volgende voorbeeld bespaart Magento 1 verkeerd tijd in de streek UTC-7 in het gegevensbestand (bijvoorbeeld, wegens een defecte derdeuitbreiding). Voer de volgende stappen uit om de aanmaaktijd van de klantenaccount correct om te zetten in de UTC-0-zone bij migratie:

1. De `map-customer.xml.dist` configuratiebestand uit de desbetreffende map van het [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) in de `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` bestand.

1. Werk de `<customer_map_file>` node in `config.xml` en verwijder de `.dist` verlenging van `map-customer.xml.dist`

1. Voeg de volgende regel toe aan de `map-customer.xml` bestand:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```

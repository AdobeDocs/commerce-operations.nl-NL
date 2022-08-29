---
title: Follow-up gegevensmigratie
description: Leer hoe u kunt controleren of de gegevensmigratie tussen Magento 1 en Magento 2 is gelukt en of alle functies naar behoren werken.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Follow-up gegevensmigratie

Sommige gedragingen en logica van Magento 1 zijn anders geïmplementeerd in Magento 2. De [!DNL Data Migration Tool] zorgt ervoor. Er zijn enkele migratieaspecten die u bekend moet maken, en soms moet u kleine stappen nemen om sommige functies na migratie probleemloos te laten werken.

## Informatie

### Gesplitste database niet ondersteund

De [!DNL Data Migration Tool] ondersteunt geen gesplitste databases.

### Groepsprijzen geconverteerd naar Tier-prijzen

Alle groepsprijzen worden tijdens de migratie automatisch omgezet in Tier-prijzen.

### Nieuwe nummering voor verkoopentiteiten

Referentienummers voor bestellingen, facturen, verzendingen, creditmemo&#39;s en RMA migreren naar de huidige vorm. Na migratie zijn de nieuwe regels voor de toewijzing van Magento 2-nummers van toepassing. De nummering voor de nieuwe verkoopeenheden is anders.

## Stappen

### Klantsegmenten opnieuw opslaan [Alleen Adobe Commerce]

Na de migratie moeten de segmenten van de Klant van het [Beheer](https://glossary.magento.com/admin) Deelvenster om ze weer aan de slag te krijgen.

### Tijdzone configureren

Het hulpmiddel migreert timezone geen montages, zodat moet u de timezone na migratie manueel vormen bij **Winkels** > **Configuratie** > **Landinstellingen** > **Tijdzone**.

Standaard slaat Magento tijdgegevens op in de UTC-0-zone in de database en wordt deze weergegeven volgens de huidige tijdzone-instellingen. Als de tijdgegevens al in het gegevensbestand in een andere streek dan UTC-0 zijn opgeslagen, moet u de bestaande tijd in UTC-0 omzetten gebruikend [!DNL Data Migration Tool]s `\Migration\Handler\Timezone` handler.

In het volgende voorbeeld bespaart Magento 1 ten onrechte tijd in de UTC-7-zone in de database (bijvoorbeeld als gevolg van een onjuiste extensie van derden). Voer de volgende stappen uit om de aanmaaktijd van de klantenaccount correct om te zetten in de UTC-0-zone bij migratie:

1. Kopieer de `map-customer.xml.dist` configuratiebestand uit de desbetreffende map van het [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) in de `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` bestand.

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

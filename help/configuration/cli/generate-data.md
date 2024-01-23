---
title: Gegevens genereren voor het testen van prestaties
description: Leer hoe u een grote hoeveelheid gegevens genereert die u kunt gebruiken voor het testen van de prestaties.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: d4a6d5cd181c7c4426914bbe481f4d5d1e828b5e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 9%

---

# Prestatie testgegevens

## Profielen

U kunt de hoeveelheid gegevens aanpassen die u maakt met _profielen_ (klein, middelgroot, groot en extra groot). Profielen bevinden zich in de `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` directory.

Bijvoorbeeld: `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

Het volgende cijfer toont hoe een product op de winkel gebruikend wordt getoond _klein_ profiel:

![Voorbeeld van opslag met gegenereerde gegevens](../../assets/configuration/generate-data.png)

De volgende tabel bevat details over de profielen van de gegevensgenerator: klein, middelgroot, groot en extra groot.

| Parameter | Klein profiel | Normaal profiel | Normaal profiel voor meerdere sites | Groot profiel | Extra groot profiel |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24.000 | 4.000 | 300.000 | 600.000 |
| `configurable_products` | 16 met 24 opties | 640 met 24 opties | 800 met 24 opties en 79 met 200 opties | 8.000 met 24 opties | 16.000 met 24 opties |
| `product_images` | 100 afbeeldingen / 3 afbeeldingen per product | 1000 afbeeldingen / 3 afbeeldingen per product | 1000 afbeeldingen / 3 afbeeldingen per product | 2000 afbeeldingen / 3 afbeeldingen per product | 2000 afbeeldingen / 3 afbeeldingen per product |
| `categories` | 30 | 300 | 100 | 3.000 | 6.000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2.000 | 2.000 | 5.000 | 10.000 |
| `tax rates` | 130 | 40.000 | 40.000 | 40.000 | 40.000 |
| `orders` | 80 | 50.000 | 50.000 | 100.000 | 150.000 |

### De gegevensgenerator uitvoeren

{{file-system-owner}}

>[!WARNING]
>
>Voordat u de gegevensgenerator uitvoert, schakelt u alle snijtaken uit die op de server worden uitgevoerd. Als u de functie voor uitsnijden uitschakelt, voorkomt u dat de gegevensgenerator handelingen uitvoert die een conflict veroorzaken met actieve uitsnijdtaken en dat onnodige fouten worden voorkomen.
>
>Als u de gebeurtenis wilt implementeren met [!DNL Adobe I/O Events for Adobe Commerce] tijdens het testen van de prestaties, voer deze opdracht uit voordat u zich abonneert [gebeurtenissen](https://developer.adobe.com/commerce/extensibility/events/). Als u zich eerst abonneert op gebeurtenissen, kunnen er fouten optreden.

Voer de opdracht uit zoals in deze sectie wordt beschreven. Nadat het bevel loopt, moet u [alle indexen opnieuw indexeren](../cli/manage-indexers.md).

Opdrachtopties:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Wanneer `<path-to-profile>` geeft het absolute pad van het bestandssysteem naar en de naam van een profiel op.

Bijvoorbeeld:

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Voorbeelduitvoer voor het kleine profiel:

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## Prestatiecorrecties

### Beheergebruikers

Hiermee genereert u beheergebruikers. XML-profielknooppunt:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Kenmerksets

Genereert kenmerkreeksen met gespecificeerde configuratie. XML-profielknooppunt:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Bundelproducten

Genereert bundelproducten. Gegenereerde bundelselecties worden niet afzonderlijk weergegeven in de catalogus. Producten worden gelijkmatig verdeeld over categorieën en websites. Indien  `assign_entities_to_all_websites` uit het profiel is ingesteld op `1`. Producten worden toegewezen aan alle websites.

XML-profielknooppunt:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Prijsregels voor winkelwagentjes

Hiermee genereert u regels voor de kartprijs. XML-profielknooppunt:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Regels inzake catalogusprijzen

Genereert prijsregels voor catalogi. XML-profielknooppunt:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Categorieën

Hiermee genereert u categorieën. Indien `assign_entities_to_all_websites` is ingesteld op `0`, worden alle categorieën gelijkmatig verdeeld per wortelcategorieën; anders, worden alle categorieën toegewezen aan één wortelcategorie.

XML-profielknooppunt:

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### Configs

Stelt waarden in voor configuratievelden. XML-profielknooppunt:

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### Configureerbare producten

Hiermee genereert u configureerbare producten. Gegenereerde configureerbare opties worden niet afzonderlijk weergegeven in de catalogus. Producten worden gelijkmatig verdeeld over categorieën en websites. Indien `assign_entities_to_all_websites` is ingesteld op `1`, worden producten aan alle websites toegewezen.

De volgende XML-knooppuntindelingen worden ondersteund:

- Distributie per standaard en vooraf gedefinieerde kenmerksets:

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- Producten genereren op basis van een bestaande kenmerkset:

  ```xml
  <configurable_products>
  
      <config>
              <!-- Existing attribute set name -->
              <attributeSet>{string}</attributeSet>
  
              <!-- Configurable sku pattern with %s -->
              <sku>{string}</sku>
  
              <!-- Number of configurable products -->
              <products>{int}</products>
  
              <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
              <category>[{string}]</category>
  
              <!-- Type of Swatch attribute e.g. color|image -->
              <swatches>{string}</swatches>
      </config>
  
  <!-- ... more entries ... -->
  </configurable_products>
  ```

- Produceren op basis van een dynamisch gemaakt kenmerk ingesteld met een opgegeven aantal kenmerken en opties:

  ```xml
  <configurable_products>
  
      <config>
          <!-- Number of attributes in configurable product -->
          <attributes>{int}</attributes>
  
          <!-- Number of options per attribute -->
          <options>{int}</options>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
          <category>[{string}]</category>
  
          <!-- Type of Swatch attribute e.g. color|image -->
          <swatches>{string}</swatches>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

- Produceer producten die op een dynamisch gecreeerd attribuut worden gebaseerd dat met een gespecificeerde configuratie per elk attribuut wordt geplaatst:

  ```xml
  <configurable_products>
  
      <config>
          <attributes>
              <!-- Configuration for a first attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
  
                  <!-- Type of Swatch attribute -->
                  <swatches>{string}</swatches>
              </attribute>
  
              <!-- Configuration for a second attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
              </attribute>
          </attributes>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
          <category>[{string}]</category>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

### Klanten

Hiermee genereert u klanten. Klanten hebben een normale distributie op alle beschikbare websites. Elke klant heeft dezelfde gegevens, met uitzondering van de e-mail van de klant, de klantengroep en de klantadressen.

XML-profielknooppunt:

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

U kunt de volgende XML gebruiken om de klantenconfiguratie te veranderen:

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### Productafbeeldingen

Hiermee genereert u productafbeeldingen. Genereren omvat niet vergroten/verkleinen.

XML-profielknooppunt:

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### Indexeerstatus

Werkt de status van de indexeerders bij. XML-profielknooppunt:

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### Orders

Hiermee genereert u orders met een configureerbaar aantal verschillende typen orderitems. Hiermee worden optioneel inactieve aanhalingstekens voor gegenereerde orders gegenereerd.

XML-profielknooppunt:

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### Eenvoudige producten

Hiermee genereert u eenvoudige producten. De producten worden verdeeld per gebrek en vooraf bepaalde attributenreeksen. Als extra kenmerksets in profiel worden opgegeven als: `<product_attribute_sets>{int}</product_attribute_sets>`, worden de producten ook verdeeld per extra attributenreeksen.

Producten worden gelijkmatig verdeeld over categorieën en websites. Indien `assign_entities_to_all_websites` is ingesteld op `1`, worden producten aan alle websites toegewezen.

XML-profielknooppunt:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Websites

Genereert websites. XML-profielknooppunt:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Winkelgroepen

Genereert opslaggroepen (in de beheerder wordt verwezen naar _winkelen_). Winkelgroepen worden normaal over websites verdeeld.

XML-profielknooppunt:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Winkelweergaven

Hiermee genereert u opslagweergaven. De mening van de opslag wordt normaal verdeeld over winkelgroepen. XML-profielknooppunt:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Belastingtarieven

Hiermee genereert u belastingtarieven. XML-profielknooppunt:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Aanvullende configuratiegegevens:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml`—Standaardkenmerksets

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml`—Klantenconfiguratie

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml`—Configuratie van volledige productbeschrijving

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml`—Configuratie van productkorte beschrijving

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml`—Configuratie voor korte en volledige beschrijving van het product. Deze oudere implementatie is beschikbaar voor achterwaartse compatibiliteit.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml`—Klein aantal zoektermen tot in korte en volledige beschrijvingen

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml`—Groter aantal zoektermen dat moet worden gebruikt in korte en volledige beschrijving.

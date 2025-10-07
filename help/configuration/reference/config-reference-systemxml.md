---
title: system.xml reference
description: Leer hoe het bestand system.xml de configuratie van Adobe Commerce-toepassingen beheert. Ontdek systeemconfiguratiebeheer, de structuur van XML, en implementatietechnieken.
feature: Configuration, System
badge: label="Bijdrage van David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2717'
ht-degree: 0%

---

# system.xml reference

Met het bestand `system.xml` kunt u de Commerce-systeemconfiguratie beheren. Gebruik dit onderwerp als algemene referentie voor het `system.xml` bestand. Het `system.xml` -bestand bevindt zich onder `etc/adminhtml/system.xml` in een bepaalde Commerce 2-extensie.

Het volgende codefragment toont het blote skelet van het dossier:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Als u onmiddellijke *XSD bevestiging in uw winde wilt, kunt u `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>` in werking stellen.

## Tabs // secties // groepen // velden

In het `system.xml` -bestand is het mogelijk vier verschillende typen entiteiten te definiëren, die aan elkaar zijn gerelateerd. In de volgende sectie wordt de relatie beschreven tussen tabbladen, secties, groepen en velden. In de volgende schermafbeelding wordt de Commerce 2 System Configuration weergegeven in de Admin-back-end.
De rode vierkantjes geven de verschillende typen aan die in het `system.xml` -bestand zijn gedefinieerd:

![&#x200B; Screenshot die een gevormde sectie in Admin toont.](../../assets/configuration/magento2-system-configuration.png)

Tabs worden gebruikt om verschillende configuratiegebieden semantisch te splitsen. Elk tabblad kan een of meer secties bevatten, die ook submenu&#39;s kunnen worden genoemd. Een sectie bevat een of meer groepen.
Elke groep geeft een of meer velden weer. U kunt ook een groep gebruiken om een algemene beschrijving toe te voegen voor de volgende velden. Zoals vermeld, kan elke groep één of meerdere gebieden hebben. Velden zijn de kleinste entiteit
in de systeemconfiguratiecontext.

## Tabs

Een `<tab>` -tag verwijst naar een bestaand of een nieuw tabblad in de systeemconfiguratie.

### Referentie tabkenmerk

Een `<tab>` -tag kan de volgende kenmerken hebben:

| Kenmerk | Beschrijving | Type | Vereist |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Definieert de id die wordt gebruikt bij het verwijzen naar de sectie. | `typeId` | vereist |
| `translate` | Hiermee definieert u het veld dat moet kunnen worden vertaald. Geef `label` op om het label vertaalbaar te maken. | `string` | optioneel |
| `sortOrder` | Hiermee definieert u de sorteervolgorde van de sectie. Met een hoge waarde wordt de sectie naar de onderkant van de pagina verplaatst en met een lage waarde wordt de sectie naar de bovenkant verschoven. | `float` | optioneel |
| `class` | Voegt een gedefinieerde CSS-klasse toe aan het gerenderde tab HTML-element. | `string` | optioneel |

### Referentie tabknooppunt

Een `<tab>` -tag kan het volgende onderliggende element hebben:

| Knooppunt | Beschrijving | Type |
|---------|------------------------------------------------------|----------|
| `label` | Definieert het label dat in de voorzijde wordt weergegeven. | `string` |

### Voorbeeld: Een tabblad maken

In het volgende codefragment ziet u hoe u een nieuw tabblad maakt met voorbeeldgegevens.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Het bovenstaande fragment maakt een nieuw tabblad met de id `A_UNIQUE_ID` . Terwijl het kenmerk `translate` wordt gedefinieerd en naar het label verwijst, is het knooppunt `label` vertaalbaar. Tijdens het renderingsproces wordt de CSS-klasse `a-custom-css-class-to-style-this-tab` toegepast op het HTML-element dat voor dit tabblad is gemaakt.
Het kenmerk `sortOrder` met de waarde `10` definieert de positie van de tab in de lijst met alle tabbladen wanneer deze wordt gerenderd.

## Secties

Een `<section>` -tag verwijst naar een bestaande of een nieuwe sectie in de systeemconfiguratie.

### Verwijzing naar kenmerk Sectie

Een `<section>` -tag kan de volgende kenmerken hebben:

| Kenmerk | Beschrijving | Type | Vereist |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definieert de id die wordt gebruikt bij het verwijzen naar de sectie. | `typeId` | vereist |
| `translate` | Hiermee definieert u het veld dat moet kunnen worden vertaald. Geef `label` op om het label vertaalbaar te maken. | `string` | optioneel |
| `type` | Definieert het invoertype van het gerenderde HTML-element. Wordt standaard ingesteld op `text` . | `string` | optioneel |
| `sortOrder` | Hiermee definieert u de sorteervolgorde van de sectie. Bij een hoge waarde wordt de sectie onder aan de pagina geplaatst. Bij een lage waarde wordt de sectie naar de bovenkant verschoven. | `float` | optioneel |
| `showInDefault` | Bepaalt of de sectie in het standaardconfiguratiewerkingsgebied wordt getoond. Geef `1` op om de sectie weer te geven en `0` om de sectie te verbergen. | `int` | optioneel |
| `showInStore` | Bepaalt of de sectie op archiefniveau wordt getoond. Geef `1` op om de sectie weer te geven en `0` om de sectie te verbergen. | `int` | optioneel |
| `showInWebsite` | Bepaalt of de sectie op websiteniveau wordt getoond. Geef `1` op om de sectie weer te geven en `0` om de sectie te verbergen. | `int` | optioneel |
| `canRestore` | Definieert of de sectie kan worden teruggezet op de standaardwaarde. | `int` | optioneel |
| `advanced` | Vervangen vanaf 10.0.2. | `bool` | optioneel |
| `extends` | Door een id van een andere sectie op te geven, breidt de inhoud van dit knooppunt de sectie uit waarnaar u verwijst. | `string` | optioneel |

### Verwijzing naar knooppunt

Een `<section>` -tag kan de volgende onderliggende elementen hebben:

| Knooppunt | Beschrijving | Type |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Definieert het label dat in de voorzijde wordt weergegeven. | `string` |
| `class` | Voegt een gedefinieerde CSS-klasse toe aan het gerenderde HTML-element van de sectie. | `string` |
| `tab` | Verwijst naar het bijbehorende tabblad. Hiermee wordt de id van het tabblad verwacht. | `typeTabId` |
| `header_css` | Op het moment van schrijven is deze functie niet gebruikt en niet geëvalueerd. | `string` |
| `resource` | Verwijst naar een ACL middel om toestemmingsmontages voor deze sectie te verstrekken. | `typeAclResourceId` |
| `group` | Definieer een of meer subgroepen. | `typeGroup` |
| `frontend_model` | Geeft een ander frontend model op om de rendering te wijzigen en de uitvoer te wijzigen. | `typeModel` |
| `include` | Wordt gebruikt om extra `system_include.xsd` compatibele bestanden op te nemen. Wordt meestal gebruikt om grote `system.xml` bestanden te structureren. | `includeType` |

### Voorbeeld: Een sectie maken en toewijzen aan een tabblad

In het volgende codefragment ziet u het basisgebruik van het maken van een nieuwe sectie.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

De sectie die hierboven wordt beschreven bepaalt identiteitskaart `A_UNIQUE_SECTION_ID`, is zichtbaar in het gebrek config mening en in een archiefcontext. Het knooppunt `label` is vertaalbaar. De sectie wordt gekoppeld aan de tab met de id `A_UNIQUE_ID` . De sectie kan slechts door gebruikers worden betreden die de toestemmingen hebben die in ACL `VENDOR_MODULE::path_to_the_acl_resource` worden bepaald.

## Groepen

De tag `<group>` -Tag wordt gebruikt om velden samen te groeperen.

### Groepskenmerkverwijzing

Een `<group>` -tag kan de volgende kenmerken hebben:

| Kenmerk | Beschrijving | Type | Vereist |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definieert de id die wordt gebruikt bij het verwijzen naar de groep. | `typeId` | vereist |
| `translate` | Hiermee definieert u de velden die u wilt vertalen. Geef `label` op om het label vertaalbaar te maken. Meerdere velden moeten worden gescheiden door een spatie. | `string` | optioneel |
| `type` | Definieert het invoertype van het gerenderde HTML-element. Wordt standaard ingesteld op `text` . | `string` | optioneel |
| `sortOrder` | Hiermee definieert u de sorteervolgorde van de sectie. Bij een hoge waarde wordt de sectie onder aan de pagina geplaatst. Bij een lage waarde wordt de sectie naar de bovenkant verschoven. | `float` | optioneel |
| `showInDefault` | Bepaalt of de groep in het standaardconfiguratiewerkingsgebied wordt getoond. Geef `1` op om de groep weer te geven en `0` om de groep te verbergen. | `int` | optioneel |
| `showInStore` | Bepaalt of de groep op archiefniveau wordt getoond. Geef `1` op om de groep weer te geven en `0` om de groep te verbergen. | `int` | optioneel |
| `showInWebsite` | Bepaalt of de groep op websiteniveau wordt getoond. Geef `1` op om de groep weer te geven en `0` om de groep te verbergen. | `int` | optioneel |
| `canRestore` | Definieert of de standaardgroep kan worden hersteld. | `int` | optioneel |
| `advanced` | Vervangen vanaf 10.0.2. | `bool` | optioneel |
| `extends` | Door een id van een andere groep op te geven, breidt de inhoud van dit knooppunt de sectie uit waarnaar u verwijst. | `string` | optioneel |

### Referentie van knooppunt groeperen

Een `<group>` -tag kan de volgende onderliggende elementen hebben:

| Knooppunt | Beschrijving | Type |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Definieert het label dat in de voorzijde wordt weergegeven. | `string` |
| `fieldset_css` | Hiermee voegt u een of meer CSS-klassen toe aan een set groepsvelden. | `string` |
| `frontend_model` | Geeft een ander frontend model op om de rendering te wijzigen en de uitvoer te wijzigen. | `typeModel` |
| `clone_model` | Hiermee geeft u een bepaald model op voor het klonen van velden. | `typeModel` |
| `clone_fields` | Het klonen van velden is in- of uitgeschakeld. | `int` |
| `help_url` | Niet uitbreidbaar. Zie hieronder. | `typeUrl` |
| `more_url` | Niet uitbreidbaar. Zie hieronder. | `typeUrl` |
| `demo_link` | Niet uitbreidbaar. Zie hieronder. | `typeUrl` |
| `comment` | Voegt een opmerking toe onder het groeplabel. Met `<![CDATA[//]]>` kunt u HTML toepassen. | `string` |
| `hide_in_single_store_mode` | Of de groep op enige opslagwijze zichtbaar zou moeten zijn. `1` verbergt de groep; in `0` wordt de groep weergegeven. | `int` |
| `field` | Definieer een of meer velden die beschikbaar moeten zijn onder deze groep. | `field` |
| `group` | Definieer een of meer subgroepen. | `unbounded` |
| `depends` | Kan worden gebruikt om gebiedsdelen op andere gebieden te verklaren. Wordt alleen gebruikt om specifieke velden/groepen weer te geven wanneer een bepaald veld de waarde `1` heeft. Dit knooppunt verwacht een `section/group/field` -string. | `depends` |
| `attribute` | Aangepaste kenmerken kunnen worden gebruikt door frontend-modellen. Wordt meestal gebruikt om een bepaald frontend model dynamischer te maken. | `attribute` |
| `include` | Wordt gebruikt om extra `system_include.xsd` compatibele bestanden op te nemen. Wordt meestal gebruikt om grote `system.xml` bestanden te structureren. | `includeType` |

>[!WARNING]
>
>De knooppunten `more_url` , `demo_url` en `help_url` worden gedefinieerd door een PayPal-frontendmodel dat slechts eenmaal wordt gebruikt. Deze knooppunten kunnen niet opnieuw worden gebruikt.

### Voorbeeld: een groep maken voor een bepaalde sectie

In het volgende codefragment ziet u het basisgebruik van het maken van een nieuwe groep.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

De hierboven beschreven groep definieert de id `A_UNIQUE_GROUP_ID` , is zichtbaar in de standaardconfiguratieweergave en in een archiefcontext. Zowel `label` als `comment` zijn gemarkeerd als te vertalen.

## Velden

De `<field>` -tag wordt gebruikt binnen `<group>` -tags om specifieke configuratiewaarden te definiëren.

### Verwijzing veldkenmerk

Een `<field>` -tag kan de volgende kenmerken hebben:

| Kenmerk | Beschrijving | Type | Vereist |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definieert de id die wordt gebruikt bij het verwijzen naar het veld. | `typeId` | vereist |
| `translate` | Hiermee definieert u de velden die u wilt vertalen. Geef `label` op om het label vertaalbaar te maken. Meerdere velden moeten worden gescheiden door een spatie. | `string` | optioneel |
| `type` | Definieert het invoertype van het gerenderde HTML-element. Wordt standaard ingesteld op `text` . | `string` | optioneel |
| `sortOrder` | Hiermee definieert u de sorteervolgorde van de sectie. Met een hoge waarde wordt de sectie naar de onderkant van de pagina verplaatst en met een lage waarde wordt de sectie naar de bovenkant verschoven. | `float` | optioneel |
| `showInDefault` | Bepaalt of het gebied in het standaardconfiguratiewerkingsgebied wordt getoond. Geef `1` op om het veld weer te geven en `0` om het veld te verbergen. | `int` | optioneel |
| `showInStore` | Bepaalt of het gebied op archiefniveau wordt getoond. Geef `1` op om het veld weer te geven en `0` om het veld te verbergen. | `int` | optioneel |
| `showInWebsite` | Hiermee wordt gedefinieerd of het veld op websiteniveau wordt weergegeven. Geef `1` op om het veld weer te geven en `0` om het veld te verbergen. | `int` | optioneel |
| `canRestore` | Definieert of de standaardinstelling van het veld kan worden hersteld. | `int` | optioneel |
| `advanced` | Vervangen vanaf 10.0.2. | `bool` | optioneel |
| `extends` | Door een id van een ander veld op te geven, breidt de inhoud van dit knooppunt de sectie uit waarnaar u verwijst. | `string` | optioneel |

### Verwijzing naar veldtype

Een `<field>` -tag kan de volgende waarden voor het `type=""` -kenmerk hebben:

| Type | Beschrijving |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Standaard, tekstveld met één rij |
| `textarea` | Tekstblok |
| `select` | Bij een normale vervolgkeuzelijst is mogelijk een aangepaste `source_model` vereist. Wordt ook gebruikt voor `Yes/No` selecties. Zie `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` voor een voorbeeld. |
| `multiselect` | Net als `select` maar meerdere opties zijn geldig. |
| `button` | Een knop die een directe gebeurtenis activeert. Vereist een aangepast front-end model om de knoptekst en de handeling te definiëren. Zie `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` voor een voorbeeld. |
| `obscure` | Een tekstveld met de waarde gecodeerd en weergegeven als `**&#x200B;**` . Als u de tekst wijzigt met &#39;Element controleren&#39; in de browser, wordt de waarde niet weergegeven. |
| `password` | Net als bij `obscure` wordt de verborgen waarde niet gecodeerd en wordt de waarde zichtbaar wanneer u het type met &#39;Inspect Element&#39; in de browser forceert wijzigt. |
| `file` | Hiermee kan een bestand worden geüpload voor verwerking. |
| `label` | Hiermee geeft u een label weer in plaats van een bewerkbaar veld. Gebruik dit type wanneer een veld alleen binnen een bepaald bereik kan worden bewerkt, bijvoorbeeld alleen in de weergave Winkel. |
| `time` | Controle om tijd te plaatsen gebruikend drie dropdowns-Uur, minuut en seconde. |
| `allowspecific` | Een lijst met meerdere landen. `source_model` zoals `Magento\Shipping\Model\Config\Source\Allspecificcountries` vereist |
| `image` | Hiermee kunt u een afbeelding uploaden. |
| `note` | Hiermee kunt u een informatieve notitie aan de pagina toevoegen. Voor dit type is een `frontend_model` vereist om de notitie te renderen. |

Het is ook mogelijk een aangepast veldtype te maken. Dit wordt vaak gedaan wanneer een speciale knoop, met een actie, wordt vereist. Hiervoor zijn twee hoofdelementen nodig:

- Een blok maken in het gebied `adminhtml`
- De `type=""` instellen op het pad naar dit blok

Voor het blok zelf zijn ten minste een methode `__construct` en een methode `getElementHtml()` vereist. [&#x200B; Magento_OfflineShipping &#x200B;](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) is een eenvoudig voorbeeld van een douanetype.

In de module OfflineShipping bijvoorbeeld wordt de knop Exporteren gedefinieerd in `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` en ziet de velddefinitie er als volgt uit:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Referentie van veldknooppunt

Een `<field>` -tag kan de volgende onderliggende elementen hebben:

| Knooppunt | Beschrijving | Type |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Definieert het label dat in de voorzijde wordt weergegeven. | `string` |
| `comment` | Voegt een opmerking toe onder het veldlabel. Met `<![CDATA[//]]>` kunt u HTML toepassen. | `string` |
| `tooltip` | Een ander mogelijk frontend element dat kan worden gebruikt om de betekenis van dit gebied te beschrijven. Wordt weergegeven als een klein pictogram naast het veld. | `string` |
| `hint` | Geeft aanvullende informatie weer. Alleen beschikbaar bij specifieke `frontend_model` . | `string` |
| `frontend_class` | Voegt een gedefinieerde CSS-klasse toe aan het gerenderde HTML-element van de sectie. | `string` |
| `frontend_model` | Geeft een ander frontend model op om de rendering te wijzigen en de uitvoer te wijzigen. | `typeModel` |
| `backend_model` | Specificeert een verschillend achterste model om de gevormde waarden te wijzigen. | `typeModel` |
| `source_model` | Geeft een ander bronmodel op dat een specifieke reeks waarden biedt. | `typeModel` |
| `config_path` | Kan worden gebruikt om de generische config weg van een gebied te beschrijven. | `typeConfigPath` |
| `validate` | Verschillende validatieregels definiëren (ruimte gescheiden). De volledige referentielijst met beschikbare validatieregels wordt hieronder weergegeven. | `string` |
| `can_be_empty` | Wordt gebruikt wanneer `type` `multiselect` is om op te geven dat een veld leeg kan zijn. | `int` |
| `if_module_enabled` | Wordt alleen gebruikt om een veld weer te geven wanneer een bepaalde module is ingeschakeld. | `typeModule` |
| `base_url` | Wordt gebruikt in combinatie met `upload_dir` voor het uploaden van bestanden. | `typeUrl` |
| `upload_dir` | Geef een doelmap op voor uploads. Dit knooppunt heeft aanvullende kenmerken en knooppunten. Zoek ze op voordat je dit gebruikt. | `typeUploadDir` |
| `button_url` | Hiermee wordt een knop weergegeven als `button_url` en `button_label` zijn opgegeven. Gewoonlijk gebruikt in combinatie met een aangepast frontend model. | `typeUrl` |
| `button_label` | Hiermee wordt een knop weergegeven als `button_label` en `button_url` zijn opgegeven. Gewoonlijk gebruikt in combinatie met een aangepast frontend model. | `string` |
| `more_url` | Niet uitbreidbaar. Zie hieronder. | `typeUrl` |
| `demo_url` | Niet uitbreidbaar. Zie hieronder. | `typeUrl` |
| `hide_in_single_store_mode` | Of de groep op enige opslagwijze zichtbaar zou moeten zijn. `1` verbergt de groep; in `0` wordt de groep weergegeven. | `int` |
| `options` | Niet gebruikt. Mogelijk afgekeurd. | `complexType` |
| `depends` | Kan worden gebruikt om gebiedsdelen aan andere gebieden te verklaren. Wordt alleen gebruikt om specifieke velden/groepen weer te geven wanneer een bepaald veld de waarde `1` heeft. Dit knooppunt verwacht een `section/group/field` -string. | `complexType` |
| `attribute` | Aangepaste kenmerken kunnen worden gebruikt door frontend-modellen. Wordt meestal gebruikt om een bepaald frontend model dynamischer te maken. | `complexType` |
| `requires` | Niet uitbreidbaar. Zie hieronder. | `complexType` |

>[!WARNING]
>
>De knooppunten `more_url`, `demo_url`, `requires` en `options` worden gedefinieerd door een ander basisbetalingsmodel en worden slechts eenmaal gebruikt. Deze knooppunten kunnen niet opnieuw worden gebruikt.

### Voorbeeld: twee velden maken in een bepaalde groep

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

In het bovenstaande voorbeeld worden twee velden gemaakt, zowel in de standaardweergave als in de winkelweergave zichtbaar/configureerbaar. Beide velden hebben een opmerking en knopinfo waarin het doel voor de gebruiker wordt beschreven. Het knooppunt `label` is vertaalbaar.
Het veld met de id `ANOTHER_UNIQUE_FIELD_ID` is zichtbaar wanneer de opgegeven module in `if_module_enabled` algemeen is ingeschakeld. De waarde van het veld wordt ook gevalideerd op basis van de regels `required-entry` en `no-whitespace` .
Het veld met de id `A_UNIQUE_FIELD_ID` definieert een ander bronmodel dat de waarden `Yes` en `No` bevat.

### Gemeenschappelijke bronmodellen

De volgende bronmodellen worden geleverd door de Commerce 2 Core. Over het algemeen zijn er veel meer bronmodellen. In de volgende lijst worden de meest voorkomende modellen beschreven. Houd er rekening mee dat voor deze bronmodellen het veldkenmerk `type` moet worden ingesteld op `select` om correct te werken.

| Source-model | Beschrijving |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Geeft de waarden `Yes` , `No` en `Specified` op. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Geeft de waarden `Enable`, `Disable` . Hiermee slaat u de waarden op als `0` en `1` in de database. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Verstrekt de waarden `1 Hour`, `2 Hours`, `6 Hours`, `12 Hours` en `24 Hours`. Waarden worden opgeslagen als gehele getallen. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Geeft de waarden voor de tijdnotatie (12 uur/24 uur). |
| `Magento\Cron\Model\Config\Source\Frequency` | Geeft de waarden `Daily` , `Weekly` en `Monthly` op. Waarden worden in de database opgeslagen als `D` , `W` en `M` . |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Verstrekt de waarden voor een 2-lettercode van een bepaalde taal in het formaat ISO 639-1 (b.v. en). |
| `Magento\Config\Model\Config\Source\Locale` | Verstrekt de waarden gelijkend op bovengenoemde, maar heeft een scènecode (b.v. en_US). |

### Veldvalidatie

Aan een veld kunnen een of meer validatieklassen worden toegewezen om te controleren of de invoer van de gebruiker voldoet aan de vereisten voor de extensie. Validatieregels kunnen worden toegepast met de tag `<validate>` -Tag.
In het volgende voorbeeld wordt een veld gevalideerd en worden verschillende validatieregels toegevoegd.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

De volgende validatieregels zijn beschikbaar:

| Regel | Beschrijving |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Hiermee worden alleen letters, cijfers, spaties of onderstrepingstekens toegestaan. |
| `integer` | Hiermee wordt een positief of negatief getal zonder decimaal getal toegestaan. |
| `ipv4` | Staat een geldig IP v4 adres toe. |
| `ipv6` | Hiermee wordt een geldig IP v6-adres toegestaan. |
| `letters-only` | Hiermee worden alleen letters toegestaan. Bijvoorbeeld `abcABC` . |
| `letters-with-basic-punc` | Hiermee worden alleen letters of interpunctie toegestaan.<br> moet de volgende uitdrukking overgaan: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Hiermee wordt een (VK) mobiel telefoonnummer toegestaan. |
| `no-marginal-whitespace` | Hiermee worden witruimten aan het begin of einde van de waarde uitgeschakeld. |
| `no-whitespace` | Hiermee worden witruimten uitgeschakeld. |
| `phoneUK` | Staat een (VK) telefoonaantal toe. |
| `phoneUS` | Hiermee wordt een (Amerikaans) telefoonnummer toegestaan. |
| `required-entry` | Hiermee wordt een lege waarde uitgeschakeld (equivalente validatie als `validate-no-empty` ).<br> de mislukkingsbericht van de Bevestiging: &quot;Dit is een vereist gebied.&quot; |
| `time` | Staat een geldige tijd in 24-uurformaat, tussen 00 :00 en 23 :59 toe. Bijvoorbeeld `15` , `15:05` of `15:05:48` . |
| `time12h` | Staat een geldige tijd in formaat van 12 uur, tussen 12 :00 am en 11 :59: toe 59 pm. Bijvoorbeeld `3 am` , `11:30 pm` , `02:15:00 pm` . |
| `validate-admin-password` | Hiermee staat u 7 of meer tekens toe, zowel numeriek als alfabetisch. |
| `validate-alphanum-with-spaces` | Hiermee wordt het gebruik van letters (a-z of A-Z), getallen (0-9) of alleen spaties toegestaan. |
| `validate-clean-url` | Hiermee wordt een geldige URL toegestaan. Bijvoorbeeld `https://www.example.com` of `www.example.com` . |
| `validate-currency-dollar` | Hiermee wordt een geldig bedrag (in dollar) toegestaan. Bijvoorbeeld $100.00. |
| `validate-data` | Hiermee wordt het gebruik van letters (a-z of A-Z), getallen (0-9) of onderstrepingstekens (\_) alleen toegestaan.<br> het eerste karakter moet een brief zijn.<br> (Moet uitdrukking aanpassen: `/^[A-Za-z]+[A-Za-z0-9_]+$/`) <br> de mislukkingsbericht van de Bevestiging: &quot;Gelieve te gebruiken slechts brieven (a-z of A-Z), aantallen (0-9) of onderstrepingsteken (\_) op dit gebied, en het eerste karakter zou een brief moeten zijn.&quot; |
| `validate-date-au` | Hiermee wordt de volgende datumnotatie ingeschakeld: dd/mm/jjjj. Bijvoorbeeld 17/03/2006 voor 17 maart 2006. |
| `validate-email` | Hiermee wordt een geldig e-mailadres toegestaan. Bijvoorbeeld johndoe@domain.com. |
| `validate-emailSender` | Hiermee wordt een geldig e-mailadres toegestaan. Bijvoorbeeld johndoe@domain.com. |
| `validate-fax` | Hiermee wordt een geldig faxnummer toegestaan. Bijvoorbeeld 123-456-7890. |
| `validate-no-empty` | Hiermee wordt een lege waarde uitgeschakeld (equivalente validatie als `requried-entry` ).<br> de mislukkingsbericht van de Bevestiging: &quot;Lege waarde.&quot; |
| `validate-no-html-tags` | Hiermee wordt het gebruik van HTML-tags uitgeschakeld. |
| `validate-password` | Hiermee worden 6 of meer tekens toegestaan. Voorloopspaties en navolgende spaties worden genegeerd. |
| `validate-phoneLax` | Staat een geldig telefoonaantal toe. Bijvoorbeeld (123) 456-7890 of 123-456-7890. |
| `validate-phoneStrict` | Staat een geldig telefoonaantal toe. Bijvoorbeeld (123) 456-7890 of 123-456-7890. |
| `validate-select` | Hiermee wordt gedwongen dat de gekozen optie geen `null` -waarde, tekenreekswaarde `none` of tekenreekslengte 0 heeft. |
| `validate-ssn` | Hiermee wordt een geldig (US) socialezekerheidsnummer toegestaan. Bijvoorbeeld 123-45-6789. |
| `validate-street` | Hiermee wordt het gebruik van letters (a-z of A-Z), getallen (0-9), spaties en alleen &quot;#&quot; toegestaan. |
| `validate-url` | Hiermee wordt een geldige URL toegestaan. Protocol is vereist (http://, https:// of ftp://). |
| `validate-xml-identifier` | Hiermee wordt een geldige XML-id toegestaan. Bijvoorbeeld iets_1, block5, id-4. |
| `validate-zip-us` | Hiermee wordt een geldige postcode (US) toegestaan. Bijvoorbeeld 90602 of 90602-1234. |
| `vinUS` | Hiermee wordt de waarde van het voertuigidentificatienummer (VIN) in de VS toegestaan. |

### Standaardwaarden

U kunt standaardwaarden voor velden instellen in het `etc/config.xml` -bestand van de module door de standaardwaarde in het `section/group/field_ID` -knooppunt op te geven.

#### Voorbeeld: de standaardwaarde instellen voor `ANOTHER_UNIQUE_FIELD_ID` (standaardbereik)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Voorbeeld: de standaardwaarde instellen voor `ANOTHER_UNIQUE_FIELD_ID` (bereik website)

Geef met de tag `websites` de standaardwaarde voor een specifieke website op.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```

---
title: Aanbevolen procedures voor het op schaal distribueren van patches
description: Leer hoe gecentraliseerde patches voor Adobe Commerce u kunnen helpen bij het beheren van bedrijfsprojecten.
role: Developer
feature: Best Practices
badge: label="Bijgedragen door Anton Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Bijgedragen door Anton Evers"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Aanbevolen procedures voor het distribueren van Adobe Commerce-patches op schaal

Als u meerdere Adobe Commerce-installaties beheert, [patches](../../../upgrade/patches/apply.md) Dit kan een complex proces zijn. _Gecentraliseerde patches_ is een essentieel onderdeel van [algemene verwijzingsarchitectuur](../../architecture/global-reference/overview.md) en een goede praktijk voor ondernemingen. Hiermee kunt u de juiste patches toepassen op al uw Adobe Commerce-installaties. Dit onderwerp verklaart hoe te om gecentraliseerde patchdistributie voor alle types van Adobe Commerce te bereiken [patches](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>De volgende inhoud is oorspronkelijk gepubliceerd in het dialoogvenster [Adobe Commerce-patches op schaal distribueren](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) post op de Adobe Tech Blog. Het is gewijzigd om zich op de stappen en codesteekproeven voor het uitvoeren van een gecentraliseerde het patchen strategie te concentreren. Zie het originele artikel voor meer informatie over de verschillende typen patches die hier worden beschreven.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce in gebouwen

## Strategie

Hoe weet u, aangezien er veel verschillende typen patches zijn en er vele manieren zijn om deze toe te passen, welke patch als eerste wordt toegepast? Hoe meer patches u hebt, des te groter de kans dat ze op hetzelfde bestand of op dezelfde coderegel worden toegepast. Patches worden in de volgende volgorde toegepast:

1. **Beveiligingspatches** maakt deel uit van de statische codebasis van een Adobe Commerce-release.
1. **Composer-patches** doorheen `composer install` en `composer update` plug-ins zoals [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alles **vereiste patches** opgenomen in de [Cloud-patches voor handel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) pakket.
1. Geselecteerd **kwaliteitspatches** opgenomen in de [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Aangepaste patches** en Adobe Commerce Support-patches in het dialoogvenster `/m2-hotfixes` directory in alfabetische volgorde op flardnaam.

   >[!IMPORTANT]
   >
   >Hoe meer patches u toepast, hoe complexer de code wordt. De complexe code kan bevordering aan een nieuwe versie van de handel van de Adobe bemoeilijken en uw totale kosten van eigendom verhogen.

Als u verantwoordelijk bent voor het onderhoud van meerdere installaties van Adobe Commerce, kan het lastig zijn om ervoor te zorgen dat alle instanties dezelfde set geïnstalleerde patches hebben. Elke installatie heeft een eigen git-opslagplaats. `/m2-hotfixes` map, en `composer.json` bestand. De enige garantie die u hebt, is dat de **beveiligingspatches** en **vereiste patches** voor gebruikers in de cloud worden geïnstalleerd als onderdeel van uw belangrijkste Adobe Commerce-versie.

Momenteel is er geen enkele gecentraliseerde oplossing voor dit probleem, maar Composer biedt een manier om de kloof te dichten. De [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) pakket kunt u [patches toepassen vanuit afhankelijkheden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). U kunt een Composer-pakket maken waarin al uw patches worden geïnstalleerd en dat pakket vervolgens in al uw projecten wordt vereist.

Dat omvat **beveiligingspatches**, **vereiste patches**, en **Composer-patches**, maar hoe zit het met kwaliteitspatches en de inhoud van de `/m2-hotfixes` directory?

## Patches en hotfixes voor kwaliteit toepassen

U kunt kwaliteitspatches installeren op zowel cloudinfrastructuur als op locatie via de `vendor/bin/magento-patches apply` gebruiken. U moet ervoor zorgen dat de `vendor/bin/magento-patches apply` opdrachtuitvoering na `composer install` bewerkingen.

>[!NOTE]
>
>Op cloudinfrastructuur kunt u ook kwaliteitspatches installeren door deze weer te geven in de `.magento.env.yaml` bestand. Het hier beschreven voorbeeld vereist het gebruik van `vendor/bin/magento-patches apply` gebruiken.

U kunt opgeven welke patches moeten worden toegepast in het dialoogvenster `composer.json` bestand van een aangepast componentpakket Composer en vervolgens een insteekmodulepakket maken dat de opdracht uitvoert na `composer install` bewerkingen.

Om samen te vatten, vereist dit gecentraliseerde het patchen voorbeeld u om twee pakketten van de douanecomposer tot stand te brengen:

- **Componentpakket:** `centralized-patcher`

   - Definieert de lijst met kwaliteitspatches en `m2-hotfixes` installeren
   - Vereist de `centralized-patcher-composer-plugin` pakket, dat het `vendor/bin/magento-patches apply` opdracht after `composer install` bewerkingen

- **Plugin-pakket:** `centralized-patcher-composer-plugin`

   - Definieert een `CentralizedPatcher` PHP-klasse die de lijst met kwaliteitspatches leest vanuit de `centralized-patcher` package
   - Hiermee wordt het `vendor/bin/magento-patches apply` om de lijst met kwaliteitspatches na `composer install` bewerkingen

### `centralized-patcher`

U kunt een componentpakket maken (`centralized-patcher`) om alle kwaliteitspatches centraal te beheren en `/m2-hotfixes` in al uw Adobe Commerce-installaties.

Het componentpakket moet:

- Kopieer de inhoud van het dialoogvenster `/m2-hotfixes` in al uw installaties tijdens plaatsing.
- Definieer de lijst met kwaliteitspatches die u wilt installeren.
- Voer de `vendor/bin/magento-patches` om dezelfde lijst met kwaliteitspatches voor alle installaties te installeren (met de opdracht [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) insteekmodule als afhankelijkheid).

Als u de opdracht `centralized-patcher` componentpakket:

1. Een `composer.json` bestand met de volgende inhoud:

   >[!NOTE]
   >
   >De `require` kenmerk in het volgende voorbeeld toont een `require` afhankelijkheid van de [insteekmodule](#centralized-patcher-composer-plugin) die u later dit voorbeeld moet maken.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Een `/m2-hotfixes` directory in uw pakket en voeg het toe aan de `map` kenmerk in uw `composer.json` bestand. De `map` attribuut bevat dossiers om van dit pakket in de wortel van het doelproject te kopiëren dat u wilt herstellen.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >De `centralized-patcher` de inhoud van het pakket wordt gekopieerd `/m2-hotfixes` directory in m2-hotfixes folder van het doelproject op `composer install`.  Omdat de scripts voor cloudimplementatie m2-hotfixes toepassen na `composer install`, worden alle hotfixes geïnstalleerd door het plaatsingsmechanisme.

1. Definieer de kwaliteitspatches die u wilt installeren in het dialoogvenster `quality-patches` kenmerk.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


De `quality-patches` kenmerk in het voorgaande codevoorbeeld bevat twee patches van het [volledige patchlijst](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) als voorbeeld.  Deze kwaliteitspatches worden geïnstalleerd op elk project waarvoor de `centralized-patcher` pakket gebruiken met de `vendor/bin/magento-patches apply` gebruiken.

Voor testdoeleinden kunt u een voorbeeldpatch maken (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Plaats uw eigen pleisters in de `m2-hotfixes` samen met patches die u rechtstreeks van Adobe Commerce Support ontvangt.

Een voorbeeld van een patch-bestand (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Aangezien in dit voorbeeld de methode op locatie wordt gebruikt om kwaliteitspatches te installeren, moet u ervoor zorgen dat de optie `vendor/bin/magento-patches apply` opdrachtuitvoering na `composer install` bewerkingen. Deze insteekmodule wordt geactiveerd na `composer install` bewerkingen, die de `vendor/bin/magento-patches apply` gebruiken.

Als u de opdracht `centralized-patcher-compose-plugin` componentpakket:

1. Een `composer.json` bestand met de volgende inhoud:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Een PHP-bestand maken en een `CentralizedPatcher` klasse voor het lezen van de lijst met kwaliteitspatches in het menu [`centralized-patcher`](#centralized-patcher) componentpakket en installeer ze onmiddellijk na elke `composer install` -bewerking.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Zie de [codevoorbeelden](#code-examples) om de twee pakketten die in dit voorbeeld worden beschreven in actie te zien.


## Wat u moet doen met projectspecifieke patches

U kunt een scenario hebben waar slechts 95% van de flarden in alle projecten worden vereist, terwijl een paar flarden slechts op een specifiek geval van toepassing zijn. De normale manier om het aanbrengen van patches toe te passen werkt nog steeds. U kunt projectspecifieke flarden in houden `/m2-hotfixes` map en installeer kwaliteitspatches per project.

Als u deze aanpak gebruikt, **niet** patches toewijzen in het dialoogvenster `/m2-hotfixes` directory die door de `centralized-patcher` componentpakket. U kunt per ongeluk gemaakte afspraken voorkomen door `/m2-hotfixes` aan uw `.gitignore` bestand. Na het bijwerken van de `.gitignore` bestand, vergeet niet dat een projectspecifiek bestand `/m2-hotfixes` moet worden toegevoegd met de `git add –force` gebruiken.

## Verschillende Adobe Commerce-versies uitvoeren

Zorg ervoor dat u het juiste gebiedsdeel in plaatst `centralized-patcher` componentpakket. U hebt bijvoorbeeld Adobe Commerce 2.4.5-p2 nodig voor een specifieke versie van uw pakket, dat alleen patches bevat die compatibel zijn met Adobe Commerce 2.4.5-p2. U hebt mogelijk een andere versie van dit pakket die compatibel is met Adobe Commerce 2.4.4.

## Het resultaat begrijpen

Net als bij Adobe Commerce op cloudinfrastructuur wordt in dit artikel ervan uitgegaan dat uw implementatieproces de `composer install` en niet `composer update` of `git pull` om nieuwe code aan uw servers op te stellen. De stroom van gecentraliseerde flardinstallatie zal dan als volgt kijken:

1. Composer installeren

   - Hiermee installeert u Adobe Commerce, inclusief -p1- of -p2-beveiligingspatches en functionele patches
   - Combineert gecentraliseerd `/m2-hotfixes` en ondersteunt patches met projectspecifieke `/m2-hotfixes` en supportpatches
   - Hiermee past u patches toe die met de `cweagans/composer-patches` Composer-pakket

1. Na `composer install`

   - Met de plug-in Composer installeert u gecentraliseerde kwaliteitspatches

1. Implementatie

   - Vereiste patches en projectspecifieke kwaliteitspatches worden geïnstalleerd op basis van de `.magento.env.yaml` bestand (alleen Adobe Commerce voor cloud-infrastructuurprojecten).
   - Aangepaste patches en supportpatches vanuit de `/m2-hotfixes` worden geïnstalleerd in alfabetische volgorde op flardnaam.

Op deze manier kunt u al uw patches centraal beheren voor al uw installaties en kunt u de veiligheid en stabiliteit van uw Adobe Commerce-winkels beter garanderen. Gebruik de volgende methoden om de patchstatus te controleren:

- [Cloud-infrastructuurprojecten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Projecten ter plaatse](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Codevoorbeelden

- [Gecentraliseerde patches in Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Gecentraliseerde patches in Adobe Commerce op cloudinfrastructuur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Gecentraliseerde plug-in voor patchercomposer](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Gecentraliseerde patchercomponent](https://github.com/AntonEvers/centralized-patcher)

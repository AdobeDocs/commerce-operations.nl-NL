---
title: Aanbevolen procedures voor het op schaal distribueren van patches
description: Leer hoe gecentraliseerde patches voor Adobe Commerce u kunnen helpen bij het beheren van bedrijfsprojecten.
role: Developer
feature: Best Practices
badge: label="Bijgedragen door Tony Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="Bijgedragen door Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Aanbevolen procedures voor het distribueren van Adobe Commerce-patches op schaal

Als u veelvoudige installaties van Adobe Commerce beheert, [ het patchen ](../../../upgrade/patches/apply.md) kan een complex proces zijn. _Gecentraliseerde het opsluiten_ is beste praktijken voor ondernemingen. Hiermee kunt u de juiste patches toepassen op al uw Adobe Commerce-installaties. Dit onderwerp verklaart hoe te om gecentraliseerde flarddistributie voor alle types van de flarden van Adobe Commerce [ te bereiken ](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>De volgende inhoud werd oorspronkelijk gepubliceerd in [ het Verdelen van de Patches van Adobe Commerce bij de post van de Schaal ](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) op het Blog van Tech van de Adobe. Het is gewijzigd om zich op de stappen en codesteekproeven voor het uitvoeren van een gecentraliseerde het patchen strategie te concentreren. Zie het originele artikel voor meer informatie over de verschillende typen patches die hier worden beschreven.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce in gebouwen

## Strategie

Hoe weet u, aangezien er veel verschillende typen patches zijn en er vele manieren zijn om deze toe te passen, welke patch als eerste wordt toegepast? Hoe meer patches u hebt, des te groter de kans dat ze op hetzelfde bestand of op dezelfde coderegel worden toegepast. Patches worden in de volgende volgorde toegepast:

1. **de flarden van de Veiligheid** maken deel uit van de statische codebasis van een versie van Adobe Commerce.
1. **de flarden van Composer** door `composer install` en `composer update` stoppen zoals [ cweagans/composer-flarden ](https://packagist.org/packages/cweagans/composer-patches).
1. Alle **vereiste flarden** inbegrepen in het [ Reparaties van de Wolk voor Commerce ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html?lang=nl-NL) pakket.
1. Geselecteerde **kwaliteitspatches** inbegrepen in [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md).
1. **de flarden van de Douane** en de flarden van de Steun van Adobe Commerce in de `/m2-hotfixes` folder in alfabetische orde door flardnaam.

   >[!IMPORTANT]
   >
   >Hoe meer patches u toepast, hoe complexer de code wordt. De complexe code kan bevordering aan een nieuwe versie van de handel van de Adobe bemoeilijken en uw totale kosten van eigendom verhogen.

Als u verantwoordelijk bent voor het onderhoud van meerdere installaties van Adobe Commerce, kan het lastig zijn om ervoor te zorgen dat alle instanties dezelfde set geïnstalleerde patches hebben. Elke installatie heeft een eigen git-opslagplaats, `/m2-hotfixes` map en `composer.json` bestand. De enige garantie dat u hebt is dat de **veiligheidspatches** en **vereiste flarden** voor wolkengebruikers allen als deel van uw belangrijkste versie van Adobe Commerce geïnstalleerd zijn.

Momenteel is er geen enkele gecentraliseerde oplossing voor dit probleem, maar Composer biedt een manier om de kloof te dichten. Het [`cweagans/composer-patches` ](https://packagist.org/packages/cweagans/composer-patches) pakket staat u toe om [ flarden van gebiedsdelen ](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies) toe te passen. U kunt een Composer-pakket maken waarin al uw patches worden geïnstalleerd en dat pakket vervolgens in al uw projecten wordt vereist.

Dat behandelt **veiligheidspatches**, **vereiste flarden**, en **de flarden van Composer**, maar wat over kwaliteitsflarden en de inhoud van de `/m2-hotfixes` folder?

## Patches en hotfixes voor kwaliteit toepassen

Met de opdracht `vendor/bin/magento-patches apply` kunt u kwaliteitspatches installeren op zowel cloudinfrastructuur als op locatie. U moet ervoor zorgen dat de opdracht `vendor/bin/magento-patches apply` wordt uitgevoerd na `composer install` -bewerkingen.

>[!NOTE]
>
>Op cloudinfrastructuur kunt u ook kwaliteitspatches installeren door deze weer te geven in het `.magento.env.yaml` -bestand van uw project. Het hier beschreven voorbeeld vereist het gebruik van de opdracht `vendor/bin/magento-patches apply` .

U kunt opgeven welke patches moeten worden toegepast in het `composer.json` -bestand van een aangepast componentpakket Composer en vervolgens een insteekmodulepakket maken dat de opdracht uitvoert na `composer install` -bewerkingen.

Om samen te vatten, vereist dit gecentraliseerde het patchen voorbeeld u om twee pakketten van de douanecomposer tot stand te brengen:

- **het pakket van de Component:** `centralized-patcher`

   - Definieert de lijst met kwaliteitspatches en `m2-hotfixes` die moeten worden geïnstalleerd
   - Vereist het pakket `centralized-patcher-composer-plugin` dat de `vendor/bin/magento-patches apply` command after `composer install` -bewerkingen uitvoert

- **pakket van de Insteekmodule:** `centralized-patcher-composer-plugin`

   - Definieert een PHP-klasse van `CentralizedPatcher` die de lijst met kwaliteitspatches in het `centralized-patcher` -pakket leest
   - Voert de opdracht `vendor/bin/magento-patches apply` uit om de lijst met kwaliteitspatches te installeren na `composer install` -bewerkingen

### `centralized-patcher`

U kunt een componentenpakket van Composer (`centralized-patcher`) tot stand brengen om alle kwaliteitsflarden en `/m2-hotfixes` over al uw installaties van Adobe Commerce centraal te beheren.

Het componentpakket moet:

- Kopieer de inhoud van de map `/m2-hotfixes` naar al uw installaties tijdens de implementatie.
- Definieer de lijst met kwaliteitspatches die u wilt installeren.
- Voer de opdracht `vendor/bin/magento-patches` uit om dezelfde lijst met kwaliteitspatches voor alle installaties te installeren (met het [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) -insteekpakket als een afhankelijkheid).

Het componentpakket `centralized-patcher` maken:

1. Maak een `composer.json` -bestand met de volgende inhoud:

   >[!NOTE]
   >
   >Het `require` attribuut in het volgende voorbeeld toont a `require` gebiedsdeel op het [ plugin pakket ](#centralized-patcher-composer-plugin) dat u later dit voorbeeld moet tot stand brengen.

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

1. Maak een map `/m2-hotfixes` in het pakket en voeg deze toe aan het kenmerk `map` in het bestand `composer.json` . Het kenmerk `map` bevat bestanden die u vanuit dit pakket wilt kopiëren naar de hoofdmap van het doelproject dat u wilt repareren.

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
   >Het pakket `centralized-patcher` kopieert de inhoud van de map `/m2-hotfixes` naar de map m2-hotfixes van het doelproject op `composer install` .  Aangezien de scripts voor cloudimplementatie m2-hotfixes toepassen na `composer install`, worden alle hotfixes geïnstalleerd door het implementatiemechanisme.

1. Definieer de kwaliteitspatches die in het kenmerk `quality-patches` moeten worden geïnstalleerd.

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


Het `quality-patches` attribuut in de voorafgaande codesteekproef bevat twee flarden van de [ volledige flardlijst ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) als voorbeeld.  Deze kwaliteitspatches worden geïnstalleerd op elk project waarvoor het `centralized-patcher` -pakket is vereist met de opdracht `vendor/bin/magento-patches apply` .

Voor testdoeleinden kunt u een voorbeeldflard (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`) tot stand brengen.

>[!NOTE]
>
>Plaats uw eigen patches in de map `m2-hotfixes` samen met patches die u rechtstreeks van Adobe Commerce Support ontvangt.

Een voorbeeld flarddossier (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

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

Aangezien in dit voorbeeld de methode op locatie wordt gebruikt om kwaliteitspatches te installeren, moet u ervoor zorgen dat de opdracht `vendor/bin/magento-patches apply` wordt uitgevoerd na `composer install` -bewerkingen. Deze insteekmodule wordt geactiveerd na `composer install` -bewerkingen, die de opdracht `vendor/bin/magento-patches apply` uitvoert.

Het componentpakket `centralized-patcher-compose-plugin` maken:

1. Maak een `composer.json` -bestand met de volgende inhoud:

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

1. Maak een PHP-bestand en definieer een `CentralizedPatcher` -klasse voor het lezen van de lijst met kwaliteitspatches in het [`centralized-patcher`](#centralized-patcher) -componentpakket en installeer deze direct na elke `composer install` -bewerking.

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
>Verwijs naar [ code-voorbeelden ](#code-examples) om de twee pakketten te zien die in dit voorbeeld in actie worden beschreven.


## Wat u moet doen met projectspecifieke patches

U kunt een scenario hebben waar slechts 95% van de flarden in alle projecten worden vereist, terwijl een paar flarden slechts op een specifiek geval van toepassing zijn. De normale manier om het aanbrengen van patches toe te passen werkt nog steeds. U kunt projectspecifieke patches in de map `/m2-hotfixes` bewaren en kwaliteitspatches per project installeren.

Als u deze benadering gebruikt, **&#x200B;**&#x200B;begaat geen flarden in de `/m2-hotfixes` folder die in uw project door het `centralized-patcher` componentenpakket zijn gekopieerd. U kunt per ongeluk vastgelegde gegevens voorkomen door `/m2-hotfixes` aan het `.gitignore` -bestand toe te voegen. Nadat u het `.gitignore` -bestand hebt bijgewerkt, moet u niet vergeten dat projectspecifieke `/m2-hotfixes` moet worden toegevoegd met de opdracht `git add –force` .

## Verschillende Adobe Commerce-versies uitvoeren

Controleer of u de juiste afhankelijkheid instelt in het componentpakket `centralized-patcher` . U hebt bijvoorbeeld Adobe Commerce 2.4.5-p2 nodig voor een specifieke versie van uw pakket, dat alleen patches bevat die compatibel zijn met Adobe Commerce 2.4.5-p2. U hebt mogelijk een andere versie van dit pakket die compatibel is met Adobe Commerce 2.4.4.

## Het resultaat begrijpen

Net als bij Adobe Commerce op cloudinfrastructuur wordt in dit artikel ervan uitgegaan dat uw implementatieproces de opdracht `composer install` gebruikt en niet `composer update` of `git pull` om nieuwe code op uw servers te implementeren. De stroom van gecentraliseerde flardinstallatie zal dan als volgt kijken:

1. Composer installeren

   - Hiermee installeert u Adobe Commerce, inclusief -p1- of -p2-beveiligingspatches en functionele patches
   - Combineert gecentraliseerde `/m2-hotfixes` -patches en ondersteunt patches met projectspecifieke `/m2-hotfixes` -patches
   - Hiermee worden alle patches toegepast die met het Composer-pakket `cweagans/composer-patches` zijn geïnstalleerd

1. Na `composer install`

   - Met de plug-in Composer installeert u gecentraliseerde kwaliteitspatches

1. Implementatie

   - Vereiste patches en projectspecifieke kwaliteitspatches worden geïnstalleerd op basis van het `.magento.env.yaml` -bestand (alleen Adobe Commerce voor cloudinfrastructuurprojecten).
   - Aangepaste patches en ondersteuningspatches uit de map `/m2-hotfixes` worden in alfabetische volgorde op patchnaam geïnstalleerd.

Op deze manier kunt u al uw patches centraal beheren voor al uw installaties en kunt u de veiligheid en stabiliteit van uw Adobe Commerce-winkels beter garanderen. Gebruik de volgende methoden om de patchstatus te controleren:

- [ de infrastructuurprojecten van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL#view-available-patches-and-status)
- [Projecten ter plaatse](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Codevoorbeelden

- [ Gecentraliseerde flarden in Magento Open Source ](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [ Gecentraliseerde flarden in Adobe Commerce op wolkeninfrastructuur ](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [ Gecentraliseerde de stop van de Composer van de patcher ](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [ Gecentraliseerde patchercomponent ](https://github.com/AntonEvers/centralized-patcher)

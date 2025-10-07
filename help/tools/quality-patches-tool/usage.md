---
title: Gebruik
description: Leer hoe u patches voor Adobe Commerce toepast en beheert met het gereedschap Kwaliteitspatches. Testen, toepassingen en patchbeheertechnieken ontdekken.
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Gebruik

[[!DNL Quality Patches Tool] &#x200B;](https://github.com/magento/quality-patches) levert individuele die flarden door Adobe en de gemeenschap van Magento Open Source worden ontwikkeld. Hiermee kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven. U kunt patches toepassen op Adobe Commerce-projecten, ongeacht wie de patch heeft ontwikkeld. U kunt bijvoorbeeld een patch toepassen die door de gemeenschap is ontwikkeld op Adobe Commerce-projecten.

Bekijk deze [&#x200B; technische video &#x200B;](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=nl-NL) en leer hoe te om het Hulpmiddel van de Patches van de Kwaliteit voor Adobe Commerce te gebruiken.

>[!INFO]
>
>Zie [&#x200B; individuele flarden &#x200B;](#apply-individual-patches) voor instructies op het toepassen van flarden op uw projecten van Adobe Commerce toepassen. Zie [[!DNL Quality Patches Tool]: Zoeken naar patches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) voor een volledige lijst met vrijgegeven patches.

>[!WARNING]
>
>Het wordt afgeraden de [!DNL Quality Patches Tool] te gebruiken om grote aantallen patches toe te passen, omdat hierdoor de code complexer wordt en de upgrade naar een nieuwe versie moeilijker wordt.

## Installeren

>[!INFO]
>
>Als het niet reeds geïnstalleerd is, moet u [[!DNL Git] installeren &#x200B;](https://github.com/git-guides/install-git) of [&#x200B; Reparatie &#x200B;](https://man7.org/linux/man-pages/man1/patch.1.html) alvorens [!DNL Quality Patches Tool] te installeren. Voeg het `magento/quality-patches` Composer-pakket toe aan uw `composer.json` -bestand:

```bash
composer require magento/quality-patches
```

## Afzonderlijke patches weergeven

U kunt als volgt de lijst met afzonderlijke patches voor uw versie van Adobe Commerce weergeven:

```bash
./vendor/bin/magento-patches status
```

De uitvoer ziet er ongeveer als volgt uit:

| Id | Titel | Type | Status | Details |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC wordt uitgeschakeld tijdens implementaties | Optioneel | Niet toegepast | Betrokken componenten:<br> - magento/module-page-cache |
| MCLOUD-5650 | Implementatieconfiguratie bewaren na lezen van bestand | Optioneel | Niet toegepast | Betrokken componenten:<br> - magento/framework |
| MCLOUD-5684 | Paginering werkt niet - product_list_limit=all | Optioneel | Niet toegepast | Betrokken componenten: - magento/module-elasticsearch |
| MCLOUD-5837 | Probleem met taakverdelingsmechanisme verhelpen | Vervangen | Toegepast | Aanbevolen vervanging: MC-1 <br> Betrokken componenten: - magento/framework |
| BUNDLE-2554 | Fout in betalingsgegevens instellen | Optioneel | Niet toegepast | Betrokken componenten: <br>- amzn/amazon-pay-module |
| MC-1 | Opgeloste problemen 1 | Optioneel | Toegepast | Betrokken componenten: <br> - magento/module-cms |
| MC-2 | Opgeloste problemen 2 | Optioneel | Niet toegepast | Betrokken componenten: <br> - magento/module-cms |
| MC-3 | Opgeloste problemen 3 | Optioneel | Niet toegepast | Vereiste flarden:<br> - mc-2 <br> Betrokken componenten: <br> - magento/module-cms |
| MC-3-V2 | Bijgewerkte oplossing voor probleem 3; vervangt MC-3-patch | Optioneel | NVT | Betrokken componenten: <br> magento/module-cms |

Adobe Commerce 2.3.5.

De statustabel bevat:

- **Type**:
   - `Optional` — Alle flarden van [!DNL Quality Patches Tool] en [&#x200B; Commerce op de Gids van de Infrastructuur van de Wolk > passen flarden &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) pakket toe zijn facultatief voor de installaties van Adobe Commerce.
   - `Deprecated` — Adobe heeft de afzonderlijke patch vervangen. Als u de pleister hebt aangebracht, raden wij u aan deze weer in te voeren. De herstelbewerking verwijdert de patch ook uit de statustabel.

- **Status**:
   - `Applied` — De patch is toegepast.
   - `Not applied` — De patch is niet toegepast.
   - `N/A` — De status van de patch kan niet worden gedefinieerd vanwege conflicten.

- **Details**:
   - `Affected components` — De lijst met betrokken modules.
   - `Required patches` — De lijst met patches die moeten worden toegepast om een aangegeven patch correct te laten werken (afhankelijkheden).
   - `Recommended replacement` — De patch die een aanbevolen vervanging voor een vervangen patch is.

>[!INFO]
>
>Nadat u de upgrade naar een nieuwe versie van Adobe Commerce hebt uitgevoerd, moet u de patches opnieuw toepassen als de patches niet in de nieuwe versie zijn opgenomen. Zie [&#x200B; passen flarden na een verbetering &#x200B;](#re-apply-patches-after-an-upgrade) opnieuw toe.

## Afzonderlijke patches toepassen {#apply-individual-patches}

>[!WARNING]
>
>Het is aan te raden om alle patches in een testomgeving of ontwikkelomgeving te testen voordat ze worden geïmplementeerd. Het wordt ook aanbevolen een back-up van uw gegevens te maken voordat u een patch toepast. Zie [&#x200B; Steun en terugdraaiend het dossiersysteem, media, en gegevensbestand &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html?lang=nl-NL).

Als u één patch wilt toepassen, voert u de volgende opdracht uit, waarbij `MAGETWO-XXXX` de patch-id is die in de statustabel is opgegeven:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

U kunt ook meerdere patches tegelijk toepassen door elke extra patch-id te scheiden met een spatie:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

U moet de cache wissen nadat u patches hebt toegepast om de wijzigingen in de Adobe Commerce-toepassing te kunnen zien:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Bewaar een lijst met toegepaste patches op een aparte locatie. Mogelijk moet u een aantal van deze programma&#39;s opnieuw toepassen nadat u een upgrade hebt uitgevoerd naar een nieuwe versie van Adobe Commerce. Zie [&#x200B; passen flarden na een verbetering &#x200B;](#re-apply-patches-after-an-upgrade) opnieuw toe.

## Afzonderlijke patches herstellen

>[!WARNING]
>
>Het is aan te raden om alle patches in een testomgeving of ontwikkelomgeving te testen voordat ze worden geïmplementeerd. Het wordt ook aanbevolen een back-up van uw gegevens te maken voordat u een patch toepast. Zie [&#x200B; Steun en terugdraaiend het dossiersysteem, media, en gegevensbestand &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html?lang=nl-NL).

Als u één patch wilt herstellen, voert u de volgende opdracht uit, waarbij `MAGETWO-XXXX` de patch-id is die in de statustabel is opgegeven:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

U kunt ook meerdere patches tegelijk herstellen door elke extra patch-id te scheiden met een spatie:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Alle toegepaste patches herstellen:

```bash
./vendor/bin/magento-patches revert --all
```

U moet de cache wissen nadat u de patches hebt teruggedraaid om de wijzigingen in de Adobe Commerce-toepassing te kunnen zien:

```bash
./bin/magento cache:clean
```

## Updates ophalen

Adobe Commerce brengt regelmatig nieuwe afzonderlijke patches uit. U moet de [!DNL Quality Patches Tool] bijwerken voor nieuwe afzonderlijke patches:

```bash
composer update magento/quality-patches
```

De toegevoegde patches weergeven:

>[!TIP]
>
>Nieuwe patches toevoegen worden onder aan de tabel weergegeven.

```bash
./vendor/bin/magento-patches status
```

## Patches opnieuw toepassen na een upgrade {#re-apply-patches-after-an-upgrade}

Wanneer u een upgrade uitvoert naar een nieuwe versie van Adobe Commerce, moet u de patches opnieuw toepassen als de patches niet in de nieuwe versie zijn opgenomen.

Patches opnieuw toepassen:

1. Werk [!DNL Quality Patches Tool] bij:

   ```bash
   composer update magento/quality-patches.
   ```

1. Open de lijst van eerder toegepaste flarden, die in [&#x200B; werd geadviseerd individuele flarden &#x200B;](#apply-individual-patches) toepassen.

1. Pas de pleisters toe:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   De beste manier is om patches één voor één toe te passen.

1. De cache reinigen:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Wanneer u de opdracht `status` uitvoert, worden de patches die in de nieuwe versie zijn opgenomen, niet meer weergegeven in de tabel met beschikbare patches.

## Logboekregistratie

In [!DNL Quality Patches Tool] worden alle bewerkingen in het `<Magento_root>/var/log/patch.log` -bestand geregistreerd.

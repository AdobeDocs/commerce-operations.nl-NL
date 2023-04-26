---
title: Gebruik
description: Leer hoe u de [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Gebruik

De [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) levert afzonderlijke patches die door Adobe en de Magento Open Source-gemeenschap zijn ontwikkeld. Hiermee kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce of Magento Open Source, toepassen, herstellen en weergeven. U kunt patches toepassen op Adobe Commerce- en Magento Open Source-projecten, ongeacht wie de patch heeft ontwikkeld. U kunt bijvoorbeeld een patch toepassen die door de gemeenschap is ontwikkeld op Adobe Commerce-projecten.


Dit bekijken [technische video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) en leer hoe u het gereedschap Kwaliteitspatches kunt gebruiken voor Adobe Commerce en Magento Open Source.

>[!INFO]
>
>Zie [Afzonderlijke patches toepassen](#apply-individual-patches) voor instructies voor het toepassen van patches op uw Adobe Commerce- of Magento Open Source-projecten. Zie [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) om een volledige lijst met vrijgegeven patches te bekijken.

>[!WARNING]
>
>Het wordt niet aanbevolen om de [!DNL Quality Patches Tool] om grote aantallen patches toe te passen, omdat hierdoor de code complexer wordt en de upgrade naar een nieuwe versie moeilijker wordt.

## Installeren

>[!INFO]
>
>Als dit nog niet het geval is, moet u de installatie [[!DNL Git]](https://github.com/git-guides/install-git) of [Reparatie](https://man7.org/linux/man-pages/man1/patch.1.html) voordat u de [!DNL Quality Patches Tool]. Voeg de `magento/quality-patches` Composer-pakket naar uw `composer.json` bestand:

```bash
composer require magento/quality-patches
```

## Afzonderlijke patches weergeven

U kunt als volgt de lijst met afzonderlijke patches weergeven die beschikbaar zijn voor uw versie van Adobe Commerce of Magento Open Source:

```bash
./vendor/bin/magento-patches status
```

De uitvoer ziet er ongeveer als volgt uit:

| Id | Titel | Type | Status | Details |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC wordt uitgeschakeld tijdens implementaties | Optioneel | Niet toegepast | Betrokken onderdelen:<br> - magento/module-page-cache |
| MCLOUD-5650 | Implementatieconfiguratie bewaren na lezen van bestand | Optioneel | Niet toegepast | Betrokken onderdelen:<br> - magento/framework |
| MCLOUD-5684 | Paginering werkt niet - product_list_limit=all | Optioneel | Niet toegepast | Betrokken onderdelen: - magento/module-elasticsearch |
| MCLOUD-5837 | Probleem met taakverdelingsmechanisme verhelpen | Vervangen | Toegepast | Aanbevolen vervanging: MC-1 <br> Betrokken onderdelen: - magento/framework |
| BUNDLE-2554 | Fout in betalingsgegevens instellen | Optioneel | Niet toegepast | Betrokken onderdelen: <br>- amzn/amazon-pay-module |
| MC-1 | Opgeloste problemen 1 | Optioneel | Toegepast | Betrokken onderdelen: <br> - magento/module-cms |
| MC-2 | Opgeloste problemen 2 | Optioneel | Niet toegepast | Betrokken onderdelen: <br> - magento/module-cms |
| MC-3 | Opgeloste problemen 3 | Optioneel | Niet toegepast | Vereiste patches:<br> - MC-2 <br>Betrokken onderdelen: <br>- magento/module-cms |
| MC-3-V2 | Bijgewerkte oplossing voor probleem 3; vervangt MC-3-patch | Optioneel | N.v.t. | Betrokken onderdelen:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

De statustabel bevat:

- **Type**:
   - `Optional` — Alle patches van de [!DNL Quality Patches Tool] en de [Commerce on Cloud Infrastructure Guide > Patches toepassen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) -pakket is optioneel voor Adobe Commerce- en Magento Open Source-installaties.
   - `Deprecated` - Adobe heeft de afzonderlijke pleister vervangen. Als u de pleister hebt aangebracht, raden wij u aan deze weer in te voeren. De herstelbewerking verwijdert de patch ook uit de statustabel.

- **Status**:
   - `Applied` — De pleister is aangebracht.
   - `Not applied` — De pleister is niet aangebracht.
   - `N/A` — De status van de patch kan niet worden gedefinieerd vanwege conflicten.

- **Details**:
   - `Affected components` — De lijst van betrokken modules.
   - `Required patches` — De lijst van flarden die voor een aangewezen flard moeten worden toegepast behoorlijk (gebiedsdelen) te werken.
   - `Recommended replacement` — De pleister die een aanbevolen vervanging voor een vervangen pleister is.

>[!INFO]
>
>Nadat u een upgrade hebt uitgevoerd naar een nieuwe versie van Adobe Commerce of Magento Open Source, moet u de patches opnieuw toepassen als de patches niet in de nieuwe versie zijn opgenomen. Zie [Patches opnieuw toepassen na een upgrade](#re-apply-patches-after-an-upgrade).

## Afzonderlijke patches toepassen {#apply-individual-patches}

>[!WARNING]
>
>Het is aan te raden om alle patches in een testomgeving of ontwikkelomgeving te testen voordat ze worden geïmplementeerd. Het wordt ook aanbevolen een back-up van uw gegevens te maken voordat u een patch toepast. Zie [Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Als u één patch wilt toepassen, voert u de volgende opdracht uit, waarbij `MAGETWO-XXXX` is de patch-id die is opgegeven in de statustabel:

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
>Bewaar een lijst met toegepaste patches op een aparte locatie. Mogelijk moet u een aantal van deze toepassingen opnieuw toepassen nadat u een upgrade hebt uitgevoerd naar een nieuwe versie van Adobe Commerce of Magento Open Source. Zie [Patches opnieuw toepassen na een upgrade](#re-apply-patches-after-an-upgrade).

## Afzonderlijke patches herstellen

>[!WARNING]
>
>Het is aan te raden om alle patches in een testomgeving of ontwikkelomgeving te testen voordat ze worden geïmplementeerd. Het wordt ook aanbevolen een back-up van uw gegevens te maken voordat u een patch toepast. Zie [Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Om één enkel flard terug te keren, stel het volgende bevel in werking waar `MAGETWO-XXXX` is de patch-id die is opgegeven in de statustabel:

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

Adobe Commerce brengt regelmatig nieuwe afzonderlijke patches uit. U moet de [!DNL Quality Patches Tool] voor nieuwe afzonderlijke patches:

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

Wanneer u een upgrade uitvoert naar een nieuwe versie van Adobe Commerce of Magento Open Source, moet u de patches opnieuw toepassen als de patches niet in de nieuwe versie zijn opgenomen.

Patches opnieuw toepassen:

1. Werk de [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Open de lijst met eerder toegepaste pleisters, die werd aanbevolen in [Afzonderlijke patches toepassen](#apply-individual-patches).

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
   >Wanneer u de `status` , worden de patches die in de nieuwe versie waren opgenomen niet meer weergegeven in de tabel met beschikbare patches.

## Logboekregistratie

De [!DNL Quality Patches Tool] Hiermee worden alle bewerkingen in het dialoogvenster `<Magento_root>/var/log/patch.log` bestand.

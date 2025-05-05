---
title: Hoe reparaties werken
description: Leer meer over de verschillende typen patches voor Adobe Commerce en hoe ze werken.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Hoe patches werken

>[!WARNING]
>
>We raden u ten zeerste aan alle patches in een testomgeving of ontwikkelomgeving te testen voordat u de patches gaat implementeren in productie. We raden u ook aan een back-up van uw gegevens te maken voordat u een patch toepast. Zie [ file en rol terug het dossiersysteem ](../../installation/tutorials/backup.md).

Patch-bestanden (of diff-bestanden) zijn tekstbestanden met de volgende notatie:

- De bestanden die moeten worden gewijzigd.
- Het regelnummer waarmee de wijziging moet beginnen en het aantal regels dat moet worden gewijzigd.
- De nieuwe code die moet worden omgewisseld.

Wanneer het patchprogramma wordt uitgevoerd, wordt dit bestand ingelezen en worden de opgegeven wijzigingen aangebracht in het bestand of de bestanden.

Er zijn drie typen patches:

- **Hotfixes** - de flarden die de Adobe op het [ Centrum van de Veiligheid ](https://magento.com/security/patches) publiceert.
- **Individuele flarden** - de flarden die de Steun van Adobe Commerce leidt en op een individuele basis verdeelt.
- **de flarden van de Douane** - de Unofficiale flarden die u van een it kunt tot stand brengen begaat.

## Hotfixes

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties bevatten die vele verkopers beïnvloeden. Deze correcties worden toegepast op de volgende patchrelease voor de toepasselijke secundaire versie. De Adobe geeft hotfixes terug zoals nodig.

U kunt hotfixes in het [ Centrum van de Veiligheid ](https://magento.com/security/patches) vinden. Volg de instructies op de pagina om het patchbestand te downloaden, afhankelijk van uw versie en installatietype. Gebruik de [ bevellijn ](../patches/apply.md#) of [ Composer ](../patches/apply.md) om hete fixflarden toe te passen.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Afzonderlijke patches

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de meest recente ondersteunde secundaire versie (bijvoorbeeld 2.4.x), maar kunnen ontbreken in de vorige ondersteunde secundaire versie (bijvoorbeeld 2.3.x). Adobe geeft individuele pleisters vrij waar nodig.

Gebruik [[!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}  om individuele flarden toe te passen.

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaartse incompatibele wijzigingen.

## Aangepaste patches

Soms duurt het even voor het Team van de Techniek van de Adobe om een insectenmoeilijke situatie te omvatten die op GitHub in een versie van de Composer van Adobe Commerce wordt gemaakt. Ondertussen, kunt u een flard van GitHub tot stand brengen en de [`cweagans/composer-patches` ](https://github.com/cweagans/composer-patches/) stop gebruiken om het op uw op composer-Gebaseerde installatie toe te passen.

Gebruik de [ bevellijn ](apply.md#command-line) of [ Composer ](apply.md#composer) om douanepatches toe te passen.

U kunt op verschillende manieren aangepaste patchbestanden maken. In het volgende voorbeeld wordt gefocust op het maken van een patch op basis van een bekende it.

Een aangepaste patch maken:

1. Maak een map `patches/composer` in uw lokale project.
1. Identificeer GitHub begaat of trekt verzoek om voor het flard te gebruiken. Dit voorbeeld gebruikt [`2d31571` ](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) begaan, verbonden aan GitHub kwestie [ #6474 ](https://github.com/magento/magento2/issues/6474).
1. Voeg de extensies `.patch` of `.diff` toe aan de URL voor doorvoeren. Gebruik `.diff` voor een kleinere bestandsgrootte. Bijvoorbeeld: [ https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Sla de pagina op als een bestand in de map `patches/composer` . Bijvoorbeeld `github-issue-6474.diff` .
1. Bewerk het bestand en verwijder `app/code/<VENDOR>/<PACKAGE>` uit alle paden, zodat deze relatief zijn ten opzichte van de map `vendor/<VENDOR>/<PACKAGE>` .

   >[!NOTE]
   >
   >Teksteditors die automatisch navolgende witruimte verwijderen of nieuwe regels toevoegen, kunnen de patch verbreken. Gebruik een eenvoudige teksteditor om deze wijzigingen aan te brengen.

In het volgende voorbeeld wordt het eerder vermelde DIFF-bestand getoond nadat alle instanties van `app/code/Magento/Payment` zijn verwijderd:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## Patches toepassen

U kunt patches op een van de volgende manieren toepassen:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}
- [Opdrachtregel](/help/upgrade/patches/apply.md#command-line)
- [Composer](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Om een flard op een Adobe Commerce op het project van de wolkeninfrastructuur toe te passen, zie [ flarden ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in _Commerce op de gids van de Wolk_ toepassen.

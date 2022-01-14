---
title: Hoe reparaties werken
description: Leer meer over de verschillende typen patches voor Adobe Commerce en Magento Open Source en hoe ze werken.
source-git-commit: 38b054bbae8ba116557ce367c8397c646c837558
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# Hoe patches werken

>[!WARNING]
>
>We raden u ten zeerste aan alle patches in een testomgeving of ontwikkelomgeving te testen voordat u de patches gaat implementeren in productie. We raden u ook aan een back-up van uw gegevens te maken voordat u een patch toepast. Zie [Een back-up van het bestandssysteem maken en terugdraaien](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Patch-bestanden (of diff-bestanden) zijn tekstbestanden met de volgende notatie:

- Het bestand of de bestanden die moeten worden gewijzigd.
- Het regelnummer waarmee de wijziging moet beginnen en het aantal regels dat moet worden gewijzigd.
- De nieuwe code die moet worden omgewisseld.

Wanneer de [pleister](https://en.wikipedia.org/wiki/Patch_(Unix)) programma wordt uitgevoerd, wordt dit bestand ingelezen en worden de opgegeven wijzigingen aangebracht in het bestand of de bestanden.

Er zijn drie typen patches:

- **Hotfixes**—Patches die Adobe publiceert op de [Beveiligingscentrum](https://magento.com/security/patches).
- **Afzonderlijke patches**—Patches die Adobe Commerce Support maakt en distribueert op individuele basis.
- **Aangepaste patches**—Onofficiële patches die u kunt maken op basis van een git.

## Hotfixes

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties bevatten die vele verkopers beïnvloeden. Deze correcties worden toegepast op de volgende patchrelease voor de van toepassing zijnde secundaire versie. Adobe geeft waar nodig hotfixes vrij.

U kunt hotfixes in [Beveiligingscentrum](https://magento.com/security/patches). Volg de instructies op de pagina om het patchbestand te downloaden, afhankelijk van uw versie en installatietype. Gebruik de [opdrachtregel](../patches/apply.md#) of [Composer](../patches/apply.md) om hotfix-patches toe te passen.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Afzonderlijke patches

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de meest recente ondersteunde secundaire versie (bijvoorbeeld 2.4.x), maar kunnen ontbreken in de vorige ondersteunde secundaire versie (bijvoorbeeld 2.3.x). Adobe geeft zonodig afzonderlijke pleisters af.

Gebruik de [Kwaliteitspatches](https://devdocs.magento.com/quality-patches/tool.html) om afzonderlijke pleisters toe te passen.

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaartse incompatibele wijzigingen.

## Aangepaste patches

Soms duurt het even voor het Team van de Techniek van Adobe om een insectenmoeilijke situatie te omvatten die op GitHub in een versie van Adobe Commerce of van de Magento Open Source Composer wordt gemaakt. In de tussentijd, kunt u een flard van GitHub tot stand brengen en gebruiken [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) insteekmodule om deze toe te passen op de op Composer gebaseerde installatie.

Gebruik de [opdrachtregel] of [Composer] om aangepaste patches toe te passen.

U kunt op verschillende manieren aangepaste patchbestanden maken. In het volgende voorbeeld wordt gefocust op het maken van een patch op basis van een bekende it commit.

Een aangepaste patch maken:

1. Een `patches/composer` in uw lokale project.
1. Identificeer GitHub begaat of trekt verzoek om voor het flard te gebruiken. In dit voorbeeld wordt het [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) commit, verbonden aan GitHub kwestie [#6474](https://github.com/magento/magento2/issues/6474).
1. Voeg de `.patch` of de `.diff` extensies voor de URL toewijzen. Gebruiken `.diff` voor een kleinere bestandsgrootte. Bijvoorbeeld: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. De pagina opslaan als een bestand in het dialoogvenster `patches/composer` directory. Bijvoorbeeld: `github-issue-6474.diff`.
1. Bewerk het bestand en verwijder `app/code/<VENDOR>/<PACKAGE>` van alle paden, zodat deze relatief zijn ten opzichte van de `vendor/<VENDOR>/<PACKAGE>` directory.

   >[!NOTE]
   >
   >Teksteditors die automatisch navolgende witruimte verwijderen of nieuwe regels toevoegen, kunnen de patch verbreken. Gebruik een eenvoudige teksteditor om deze wijzigingen aan te brengen.

In het volgende voorbeeld wordt het eerder vermelde DIFF-bestand getoond nadat alle exemplaren van het bestand zijn verwijderd `app/code/Magento/Payment`:

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

- [Kwaliteitspatches](https://devdocs.magento.com/quality-patches/tool.html)
- [Opdrachtregel](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)

>[!NOTE]
>
>Als u een patch wilt toepassen op een Adobe Commerce-project voor cloudinfrastructuur, raadpleegt u [Patches toepassen](https://devdocs.magento.com/cloud/project/project-patch.html) in de _Wolkengids_.

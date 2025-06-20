---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.1.61'
description: Deze subsectie biedt een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in  [!DNL Quality Patches Tool]  (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.61

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.61.

QPT v1.1.61 omvat de volgende flarden:

1. **ACP2E-3689**: Verhelpt veelvoudige kwesties met de vertoning van de categorieboom op diepere niveaus en het weerspiegelen van anker/niet-ankerverhoudingen.
1. **ACP2E-3705**: Bevestigt een kwestie waar de `indexer_update_all_views` kroonuitvoering ontbreekt wanneer `MAGE_INDEXER_THREADS_COUNT` wordt geplaatst.
1. **ACSD-63883**: Verhelpt de kwestie waar [!UICONTROL Requisition List] een onjuist `items_count` in de [!DNL GraphQL] reactie terugkeert.
1. **ACSD-63974**: Verhelpt de kwestie waar de [!UICONTROL Requisition List] pagina te veel tijd vergt om te laden wanneer er teveel punten zijn, door een pagineringseigenschap aan het [!UICONTROL Requisition List] net op de storefront toe te voegen, die slechts gedeelten verslagen toont die tot het aantal verslagen per pagina, in plaats van alle verslagen in één keer beperkt zijn.
1. **ACSD-64178**: Verhelpt de kwestie waar [!UICONTROL Attribute Set] pagina langzaam uitgeeft laadt als er duizenden productattributen zijn.
1. **ACSD-64209**: Verhelpt de kwestie waar de cron planner alle verhandelbare citaten terugwint zonder hen met de status **[!UICONTROL ordered]** uit te sluiten, die een e-mail of e-mails veroorzaken om worden teweeggebracht.
1. **ACSD-64431**: De `placeOrder` mutatie die de informatie van de couponcode in het verzoek bevat veroorzaakt niet meer een interne fout, maar toont in plaats daarvan aan dat de orde met succes werd geplaatst.
1. **ACSD-64467**: Verhelpt de kwestie waar de redacteur van WYSIWYG leeg na het opslaan van een categoriebeschrijving op het niveau van de archiefmening verschijnt.
1. **ACSD-64546**: Verhelpt de kwestie waar een generisch foutenbericht in UI voorkomt en een *Serie aan de uitzondering van de koordomzetting* wordt opgeslagen in de logboeken tijdens het verschepen van UPS etiketverwezenlijking, die ervoor zorgt dat de daadwerkelijke fout in UI wordt getoond en het correcte foutenbericht in de logboeken wordt opgeslagen.
1. **ACSD-64684**: Verhelpt de kwestie waar een bevestigingsfout voorkomt wanneer het uitgeven van en het opslaan van een geschenkkaart met een waarde groter dan *999* toe te schrijven aan de komma (duizend separator) in het aantal *duizend (1.000)*.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.

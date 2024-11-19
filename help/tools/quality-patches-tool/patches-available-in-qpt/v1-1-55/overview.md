---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.1.55'
description: Deze subsectie biedt een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in  [!DNL Quality Patches Tool]  (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.55

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.55.

QPT v1.1.55 omvat de volgende flarden:

1. **ACSD-58383**: Verhelpt de kwestie waar het uitgeven van een restitutie via [!DNL REST API] met twee identieke verzoeken die gelijktijdig worden uitgevoerd, leidt tot dubbele creditmemo&#39;s.
1. **ACSD-58471**: Verhelpt de kwestie waar de dynamische inhoud op de pagina van het productdetail ontbreekt te laden wanneer de bijbehorende regels van de catalogusprijs gepland zijn.
1. **ACSD-58566**: Verhelpt de kwestie waar [!DNL GraphQL] een interne serverfout terugkeert wanneer het vragen van het `created_at` gebied in de `addPurchaseOrderComment` mutatie.
1. **ACSD-58685**: Verhelpt de kwestie waar de verkoop e-mail in werking gestelde terwijl de e-mailmededeling wordt onbruikbaar gemaakt nog wordt verzonden zodra de e-mailmededeling opnieuw wordt toegelaten.
1. **ACSD-58735**: Verhelpt de kwestie waar beperkt admin niet de verlaten winkelwagentjes op de pagina van de klantenrekening in [!UICONTROL Admin] voor een bijbehorende website kan bekijken.
1. **ACSD-58828**: Verhelpt de kwestie waar het server-zijbevestigingsbericht *adres wordt vereist* verschijnt als om het even welk vereist gebied leeg, naast het cliënt-zijbevestigingsbericht wordt verlaten. De server-zijbevestiging zal niet het bericht voor lege vereiste gebieden tonen, en de cliënt-zijbevestiging zal het foutenmelding behandelen, die, *dit een vereist gebied verklaart.*
1. **ACSD-60344**: Bevestigt de kwestie waar de dubbele e-mails van de ordbevestiging wanneer het gebruiken van a **[!UICONTROL Purchase Order]** met auto-goedkeuring worden verzonden.
1. **ACSD-61348**: Verhelpt de kwestie waar de punten van de wenslijst via [!DNL GraphQL] zichtbaar zijn, maar niet op de storefront in een multi-websitemilieu.
1. **ACSD-61534**: Verhelpt de kwestie waar de ontwerpconfiguratie niet kan worden geplaatst gebruikend het `bin/magento config:set` bevel, en de gesloten waarden kunnen door vormmanipulatie worden veranderd. Vergrendelde waarden die zijn ingesteld in de [!DNL CLI] met `--lock-env` of `--lock-conf` , kunnen nu niet worden bijgewerkt.
1. **ACSD-61785**: Verhelpt de kwestie waar het bijwerken van het `reward_warning_notification` attribuut niet mogelijk via [!DNL GraphQL] mutatie en [!DNL REST API] vraag is, die zijn gedrag met `reward_update_notification` richt.
1. **ACSD-62591**: Verhelpt de kwestie waar het thema niet behoorlijk schakelt wanneer **[!UICONTROL User Agent Rules]** wordt gevormd.
1. **ACSD-62793**: Verhelpt de kwestie waar `datetime` attributen in uitgevoerde gegevens niet de tijdcomponent omvatten. Bovendien als *[!UICONTROL Fields Enclosure]* ** wordt toegelaten, zijn de attributenwaarden in de `additional_attributes` kolom ingesloten binnen dubbel-citaten.
1. **ACSD-62332**: Verhelpt de kwestie waar de productlijst [!DNL GraphQL] vraag tot a `total_count` van 10.000 producten beperkt is. Ook, bevestigt de kwestie waar [!DNL Live Search] de huidige pagina aan *1* in plaats van pagina *2* in de onderzoekscriteria plaatst wanneer gevraagd via [!DNL GraphQL].

Gebruik het menu links om naar een specifieke patchpagina te navigeren.

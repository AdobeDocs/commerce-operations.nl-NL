---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.1.76'
description: Deze subsectie biedt een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in  [!DNL Quality Patches Tool]  (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9d24eeeeedc02e2e086560b5f18baa4a1a61b972
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.76

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 omvat de volgende flarden:
1. **ACSD-67091**: Bevestigt de maximum schrijvers grootte fout om de indexschoonmaakbeurt van de catalogusregel te verzekeren door twee schrappingsstrategieën uit te voeren die op gegevensvolume worden gebaseerd.
1. **ACSD-67370**: lost veelvoudige kwesties op waar de onjuiste prijzen voor de producten van de Bundel op PDP/PLP en de kartpagina voor multi-muntopslag werden getoond.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**: Verhelpt een kwestie waar het plaatsen van een orde voor een verhandelbaar citaat verkeerd toevoegt of extra wortellijnen aan het citaat samenvoegt. Producten worden nu correct toegevoegd aan het winkelwagentje nadat de laatste stap van het afrekenen van prijsnoteringen is verlaten.
1. **ACSD-69086**: Verhelpt de kwestie waar de cron baan er niet in slaagt om veranderingslijsten te ontruimen, veroorzakend [!DNL Galera Cluster] neerstortingen wanneer het behandelen van grote hoeveelheden gegevens.
1. **ACSD-69115**: Verhelpt een kwestie waar de het winkelwagentfouten niet aan de admin gebruiker werden getoond toen het beheren van het het winkelwagentje voor een klant die aan een niet-standaard website wordt toegewezen.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: Verhelpt een kwestie waar het schrappen van de standaard basiswebsite en het gebruiken van de secundaire website als gebrek in een fout resulteert wanneer het proberen om de laagprijs voor de secundaire website via [!DNL REST] API bij te werken.
1. **ACSD-69203**: Bevestigt een kwestie waar **[!UICONTROL Products List]** widget onjuiste resultaten terugkeert wanneer de veelvoudige categorieën in de categorietoestand werden vermeld.
1. **ACSD-69261**: Verhelpt een kwestie waar een coupon van de de regelregel van de kartprijs die voor enig gebruik per klant wordt gevormd veelvoudige tijden wegens onjuiste behandeling van het `times_used` attribuut in gedeeltelijke factuur en resterende scenario&#39;s van de kwantitatieve annulering werd opnieuw gebruikt.
1. **ACSD-69308**: Verhelpt een kwestie waar de regels van de catalogusprijs niet van toepassing waren toen `special_price` slechts op het websiteniveau (niet bij **[!UICONTROL All Store Views]**) werd geplaatst. Na de correctie worden de regels voor catalogusprijzen correct toegepast door eerst de standaardopslag van de website te controleren.
1. **ACSD-69319**: Verhelpt een kwestie waar de bundelprijzen niet behoorlijk werden geïndexeerd wanneer de kindproducten voorraad onder douanebronnen hadden.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: Verhelpt een kwestie waar het wijzigen van het geval van SKU het product om uit voorraad op de winkel veroorzaakt te verschijnen.
1. **ACSD-69331**: Verhelpt een kwestie waar de inhoudsmakers in de media galerie geen omslagen met slechts de `create_folder` toestemming konden tot stand brengen. Na de correctie kunnen ze naar behoren mappen maken.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: Verhelpt een kwestie waar het verminderen van de hoeveelheid van een product in [!UICONTROL Admin] aan minder dan de vorige hoeveelheid in een kart het vermogen om de producthoeveelheid in dat karretje via GraphQL uit te geven tegenhield.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**: Verhelpt een kwestie waar de veranderingen van SKU voor producten met een actieve geplande update werden toegestaan. Na de moeilijke situatie, worden de veranderingen van SKU tijdens actieve updates verboden; sparen ontbreekt met een duidelijke fout, en het admin gebied van SKU wordt onbruikbaar gemaakt. Dit voorkomt inconsistenties in de MSI-inventaris die worden veroorzaakt door wijzigingen in SKU tijdens het afbouwen van terugdraaiversies.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.

---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.1.78'
description: Deze subsectie verstrekt een gedetailleerde beschrijving van de kwesties die door de flarden beschikbaar in  [!DNL Quality Patches Tool]  (QPT) v1.1.78 worden bevestigd.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: e0111754306fc220ba7eacf3590b70bcc048f34f
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.78

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 omvat de volgende flarden:
1. **[ACP2E-4416](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416.md)**: Hiermee wordt het probleem verholpen waarbij beloningspunten voor klanten niet worden geïnitialiseerd wanneer ze in Admin worden gemaakt.
1. **[ACP2E-4431](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431.md)**: Hiermee wordt het probleem verholpen waarbij [!UICONTROL Related Products] dat overeenkomt met de doelregels, tijdens het herindexeringsproces wordt verwijderd.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: Hiermee wordt het probleem verholpen waarbij cadeaukaarten niet correct worden toegepast bij het uitchecken na geslaagde reCAPTCHA v2-validatie (&#39;Ik ben geen robot&#39;) op de winkel.
1. **ACP2E-4448**: Hiermee wordt het probleem verholpen waarbij configuratiewijzigingen die tijdens een storing met Redis zijn aangebracht, niet worden doorgevoerd nadat Redis is hersteld, waardoor schaalwaarden blijven bestaan.
1. **ACP2E-4452**: Hiermee wordt het probleem verholpen waarbij de productprijzen op de pagina Snel bestellen belasting bevatten, ongeacht de configuratie van de belastingweergave.
1. **ACP2E-4456**: Oplossing van een probleem waarbij bij het annuleren van een bestelling met behulp van een GraphQL-mutatie een bestelling die volledig met een cadeaukaart is betaald, niet wordt overgebracht naar de status Gesloten.
1. **[ACP2E-4507](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507.md)**: Hiermee wordt het probleem verholpen waarbij [!UICONTROL Password Options] -configuratie niet wordt toegepast voor aanvragen voor het opnieuw instellen van wachtwoorden van klanten die via GraphQL-mutaties zijn gemaakt.
1. **ACP2E-4513**: Hiermee verhelpt u het probleem waarbij verlopen CAPTCHA-afbeeldingen niet van het systeem worden verwijderd.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: Hiermee wordt het probleem verholpen waarbij een periodiek dubbele-sleutelfout optreedt in de quote_coupons-tabel wanneer meerdere samenvoegaanvragen voor winkelwagentjes of aanhalingstekens tegelijk worden uitgevoerd.
1. **ACP2E-4528**: Het probleem met plaatsvalidatie in klantadressen is opgelost, waardoor nu een slash (/) wordt toegestaan en ongeldige tekens zoals !, &quot;, # en ? worden afgewezen.
1. **[ACP2E-4535](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535.md)**: Oplossingen een kwestie waar het voorleggen van de vergat-wachtwoord vorm veroorzaakt dat de zitting wordt vernietigd of opnieuw geproduceerd (veranderingen PHPSESSID) en de gastkar wordt ontruimd.
1. **ACP2E-4540**: Hiermee wordt het probleem verholpen waarbij de Fotorama-bibliotheek niet correct werd geladen, zodat alleen de eerste bijgevoegde afbeelding zichtbaar was.
1. **ACP2E-4555**: Hiermee wordt het probleem opgelost waarbij moderne telefoonnummers &quot;.&quot; bevatten of &quot;/&quot; niet correct zijn gevalideerd.
1. **ACP2E-4565**: Verhelpt de kwestie waar de vraag van het Bedrijf GraphQL &quot;De huidige klant wordt niet geautoriseerd&quot;terugkeert wanneer de x-Adobe-Bedrijfs kopbal wordt gebruikt.
1. **ACP2E-4591**: Hiermee wordt het probleem verholpen waarbij klantsegmenten op basis van het aantal bestellingen, zoals &quot;Eerste kopers&quot;, niet werden bijgewerkt toen bestellingen via de REST-API werden geplaatst.
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**: Hiermee wordt het probleem verholpen waarbij de bibliotheek Fotorama niet correct werd geladen, zodat alleen de eerste bijgevoegde afbeelding zichtbaar was.
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**: Hiermee wordt het probleem opgelost waarbij moderne telefoonnummers &quot;.&quot; bevatten of &quot;/&quot; niet correct zijn gevalideerd.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: Verhelpt de kwestie waar de vraag van het Bedrijf GraphQL &quot;De huidige klant wordt niet geautoriseerd&quot;terugkeert wanneer de x-Adobe-Bedrijfs kopbal wordt gebruikt.
1. **ACP2E-4591**: Hiermee wordt het probleem verholpen waarbij klantsegmenten op basis van het aantal bestellingen, zoals &quot;Eerste kopers&quot;, niet werden bijgewerkt toen bestellingen via de REST-API werden geplaatst.
1. **[ACP2E-4609](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609.md)**: Hiermee wordt het probleem verholpen waarbij op de pagina Mijn aanhalingstekens geen aanhalingstekens worden weergegeven wanneer sommige aanhalingstekens verwijderde producten bevatten.
1. **ACP2E-4591**: Hiermee wordt het probleem verholpen waarbij klantsegmenten op basis van het aantal bestellingen, zoals &quot;Eerste kopers&quot;, niet werden bijgewerkt toen bestellingen via de REST-API werden geplaatst.
1. **ACP2E-4609**: Hiermee wordt het probleem verholpen waarbij op de pagina Mijn aanhalingstekens geen aanhalingstekens worden weergegeven wanneer sommige aanhalingstekens verwijderde producten bevatten.
1. **[ACP2E-4613](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613.md)**: Hiermee wordt het probleem verholpen waarbij grote mediamapstructuren trage reacties met getrouwe getrouwe getrouwe waarden veroorzaakten, wat tot langere laadtijden voor de mappenstructuur van **[!UICONTROL Media Gallery]** leidde.
1. **ACP2E-4628**: Oplossing voor het probleem dat bij het importeren van klanten met e-mailadressen in hoofdletters de fout met de ongedefinieerde arraysleutel optreedt wanneer Account Sharing is ingesteld op Global.
1. **ACP2E-4665**: Hiermee wordt het probleem verholpen waarbij onderliggende producten van configureerbare producten die video&#39;s in de productgalerieën bevatten, niet worden vermeld wanneer ze via de REST API worden aangevraagd.
1. **ACP2E-4732**: Oplossingen een kwestie waar de gedeeltelijke indexatie voor klanten met een groot aantal updates ophield toen version_id kolom in de veranderingslijst zijn maximumwaarde bereikte.
1. **ACP2E-4763**: Hiermee wordt het probleem verholpen waarbij de GraphQL-query voor CustomerOrders de opgeblazen original_price_include_tax en original_row_total_include_tax waarden retourneert wanneer Catalog Prices is ingesteld op Including Tax, omdat de belasting tweemaal wordt toegepast.
1. **ACSD-60989: Hiermee wordt het probleem verholpen waarbij het wijzigen van een kolom met een buitenlandse sleutel via een declaratief schema fouten veroorzaakt op MariaDB.**

Gebruik het menu links om naar een specifieke patchpagina te navigeren.

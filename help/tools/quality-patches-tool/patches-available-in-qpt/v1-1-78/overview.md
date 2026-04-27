---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.1.78'
description: Deze subsectie verstrekt een gedetailleerde beschrijving van de kwesties die door de flarden beschikbaar in  [!DNL Quality Patches Tool]  (QPT) v1.1.78 worden bevestigd.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0494717c06fcabcb093a2b168ae714f773ed6f7b
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.78

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 omvat de volgende flarden:
1. **ACP2E-4416**: Verhelpt de kwestie waar de punten van de klantenbeloning niet worden geïnitialiseerd wanneer gecreeerd in Admin.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: Verhelpt de kwestie waar de giftekaarten niet correct bij kassa na succesvolle reCAPTCHA v2 (&#39;ik ben geen robot&#39;) bevestiging op de storefront worden toegepast.
1. **ACP2E-4431**: Verhelpt de kwestie waar de Verwante Producten die door de doelregels worden aangepast tijdens het herindexeringsproces worden geschrapt.
1. **ACP2E-4448**: Verhelpt de kwestie waar de configuratieveranderingen die tijdens de stroomonderbrekingen van Redis worden aangebracht niet worden weerspiegeld nadat Redis terugkrijgt, veroorzakend de schaalwaarden om blijven bestaan.
1. **ACP2E-4452**: Verhelpt de kwestie waar de productprijzen op de Snelle pagina van de Orde belasting ongeacht de configuratie van de belastingvertoning omvatten.
1. **ACP2E-4456**: Verhelpt een kwestie waar het annuleren van een orde die een verandering van GraphQL gebruikt geen orde overgaat die volledig met giftekaarten aan de Gesloten status wordt betaald.
1. **ACP2E-4507**: Verhelpt de kwestie waar de configuratie van de Opties van het Wachtwoord niet wordt toegepast voor het terugstellen van het klantenwachtwoord verzoeken die door de mutaties van GraphQL worden gemaakt.
1. **ACP2E-4513**: Verhelpt de kwestie waar de verlopen beelden CAPTCHA niet van het systeem worden geschrapt.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: Verhelpt de kwestie waar een periodiek dubbele zeer belangrijke fout op de quote_coupons lijst voorkomt wanneer de veelvoudige kartsamenvoeging of citaat sparen verzoeken tezelfdertijd lopen.
1. **ACP2E-4528**: Bevestigt de kwestie met plaatsbevestiging in klantenadressen, die nu een voorwaartse schuine streep (/) karakter toestaat en ongeldige karakters zoals !, &quot;, #, en verwerpt?.
1. **ACP2E-4535**: Verhelpt een kwestie waar het voorleggen van de vergat-wachtwoordvorm de te vernietigen of opnieuw te produceren zitting veroorzaakt (veranderingen PHPSESSID) en de gastkar wordt ontruimd.
1. **ACP2E-4540**: Verhelpt de kwestie waar de bibliotheek Fotorama niet correct laadde, veroorzakend slechts het eerste in bijlage beeld om zichtbaar te zijn.
1. **ACP2E-4555**: Verhelpt de kwestie waar de moderne telefoonaantallen &quot;.&quot; bevatten of &quot;/&quot; niet correct zijn gevalideerd.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: Verhelpt de kwestie waar de vraag van GraphQL van het Bedrijf &quot;de huidige klant niet&quot;terugkeert wanneer de x-Adobe-Bedrijfs kopbal wordt gebruikt.
1. **ACP2E-4591**: Verhelpt de kwestie waar de klantensegmenten die op ordertelling, zoals &quot;Eerste-tijdekopers&quot;worden gebaseerd, niet bijwerkten toen de orden via REST API werden geplaatst.
1. **ACP2E-4609**: Verhelpt de kwestie waar de Mijn pagina van Citaten geen citaten toont wanneer sommige citaten geschrapte producten bevatten.
1. **ACP2E-4613**: Verhelpt de kwestie waar de grote media folderstructuren langzame getrouwe reacties veroorzaakten, leidend tot de uitgebreide tijden van het laden van de folderboom van de Galerij van Media.
1. **ACP2E-4628**: Verhelpt de kwestie waar het invoeren van klanten met hoofdletters e-mailadressen in de ongedefinieerde seriezeer belangrijke fout resulteert, wanneer het Delen van de Rekening aan Globaal wordt geplaatst.
1. **ACP2E-4665**: Verhelpt de kwestie waar de kindproducten van configureerbare producten die video&#39;s in de productgalerieën bevatten niet vermeld wanneer gevraagd door REST API zijn.
1. **ACP2E-4732**: Verhelpt een kwestie waar de gedeeltelijke indexatie voor klanten met een groot aantal updates ophield toen de version_id kolom in de veranderingslijst zijn maximumwaarde bereikte.
1. **ACP2E-4763**: Verhelpt de kwestie waar de GraphQL customerOrders vraagwinst opgeblazen original_price_include_tax en original_row_total_include_tax waarden wanneer de Prijzen van de Catalogus aan Including Belasting worden geplaatst, toe te schrijven aan belasting die tweemaal wordt toegepast.
1. **ACSD-60989**: Verhelpt de kwestie waar het wijzigen van een kolom met een buitenlandse sleutel door een verklarend schema fouten op MariaDB veroorzaakt.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.

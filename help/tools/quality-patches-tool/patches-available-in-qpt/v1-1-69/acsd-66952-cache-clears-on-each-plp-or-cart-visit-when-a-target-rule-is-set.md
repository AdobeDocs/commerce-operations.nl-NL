---
title: 'ACSD-66952: Het geheime voorgeheugen ontruimt op elk PLP of kart bezoek wanneer een doelregel wordt geplaatst'
description: Pas de ACSD-66952-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de cache tijdens elk bezoek van de PLP of het winkelwagentje werd gewist, wat onnodige prestatieoverhead tot gevolg had wanneer een doelregel werd ingesteld.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-66952: Het geheime voorgeheugen ontruimt op elk PLP of kart bezoek wanneer een doelregel wordt geplaatst

De ACSD-66952-patch verhelpt het probleem waarbij de cache wordt gewist bij elk bezoek van de PLP of het winkelwagentje, wat leidt tot prestatieoverhead wanneer een doelregel wordt ingesteld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66952. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De kwestie waar het geheime voorgeheugen op elk PLAK of kart bezoek wordt ontruimd, veroorzakend prestatiesoverheadkosten wanneer een doelregel wordt geplaatst.

<u> Stappen om </u> te reproduceren:

1. Een kleine set voorbeeldgegevens genereren.
1. Geef hieronder de waarden voor de doelregel op:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Verwante Producten*
      * **[!UICONTROL Status]** = *Actief*
      * **[!UICONTROL Apply to]** = *Verwante Producten*
   1. **[!UICONTROL Products to Match]**
      * Laat de standaardwaarde ongewijzigd.
   1. **[!UICONTROL Products to Display]**
      * Als **ALLE** van deze voorwaarden ** waar zijn, plaats **[!UICONTROL Product Category]** = *Constante Waarde 11111*
1. Start de bewaking van de logboeken voor verzoeken tot invalidatie van het cachegeheugen.
1. Bezoek de productpagina.
1. Voeg een product toe aan de winkelwagentje en navigeer naar de winkelwagentje.

<u> Verwachte resultaten </u>:

De toepassing moet de cache niet ongeldig maken tijdens het bladeren door de site.

<u> Ware resultaten </u>:

Cachetags worden ongeldig gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen

---
title: 'ACSD-64149: Klantsegment met een voorwaarde [!UICONTROL Date range] kan worden opgeslagen wanneer slechts één datum wordt bewerkt'
description: Pas de ACSD-64149-patch toe om het Adobe Commerce-probleem op te lossen waarbij het klantsegment met een **[!UICONTROL Date range]**-voorwaarde kan worden opgeslagen wanneer slechts een van de datums wordt bewerkt.
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149: Klantsegment met een voorwaarde [!UICONTROL Date range] kan worden opgeslagen wanneer slechts één datum wordt bewerkt

De ACSD-64149-patch verhelpt het probleem waarbij een klantsegment met een datumbereikvoorwaarde kan worden opgeslagen wanneer slechts een van de datums wordt bewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 wordt geïnstalleerd. De patch-id is ACSD-64149. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een bestaand klantensegment met een voorwaarde op producten binnen het winkelwagentje wordt uitgeeft die door een datumwaaier wordt gespecificeerd, ontbreekt de consument `matchCustomerSegmentProcessor` met een SQL fout.

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor dat de consument `matchCustomerSegmentProcessor` wordt uitgevoerd:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Ga naar de **[!UICONTROL Magento backend]** .
1. Ga naar **[!UICONTROL Customers]** > **[!UICONTROL Segments]** .
1. Klik op **[!UICONTROL Add Segment]** .
1. Ga a **[!UICONTROL Segment Name]** in, selecteer een website onder **[!UICONTROL Assigned to Website]**, en zorg ervoor **[!UICONTROL Status]** aan *Actief* wordt geplaatst.
1. Klik op **[!UICONTROL Save and Continue Edit]**.
1. Ga naar het **[!UICONTROL Conditions]** lusje en voeg een nieuwe Voorwaarde toe: *Producten {} > {} Lijst van het Product* **.
1. Voeg een subvoorwaarde voor **[!UICONTROL Date range]** toe en stel een geldige **[!UICONTROL Date range]** in.
1. Klik op de groene bevestigingsknop naast de **[!UICONTROL Date range]** .
1. Klik nogmaals op **[!UICONTROL Date range]** , selecteer de datumkiezer, bewerk een van de datumwaarden en klik op de groene knop om te bevestigen.

<u> Verwachte resultaten </u>:

De kiezer van **[!UICONTROL Date range]** mag geen tijd aan de datum toevoegen wanneer u bewerkingen uitvoert.

<u> Ware resultaten </u>:

* De kiezer van **[!UICONTROL Date range]** voegt tijd toe aan de datum:
   * De ene datum heeft alleen de datum, de andere datum en tijd zijn opgegeven.
* De volgende fout wordt weergegeven in de logboeken:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

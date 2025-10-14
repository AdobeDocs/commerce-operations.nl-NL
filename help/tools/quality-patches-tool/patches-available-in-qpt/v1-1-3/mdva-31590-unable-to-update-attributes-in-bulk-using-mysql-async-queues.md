---
title: 'MDVA-31590: Onbekwaam om attributen in bulk bij te werken gebruikend MySQL async rijen'
description: De patch MDVA-31590 lost de kwestie op waar de gebruikers attributen in bulk kunnen bijwerken gebruikend MySQL async rijen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 is geïnstalleerd. De patch-id is MDVA-31590. De kwestie is opgelost in Adobe Commerce 2.4.2.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590: Onbekwaam om attributen in bulk bij te werken gebruikend MySQL async rijen

De patch MDVA-31590 lost de kwestie op waar de gebruikers attributen in bulk kunnen bijwerken gebruikend MySQL async rijen. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 geïnstalleerd is. De patch-id is MDVA-31590. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen attributen niet bulksgewijs bijwerken met MySQL async.

<u> Stappen om </u> te reproduceren:

1. Voer in het productraster op de achtergrond een massale actie uit om de kenmerkwaarden voor een paar producten bij te werken.
   * De producten van de controle en selecteren **Attributen van de Update** van het dropdown van Acties.
1. Stel waarden in voor de vereiste kenmerken en wijs producten toe aan websites en sla deze op.
1. Wanneer de pagina opnieuw wordt geladen, wordt er een bericht als volgt weergegeven:
   *Taak &quot;de attributen van de Update voor N geselecteerde producten&quot;: 1 punt(en) zijn gepland voor een update.*
1. Wacht enkele seconden en laad de achtergrondpagina opnieuw.

<u> Verwachte resultaten </u>:

1. De pagina toont een succesvol updatebericht zoals: *1 punt(en) is met succes bijgewerkt.*
1. Kenmerkwaarden voor verwante producten worden bijgewerkt.
1. In DB worden nieuwe records gemaakt in zowel de tabel `magento_bulk` als de tabel `magento_operation` (bewerkingen die betrekking hebben op de grote hoeveelheid).
1. Nieuwe record(s) worden gemaakt in de tabel `queue_message` (gerelateerd aan de wachtrijen `product_action_attribute.update` en/of `product_action_attribute.website.update` ).
1. `queue_message_status` -tabel bevat records met status &quot;4&quot;.
1. Er zijn GEEN fouten in `system.log`.

<u> Ware resultaten </u>:

1. Op de pagina wordt nog steeds een bericht weergegeven zoals in het volgende voorbeeld:
   *Taak &quot;de attributen van de Update voor N geselecteerde producten&quot;: 1 punt(en) zijn gepland voor een update.*
1. De kenmerkwaarden voor de producten worden bijgewerkt.
1. Een nieuwe record wordt gemaakt in de tabel `message_bulk` , maar er zijn geen verwante record(s) in de tabel `magento_operation` .
1. Nieuwe records worden gemaakt in `queue_message` - en `queue_message_status` -tabellen.
1. `queue_message_status` table has record with error status (status value &quot;6&quot;).
1. `system.log` bevat een fout die lijkt op het volgende:

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.

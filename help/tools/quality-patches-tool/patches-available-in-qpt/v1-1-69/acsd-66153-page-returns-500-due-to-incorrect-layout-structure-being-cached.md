---
title: 'ACSD-66153: Pagina retourneert 500 fout als gevolg van een onjuiste layoutstructuur in de cache'
description: Pas de ACSD-66153-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een pagina een foutcode van 500 retourneert vanwege een onjuiste lay-outstructuur in de cache.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 2d6f47cb-2244-40b6-b1b9-0d03f13adc43
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-66153: Pagina retourneert 500 fout als gevolg van een onjuiste layoutstructuur in de cache

De ACSD-66153-patch verhelpt het probleem waarbij een pagina een foutcode van 500 retourneert vanwege een onjuiste lay-outstructuur in de cache. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66153. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p10

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een pagina retourneert een fout van 500 vanwege een onjuiste layoutstructuur in de cache.

<u> Stappen om </u> te reproduceren:

1. Installeer `2.4-develop` .
1. Aangepaste module maken en installeren:
1.1 Voeg een aangepast blok toe aan de lay-out `catalog_category_view` .
1.1 Injecteer `Magento\Framework\View\Result\Layout` in het aangepaste blok via de constructor.
1. Maak de categorie **[!UICONTROL shop]** .
1. Openen **[!UICONTROL two terminal windows]** :
   1. **Terminal 1**: Maak de lay-outcache voortdurend schoon:

      ```shell
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2**: Gelijktijdige aanvragen naar de categoriepagina simuleren:

      ```shell
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Sommige aanvragen mislukken willekeurig met een 500-statuscode en in `var/log/support_report.log` wordt de volgende fout weergegeven:

   ```yaml
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u> Verwachte resultaten </u>:

Alle verzoeken keren 200 OK terug.

<u> Ware resultaten </u>:

Sommige verzoeken retourneren soms de fout van 500 interne server.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

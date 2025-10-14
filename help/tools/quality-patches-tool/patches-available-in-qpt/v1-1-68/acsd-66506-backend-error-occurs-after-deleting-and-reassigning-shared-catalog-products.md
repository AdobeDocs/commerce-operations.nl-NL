---
title: 'ACSD-66506: De fout van de achtergrond komt na het schrappen en het opnieuw toewijzen van de Gedeelde producten van de Catalogus voor'
description: Pas de ACSD-66506-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de backend de fout veroorzaakt *Het aangevraagde product bestaat niet. Verifieer het product en probeer opnieuw* na het schrappen van eerder toegewezen producten en het toewijzen van nieuwe aan een Gedeelde Catalogus.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: De fout van de achtergrond komt na het schrappen en het opnieuw toewijzen van de Gedeelde producten van de Catalogus voor

Het ACSD-66506 flard lost de kwestie op waar de backend de fout *werpt het gevraagde product niet bestaat. Verifieer het product en probeer opnieuw* na het schrappen van eerder toegewezen producten en het toewijzen van nieuwe degenen aan een Gedeelde Catalogus. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66506. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het schrappen van eerder toegewezen producten en het toewijzen van nieuwe degenen aan a **[!UICONTROL Shared Catalog]**, keert het achtereind de volgende fout terug: *het gevraagde product bestaat niet. Verifieer het product en probeer opnieuw*

<u> Stappen om </u> te reproduceren:

1. Sommige producten maken met de prestatiekoolset: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Ga naar **[!UICONTROL [!DNL B2B] Features]** Configuratie en stel **[!UICONTROL Enable Company]** en **[!UICONTROL Enable Shared Catalog]** in op `Yes` .
1. Maak een nieuwe gedeelde catalogus.
1. Wijs alle geproduceerde producten aan de pas gecreëerde Gedeelde Catalogus toe.
1. Gebruik **[!UICONTROL Product Import]** om een product te verwijderen dat is toegewezen aan de gedeelde catalogus.
   1. Een door SKU gefilterd product exporteren.
   1. Selecteer **[!UICONTROL Import Behavior: Delete]** en importeer hetzelfde bestand.
1. Open **[!UICONTROL Shared Catalog]** en vorm tarifering en structuur.
   1. Selecteer **[!UICONTROL Set Pricing and Structure]** .
   1. Klik op **[!UICONTROL Next]** en vervolgens op **[!UICONTROL Generate Catalog]** .
   1. Klik op **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

Er treedt geen fout op en de producten blijven in de gedeelde catalogus staan, zelfs als er een fout optreedt.

<u> Ware resultaten </u>:

Een fout komt voor: *het gevraagde product bestaat niet. Verifieer het product en probeer opnieuw*, en alle producten worden verwijderd uit de Gedeelde Catalogus.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

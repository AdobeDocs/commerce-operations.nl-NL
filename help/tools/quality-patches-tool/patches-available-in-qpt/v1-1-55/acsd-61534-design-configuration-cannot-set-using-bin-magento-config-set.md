---
title: 'ACSD-61534: ontwerpconfiguratie kan niet worden ingesteld met bin/magento config:set, en vergrendelde waarden kunnen worden gewijzigd via formuliermanipulatie'
description: Pas ACSD-61534 flard toe om de kwestie van Adobe Commerce te bevestigen waar de ontwerpconfiguratie niet kan worden geplaatst gebruikend het "bak/magento config:set"bevel, en de gesloten waarden kunnen door vormmanipulatie worden veranderd.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: ontwerpconfiguratie kan niet worden ingesteld met `bin/magento config:set` en vergrendelde waarden kunnen worden gewijzigd via formuliermanipulatie

De ACSD-61534-patch verhelpt het probleem waarbij de ontwerpconfiguratie niet kan worden ingesteld met de opdracht `bin/magento config:set` en vergrendelde waarden kunnen worden gewijzigd door formuliermanipulatie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-61534. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ontwerpconfiguratie kan niet worden ingesteld met de opdracht `bin/magento config:set` en vergrendelde waarden kunnen worden gewijzigd door het bewerken van formulieren. Met deze patch kunnen vergrendelde waarden die zijn ingesteld via het opdrachtregelprogramma (CLI) met `--lock-env` of `--lock-conf` , niet worden bijgewerkt.

<u> Stappen om </u> te reproduceren:

1. Vergrendel een config-waarde met een omgevingsvariabele van de cloud, zoals `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES` .
1. Ga naar het deelvenster *[!UICONTROL Admin]* .
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** .
1. Klik op **[!UICONTROL Edit]** bij **[!UICONTROL Global/Main website]** in de tweede rij.
1. Thema bewerken voor een winkelweergave.
1. Open de HTML-kop.
1. Schakel het uitgeschakelde **[!UICONTROL Scripts and Style Sheets]** veld in met behulp van ontwikkelaarsgereedschappen.
1. Wijzig de waarde en sla deze op.

<u> Verwachte resultaten </u>:

Een vergrendelde waarde kan niet worden opgeslagen.

<u> Ware resultaten </u>:

Tabel `core_config_data` bevat een bijgewerkte waarde voor `design/head/includes` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

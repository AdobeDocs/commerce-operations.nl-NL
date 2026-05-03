---
title: ACSD-55031 Fout van type "gemengd" kan niet nullable zijn tijdens compilatie
description: Pas de ACSD-55031-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de fout *Type "gemengd" niet kan worden geannuleerd* tijdens het compileren na het installeren van een aangepaste extensie.
feature: Extensions
role: Admin, Developer
exl-id: 770d35aa-7ce2-4517-b393-b7c623c9f779
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-55031 `Type "mixed" cannot be nullable` fout tijdens compilatie

De ACSD-55031-patch verhelpt het probleem waarbij de `Type "mixed" cannot be nullable` -fout optreedt tijdens het compileren na het installeren van een aangepaste extensie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-55031. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout `Type "mixed" cannot be nullable` treedt op tijdens de compilatie.

<u> Stappen om </u> te reproduceren:

1. Een aangepaste extensie installeren.
1. Voer de opdracht `bin/magento setup:di:compile` uit.

<u> Verwachte resultaten </u>:

Er treden geen fouten op tijdens de compilatie.

<u> Ware resultaten </u>:

Het bestand `var/log/system.log` bevat de fout:

```text
report.ERROR: Type "mixed" cannot be nullable
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

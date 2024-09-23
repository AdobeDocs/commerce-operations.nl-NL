---
title: 'ACSD-49513: Synchronisatie van externe opslag mislukt'
description: Pas de ACSD-49513-patch toe om het Adobe Commerce-probleem op te lossen waarbij de synchronisatie van de externe opslag mislukt als gevolg van 0-byte bestanden.
feature: Iaas, Storage
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-49513: Synchronisatie van externe opslag mislukt vanwege bestanden van 0 byte

De ACSD-49513-patch verhelpt het probleem waarbij de synchronisatie van de externe opslag mislukt als gevolg van bestanden van 0 byte. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-49513. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De synchronisatie van de externe opslag mislukt vanwege bestanden van 0 byte.

<u> Stappen om </u> te reproduceren:

1. Configureer de AWS S3 als externe opslag.
1. Voer `[bin/magento remote-storage:sync]` uit om ervoor te zorgen dat de synchronisatie aan het begin correct werkt.
1. Maak een bestand van 0 byte in de `[pub/media]` .
1. Voer `[bin/magento remote-storage:sync]` opnieuw uit.

<u> Verwachte resultaten </u>:

Aangezien de AWS S3 0-byte bestanden accepteert op de S3 Direct-push, is er geen fout.

<u> Ware resultaten </u>:

De volgende fout treedt op:

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'AC-14985: Fout bij verzenden van SMTP-e-mails met TLS'
description: Pas AC-14985 flard toe om de kwestie van Adobe Commerce te bevestigen waar een fout voorkomt wanneer het verzenden van Eenvoudige e-mail van het Protocol van de Overdracht van de Post (SMTP) gebruikend de Veiligheid van de Laag van het Vervoer (TLS).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# AC-14985: Fout bij verzenden van SMTP-e-mails met TLS

Het AC-14985 flard verhelpt een kwestie waar een fout voorkomt wanneer het verzenden van Eenvoudige e-mail van het Protocol van de Overdracht van de Post (SMTP) gebruikend de Veiligheid van de Laag van het Vervoer (TLS). Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is AC-14985. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op bij het verzenden van e-mail via SMTP met TLS ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Stel de SMTP-configuratie als volgt in:
* Vervoer: SMTP
* Host: url.to.smtp.host
* Poort: 587
* SSL: TLS

<u> Verwachte resultaten </u>:

Het e-mailbericht is zonder fouten verzonden.

<u> Ware resultaten </u>:

De volgende fout wordt weergegeven:

```text
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

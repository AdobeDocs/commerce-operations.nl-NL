---
title: 'ACSD-60811: hiermee wordt de beperking bij het bijwerken van de orderstatus naar aangepaste waarden gecorrigeerd'
description: Pas de ACSD-60811-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het bijwerken van de orderstatus met een aangepaste waarde of opmerking alleen mogelijk is als de huidige status 'processing' of 'fraude' is.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811: hiermee wordt de beperking bij het bijwerken van de orderstatus naar aangepaste waarden gecorrigeerd

ACSD-60811 flard lost de kwestie op waar het bijwerken van de ordestatus met een douanewaarde of een commentaar slechts mogelijk is als de huidige status of &quot;[!UICONTROL Processing]&quot;of &quot;[!UICONTROL Suspected Fraud]&quot;is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-60811. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bijwerken van de ordestatus met een douanewaarde of een commentaar is slechts mogelijk als de huidige status of *verwerking* of *fraude* is. De orderstatus blijft ongewijzigd wanneer een nieuwe status wordt geselecteerd en verzonden.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** om een aangepaste orderstatus te maken in het deelvenster Beheer.
1. Klik op **[!UICONTROL Assign Status to State]** om de aangepaste status aan de orderstatus toe te wijzen.
1. Wijzig de status van de volgorde op de pagina met de ordeweergave in het deelvenster Beheer.

<u> Verwachte resultaten </u>:

De beheerder moet de status van de volgorde kunnen wijzigen in een aangepaste orderstatus in het beheerpaneel.

<u> Ware resultaten </u>:

De orderstatus blijft hetzelfde wanneer een nieuwe orderstatus wordt geselecteerd en verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

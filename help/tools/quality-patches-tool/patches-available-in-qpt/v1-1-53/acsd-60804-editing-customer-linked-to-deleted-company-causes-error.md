---
title: 'ACSD-60804: Het bewerken van een klant die is gekoppeld aan een verwijderd bedrijf, resulteert in een fout'
description: Pas de ACSD-60804-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het bewerken van een klant die is gekoppeld aan een verwijderd bedrijf, resulteert in een fout *Call naar een lidfunctie getSuperUserId() op null*.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
source-git-commit: 9d39b1045099a71d23f25ad1ef4932f78b1f33f0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804: Het bewerken van een klant die is gekoppeld aan een verwijderd bedrijf, resulteert in een fout

ACSD-60804 herstelt de flard de kwestie waar het uitgeven van een klant verbonden aan een geschrapt bedrijf een fout *Vraag aan een lidfunctie getSuperUserId () op ongeldig* veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-60804. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitgeven van een klant verbonden aan een geschrapt bedrijf veroorzaakt een fout *Vraag aan een lidfunctie getSuperUserId () op ongeldig*.

<u> Eerste vereisten:</u>:

Adobe Commerce B2B-modules installeren en inschakelen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]** .
1. Ga naar **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]** .
1. Meld u aan bij `mysql` voor de instantie.
1. Schrap het bedrijf waar `entity_id` = *1*.
1. Ga naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** .
1. Bewerk de klant die automatisch is gemaakt toen u het bedrijf maakte.

<u> Verwachte resultaten </u>:

De klant wordt bewerkt zonder dat een uitzonderingsfout optreedt.

<u> Ware resultaten </u>:

Een fout komt voor: *Vraag aan een lidfunctie getSuperUserId () op ongeldig* als geen bedrijf met de klant wordt geassocieerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

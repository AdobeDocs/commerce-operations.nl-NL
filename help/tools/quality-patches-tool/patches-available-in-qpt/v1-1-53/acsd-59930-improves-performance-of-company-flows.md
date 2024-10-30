---
title: "ACSD-59930: Verbetert de prestaties van de bedrijfsstromen"
description: Pas de ACSD-59930-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een *Timeout*-fout wordt weergegeven in het beheerpaneel wanneer u een bedrijf maakt, opslaat of verwijdert met een beheerder met een *1000+*-adres in het adresboek.
feature: Customers, B2B
role: Admin, Developer
source-git-commit: bff014ede6ab7e8e72700814bb4edda2e733557a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: verbetert de prestaties van de bedrijfsstromen

ACSD-59930 flard lost de kwestie op waar de a *fout van de Onderbreking* in het admin paneel wanneer het creëren van, het bewaren van, of het schrappen van een bedrijf met admin wordt getoond die *1000+* adressen in het adresboek heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-59930. Dit probleem wordt volgens de planning opgelost in Adobe Commerce B2B-1.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verbetert de prestaties van het bedrijf creeer, sparen, en schrapt stromen.

<u> Eerste vereisten:</u>:

Adobe Commerce B2B-modules installeren en inschakelen.

<u> Stappen om </u> te reproduceren:

1. Creeer een klant met *1000+* adressen in *[!UICONTROL Address Book]*.
1. Maak een bedrijf en gebruik de klant hierboven als beheerder.
1. Sla het bedrijf op.

<u> Verwachte resultaten </u>:

Het bedrijf is gemaakt zonder time-outfouten weer te geven.

<u> Ware resultaten </u>:

Er wordt een time-outfout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
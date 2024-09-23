---
title: 'ACSD-50512: Fout bij het bijwerken van de begindatum voor een downloadbare product-staging-update'
description: Pas de ACSD-51892-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen wanneer de fout *De downloadbare koppeling is niet gerelateerd aan het product.Controleer de koppeling en probeer het opnieuw*, en dit gebeurt bij het bijwerken van de begindatum voor een downloadbare product-staging-update.
feature: Products, Staging
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-50512: Fout bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing

Het ACSD-50512 flard bevestigt de kwestie waar de fout *de downloadbare verbinding niet met het product verwant is. Verifieer de verbinding en probeer opnieuw*, komt wanneer het bijwerken van de begindatum voor een downloadbare product opvoerende update voor. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51502. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *de downloadbare verbinding is verwant met het product. Verifieer de verbinding en probeer opnieuw*, komt wanneer het bijwerken van de begindatum voor een downloadbare product opvoerende update voor.

<u> Stappen om </u> te reproduceren:

1. Creeer een downloadbaar product, met *downloadbare verbindingen* en *steekproefverbindingen*.
1. Maak een geplande update voor hetzelfde product en sla het product op.
1. Bewerk de vooraf geconfigureerde geplande update (vanuit stap 2) en wijzig de begindatum.
1. Sla de geplande update op.

<u> Verwachte resultaten </u>:

De wijzigingen in de geplande update worden opgeslagen.

<u> Ware resultaten </u>:

U krijgt de fout: *de downloadbare verbinding is niet verwant met het product. Verifieer verbinding en probeer opnieuw*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

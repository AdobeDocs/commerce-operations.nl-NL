---
title: 'MDVA-39713: de gebruiker kan de begintijd van de actieve geplande update bewerken'
description: De patch MDVA-39713 verhelpt het probleem waarbij een gebruiker de begintijd van een actieve geplande update kan bewerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-39713. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: de gebruiker kan de begintijd van de actieve geplande update bewerken

De patch MDVA-39713 verhelpt het probleem waarbij een gebruiker de begintijd van een actieve geplande update kan bewerken. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-39713. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan de begintijd voor een actieve geplande update bewerken.

<u> Stappen om </u> te reproduceren:

1. Nieuwe CMS-pagina&#39;s maken.
1. Selecteer **Nieuwe Update van het Programma** en plaats de **Datum van het Begin** aan huidige +1 minuut.
1. Activeer de Geplande Update door het bevel `bin/magento cron:run --group=staging` in lokale milieu in werking te stellen. Wacht een paar minuten en controleer of het schema actief is.
1. Zodra het programma actief is, vernieuw de pagina.
1. Klik **Mening/geef** in de Geplande sectie van Veranderingen uit.
1. Bewerk de tijd door +2 minuten toe te voegen en sla de wijziging op.
1. Sla de CMS-pagina op.
1. Voer opnieuw de volgende opdracht uit: `bin/magento cron:run --group=staging` .
1. Klik **Mening/geef** van de Geplande Update uit.

<u> Verwachte resultaten </u>:

De gebruiker kan de begintijd voor een actieve geplande update niet bewerken.

<u> Ware resultaten </u>:

De gebruiker krijgt een fout zoals *Punt (Magento\Cms\Model\Page) met zelfde identiteitskaart &quot;11&quot;bestaat reeds.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

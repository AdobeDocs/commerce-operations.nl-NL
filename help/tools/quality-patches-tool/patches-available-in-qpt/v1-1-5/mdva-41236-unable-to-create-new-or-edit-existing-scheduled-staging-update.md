---
title: 'MDVA-41236: Kan geen nieuwe geplande updates maken of bewerken voor product'
description: De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de "Einddatum" eerder is verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236: Kan geen nieuwe geplande updates voor het product maken of bewerken

De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de &quot;Einddatum&quot; eerder is verwijderd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen geen nieuwe schema&#39;s maken of bestaande schema&#39;s voor producten bewerken als de &quot;Einddatum&quot; eerder is verwijderd.

<u> Stappen om </u> te reproduceren:

1. Creeer een product met de Status die aan *wordt geplaatst onbruikbaar maken*.
1. Voeg een geplande update toe om dit product in te schakelen.
   * Voeg toekomstige begin- en einddatums toe.
1. Bewerk de geplande update door de **Datum van het Eind** te verwijderen.
1. Bewerk opnieuw het programma en probeer om een **Datum van het Eind** toe te voegen. Er treedt een fout op.
1. Vernieuw de pagina en ga opnieuw naar **Geplande Update** uitgeven.
1. Klik **verwijderen uit update** > **schrapt de update**.
1. De geplande update wordt nu niet weergegeven boven op de productbewerkingspagina.
1. Maak een nieuwe geplande update die de vorige duur overlapt.

<u> Verwachte resultaten </u>:

* Er is geen fout in stap 4. De beheerder kan de geplande update zonder enige fout bijwerken omdat het schema nog niet actief is.
* De beheerder kan de vorige update verwijderen en een nieuwe update maken.

<u> Ware resultaten </u>:

Gebruikers krijgen het volgende foutbericht:

*fout: De toekomstige Update bestaat reeds in deze tijdwaaier. Stel een ander bereik in en probeer het opnieuw.*


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) sectie.

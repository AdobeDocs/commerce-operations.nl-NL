---
title: 'MDVA-39229: Fout na het bijwerken van de regel van de Catalogus het Staging update begintijd'
description: De patch MDVA-39229 verhelpt het probleem waarbij gebruikers een fout krijgen na het bijwerken van de begintijd van de update voor het stapelen van catalogusregels. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-39229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229: Fout na het bijwerken van de regel van de Catalogus het Staging update begintijd

De patch MDVA-39229 verhelpt het probleem waarbij gebruikers een fout krijgen na het bijwerken van de begintijd van de update voor het stapelen van catalogusregels. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-39229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout na het bijwerken van de begintijd van de update voor het instellen van catalogusregels.

<u> Stappen om </u> te reproduceren:

1. Maak een regel voor catalogusprijzen.
1. Maak en voer een eventuele testupdate voor het trapsgewijs opvoeren uit.
1. Voer de query uit en controleer of de vlag Staging is gemaakt.


   `select * from flag;`


1. Maak een nieuwe Staging-update die na vijf minuten start.
1. Open **Inhoud** > **het Opvoeren** > **Dashboard** > **Nieuwe Update** en vertragen de begintijd door één minuut.
1. Wacht zes minuten.
1. Uitsnijden uitvoeren.

<u> Verwachte resultaten </u>:

De begintijd van de update wordt gewijzigd en de update wordt toegepast. De oude update wordt verwijderd uit de tabel `staging_update` .

<u> Ware resultaten </u>:

Gebruikers krijgen de volgende fout:

*report.ERROR: Het opvoeren_synchronize_entities_period van de Baan van de Kroon heeft een fout: De actieve update kan niet worden geschrapt.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) sectie.

---
title: 'ACSD-47875: kan geen product aan winkelwagentje toevoegen voor weergavebereik met voorraadbeheer'
description: Pas de ACSD-47875-patch toe om het Adobe Commerce-probleem op te lossen waarbij een product niet vanuit Admin aan een klantenkar kan worden toegevoegd voor een bepaald weergavebereik in de winkel met voorraadbeheer.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875: kan geen product aan winkelwagentje toevoegen voor weergavebereik met voorraadbeheer

De ACSD-47875-patch verhelpt het probleem dat een product niet kan worden toegevoegd aan een klankkaart van de beheerder voor een bepaald weergavebereik van de winkel met voorraadbeheer. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-47875. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers kunnen een product niet aan een winkelwagentje toevoegen met de functie **[!UICONTROL Manage Shopping Cart]** in Admin voor een bepaald weergavebereik met MSI geïnstalleerd.

<u> Eerste vereisten </u>:

[!DNL Adobe Commerce Inventory Management (MSI)] -modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een website, een winkel en een winkelweergave.
1. Creeer een extra bron buiten *Gebrek*.
1. Maak een nieuwe voorraad en wijs deze toe aan de nieuwe website en de nieuwe bron.
1. Maak een nieuwe klant voor de nieuwe website.
1. Alleen een product aan de nieuwe website toewijzen; toewijzing van de standaardwebsite ongedaan maken.

   * Wijs de nieuwe bron toe en plaats Aantal *boven 0* voor de nieuwe bron en *0* voor de standaardbron.

1. Ga naar de pagina **[!UICONTROL Customer Edit]** in Admin. Klik op **[!UICONTROL Manage Shopping Cart]**.
1. Wijzig het bereik van de winkelweergave in de nieuwe winkelweergave.
1. Ga naar de sectie **[!UICONTROL Products]** en zoek naar het product.
1. Selecteer het product en klik op **[!UICONTROL Add selections to my cart]** .

<u> Verwachte resultaten </u>:

Het product wordt toegevoegd aan het winkelwagentje.

<u> Ware resultaten </u>:

* De volgende fout wordt geworpen: *Product dat u probeert toe te voegen is niet beschikbaar.*
* Het product wordt niet toegevoegd aan het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

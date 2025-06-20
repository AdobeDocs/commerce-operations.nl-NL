---
title: 'MDVA-39163: Verzendmethoden niet beschikbaar voor nieuwe geregistreerde gebruikers met producten van gastsessies'
description: Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 is geïnstalleerd. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163: Verzendmethoden niet beschikbaar voor nieuwe geregistreerde gebruikers met producten van gastsessies

Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 geïnstalleerd is. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verzendmethoden zijn niet beschikbaar wanneer de nieuwe gebruiker is geregistreerd en producten in de winkelwagen zijn afkomstig van de gastsessie.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Admin** > **Opslag** > **Configuratie** > **Verkoop** > **Methoden van de Levering**. Laat slechts het **Vlakke Tarief** verschepen methode toe en maak alles anders onbruikbaar.
1. In het **Vaste Tarief** verschepen methode, selecteer de **Specifieke** landoptie beschikbaar in het **Schip aan Toepasselijke Landen** plaatsen en selecteer één land van de lijst (b.v., Verenigde Staten).
1. Ga naar **Admin** > **Opslag** > **Configuratie** > **Klant** > **de Configuratie van de Klant** en de reeks **vereist E-mailbevestiging** aan _ja_.
1. Creeer een nieuw E-mailMalplaatje in **Admin** > **de Marketing** > **E-mailMalplaatjes** en ladings `Footer (magento/luma)` malplaatje en vervang de malplaatjeinhoud met een blok van CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Ga naar **Admin** > **Inhoud** > **Ontwerp** > **Configuratie** en selecteer het thema dat op uw voorste website betrekking heeft. Stel de &quot;Voettekstsjabloon&quot; in op de nieuwe e-mailsjabloon die u maakt.
1. Ga naar de voorkant en voeg een product aan de kar toe.
1. Maak een klant; u ontvangt een e-mail ter bevestiging van het e-mailadres. Klik op de koppeling Verificatie. U wordt aangemeld bij de website.
1. Ga naar **Mijn Rekening** en voeg een adres toe. Stel het adresland in op het verzendland dat u eerder hebt ingesteld in de beheerconfiguratie.
1. Ga naar Afrekenen.

<u> Verwachte resultaten </u>:

De verzendmethode is beschikbaar omdat de klant een adres heeft dat compatibel is met het verzendende land.

<u> Ware resultaten </u>:

Verzendmethode is niet beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

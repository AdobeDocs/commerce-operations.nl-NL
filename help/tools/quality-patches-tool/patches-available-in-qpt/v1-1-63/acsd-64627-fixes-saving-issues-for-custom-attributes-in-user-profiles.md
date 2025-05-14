---
title: 'ACSD-64627: Aangepaste klantkenmerken kunnen niet worden opgeslagen in [!UICONTROL Company Structure]'
description: Pas de ACSD-64627-patch toe om het Adobe Commerce-probleem op te lossen, waarbij aangepaste klantkenmerken niet kunnen worden opgeslagen wanneer gebruikers binnen [!UICONTROL Company Structure] worden toegevoegd of bewerkt.
feature: B2B
role: Admin, Developer
source-git-commit: 96e20dbe336789794462232928648a22f489c88f
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-64627: Aangepaste klantkenmerken kunnen niet worden opgeslagen in [!UICONTROL Company Structure]

De ACSD-64627-patch verhelpt het probleem dat aangepaste klantkenmerken niet kunnen worden opgeslagen wanneer gebruikers binnen de **[!UICONTROL Company Structure]** -pagina worden toegevoegd of bewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 wordt geïnstalleerd. De patch-id is ACSD-64627. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepaste klantkenmerken worden niet opgeslagen wanneer u gebruikers toevoegt of bewerkt op de **[!UICONTROL Company Structure]** -pagina.

<u> Stappen om </u> te reproduceren:

1. Installeer een Adobe Commerce-instantie met ingeschakelde B2B-functies.
1. Creeer een nieuw klantenattribuut genoemd *custom_upload* met **[!UICONTROL Input Type]** plaatste aan *[!UICONTROL File (attachment)]*.
1. Creeer een ander klantenattribuut genoemd *image_gehechtheid* met **[!UICONTROL Input Type]** plaatste aan *[!UICONTROL Image File]*.
1. Plaats **[!UICONTROL Show on Storefront]** aan *ja* om beide attributen zichtbaar op storefront te maken. Alle formulieren selecteren:
   * Klantenregistratie
   * Klantaccount bewerken
   * Afhandeling beheerder
1. Een nieuw bedrijf maken en activeren.
1. Meld u aan bij de winkel als bedrijfsbeheerder.
1. Navigeer naar **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** of **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]** .
1. Klik op **[!UICONTROL Add New User]**.
1. Klik **[!UICONTROL Upload]** voor het *custom_upload* attribuut.
1. Klik **[!UICONTROL Select file]** voor het *image_gehechtheid* attribuut.

<u> Verwachte resultaten </u>:

Bestandsverkenner wordt voor beide kenmerken geopend. Bij het opslaan worden waarden opgeslagen en worden bestanden geüpload.

<u> Ware resultaten </u>:

De knoppen reageren niet. Er wordt geen bestandsverkenner geopend of er worden geen gegevens opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

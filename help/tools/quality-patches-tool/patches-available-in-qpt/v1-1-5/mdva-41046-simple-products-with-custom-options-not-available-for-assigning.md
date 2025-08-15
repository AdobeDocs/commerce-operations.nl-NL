---
title: 'MDVA-41046: eenvoudige producten met aangepaste opties die niet beschikbaar zijn voor toewijzing'
description: De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046: eenvoudige producten met aangepaste opties die niet beschikbaar zijn voor toewijzing

De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Eenvoudige producten met aangepaste opties zijn niet beschikbaar voor toewijzing aan configureerbaar/gegroepeerd product.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met aanpasbare opties en stel een waarde in voor het configureerbare kenmerk.
   * Het gebruik *Kleur* als configureerbare attributen, en selecteert *Geel* als kleurenwaarde.
1. Sla het eenvoudige product op.
1. Ga nu naar de aanpasbare productpagina maken.
1. Ga door de &quot;creeer configuratie&quot;tovenaar en zorg ervoor om *Geel* als attributenkleur te selecteren.
1. Als u het configureerbare product niet wilt opslaan, selecteert u de optie &quot;Kies een ander product&quot; in het vervolgkeuzemenu Selecteren.
1. Hiermee wordt een productraster geopend dat met geel kleurkenmerk is gefilterd. Selecteer nu het eenvoudige product dat eerder met aanpasbare opties werd gecreeerd.
1. Sla het configureerbare product op.

<u> Verwachte resultaten </u>:

Het eenvoudige product met aangepaste opties is beschikbaar voor toewijzing (zichtbaar in het raster) in stap 6.

<u> Ware resultaten </u>:

De sectie Configuratie is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.

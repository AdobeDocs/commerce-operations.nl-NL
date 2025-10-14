---
title: 'MDVA-33606: Gebruikers krijgen een foutmelding wanneer ze CMS-pagina opslaan die aan de hiërarchie is toegewezen'
description: De MDVA-33606-patch lost het probleem op waarbij de gebruikers een fout *Unieke schending van de beperking aangetroffen* krijgen bij het opslaan van een CMS-pagina die is toegewezen aan de hiërarchische structuur. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 is geïnstalleerd. De patch-id is MDVA-33606. De kwestie is opgelost in Adobe Commerce 2.4.3.
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606: Gebruikers krijgen een foutmelding wanneer ze CMS-pagina opslaan die aan de hiërarchie is toegewezen

Het flard MDVA-33606 lost de kwestie op waar de gebruikers *Unieke gevonden beperkingsschending* fout krijgen wanneer het opslaan van een pagina van CMS die aan hiërarchieboom wordt toegewezen. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 geïnstalleerd is. De patch-id is MDVA-33606. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het proberen om een pagina van CMS te bewaren die aan hiërarchieboom wordt toegewezen, krijgen de gebruikers het volgende foutenbericht: *Unieke gevonden beperkingsschending*.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe CMS-pagina. Stel het bereik in op Alle winkelweergaven. Dit is je CMS-pagina 1.
1. Maak een nieuwe winkelweergave. Dit is je winkelweergave 2.
1. Ga naar **Inhoud** > **Hiërarchie** > toevoegen CMS Pagina 1 aan hiërarchieboom.
1. Wijzig het bereik in Winkelweergave 2.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Wijzig nu het bereik in Standaardwinkelweergave.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Ga naar **Inhoud** > **Pagina&#39;s** > **voeg Nieuwe Pagina** toe.
   * Titreer de pagina als pagina 2.
   * In de Pagina in de sectie van Websites, wijs aan Alle Mening van de Opslag en beide opslagmeningen (de Mening van de StandaardOpslag en Mening 2 van de Opslag) toe en klik **sparen Pagina**.
1. Open op de CMS-bewerkingspagina het tabblad Hiërarchie.
   * Wijs Pagina 2 toe aan de knoop van de Mening 2 van de Opslag, Standaardknoop, en Al knoop Websites.

<u> Verwachte resultaten </u>:

U kunt de CMS-pagina zonder fouten toewijzen aan alle drie knooppunten.

<u> Ware resultaten </u>:

U krijgt de volgende fout: *Unieke gevonden beperkingsschending*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.

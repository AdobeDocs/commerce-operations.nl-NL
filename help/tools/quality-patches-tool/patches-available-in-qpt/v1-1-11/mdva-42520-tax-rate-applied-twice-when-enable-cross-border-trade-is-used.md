---
title: 'MDVA-42520: tweemaal toegepast belastingtarief bij gebruik van "Enable Cross Border Trade"'
description: De MDVA-42520-patch voorziet in de mogelijkheid dat het belastingtarief tweemaal wordt toegepast wanneer het **Grensoverschrijdende handel inschakelen* wordt gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-42520: tweemaal toegepast belastingtarief bij gebruik van &quot;Enable Cross Border Trade&quot;

Het flard MDVA-42520 bevestigt de kwestie waar het belastingtarief tweemaal wordt toegepast wanneer **grensoverschrijdende handel** toelaat wordt gebruikt. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 geïnstalleerd is. De patch-id is MDVA-42520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het belastingtarief wordt toegepast tweemaal wanneer **laat Grensoverschrijdende Handel** toe wordt gebruikt.

<u> Stappen om </u> te reproduceren:

1. Laat **Bedrijf** toe, **Gedeelde Catalogus**, en **Citaat**
1. Configureer belastingen volgens de schermafbeelding. Zorg ervoor u **Grensoverschrijdende Handel** toelaat.

   ![&#x200B; pagina van de de configuratiemontages van de Belasting die grensoverschrijdende handelsopties en tariefberekeningen tonen &#x200B;](/help/assets/tools/tax_settings_1.png){width="700"}

1. Een belastingtarief voor Duitsland instellen (10%).
1. Maak een belastingregel om het belastingtarief toe te passen.
1. Een bedrijf en een aangepaste gedeelde catalogus maken.
1. Maak een product met een prijs van 100 en neem het op in de aangepaste gedeelde catalogus met een prijskorting van 20%.
1. Een klant met een Duits adres maken en dit aan het bedrijf toewijzen
1. Voeg tien producten toe aan de kaart als klant.
1. Ga naar het winkelwagentje en vraag een prijsopgave.
1. Open dit citaat op de achtergrond en probeer om een extra korting van 10% toe te voegen.

<u> Verwachte resultaten </u>:

Subtotaal prijsopgave (inclusief btw) en Eindtotaal prijsopgave (inclusief btw) = $720

<u> Ware resultaten </u>:

Subtotaal prijsopgave (inclusief btw) en Eindtotaal prijsopgave (inclusief btw) = $ 649,50.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

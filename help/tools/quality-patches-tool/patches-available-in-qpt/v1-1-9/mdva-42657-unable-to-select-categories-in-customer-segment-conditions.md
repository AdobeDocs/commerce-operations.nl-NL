---
title: '42657: Kan geen categorieën selecteren in de condities van het klantensegment'
description: Met de MDVA-42657-patch wordt het probleem opgelost waarbij de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42657. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 42657: Kan geen categorieën selecteren in de condities van het klantensegment

Met de MDVA-42657-patch wordt het probleem opgelost waarbij de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 geïnstalleerd is. De patch-id is MDVA-42657. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan geen categorieën selecteren in de segmentvoorwaarden van de klant.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Klanten** > **Segmenten**.
1. Maak een nieuw segment.
1. Ga naar het pas gecreëerde segment en klik **Voorwaarden** in de linkerzijnavigatie.
1. Klik op het groene plusteken.
1. Selecteer Productgeschiedenis onder Producten.
1. Wijzig &#39;views&#39; in &#39;ordered&#39;.
1. &quot;ALL&quot; wijzigen in &quot;ANY&quot;.
1. Klik op het geneste groene plusteken en selecteer Categorie.
1. Klik op **..** en klik vervolgens op het pictogram van de kiezer (links van het vinkje).
1. Open de browser Dev Console.
1. Controleer de selectievakjes voor om het even welke/veelvoudige categorieën en neem nota van de fout javascript die in de console wordt geworpen.
1. Klik **sparen** knoop.
1. Navigeer terug naar de voorwaarde en controleer of de geselecteerde categorieën zijn opgeslagen.

<u> Verwachte resultaten </u>:

De geselecteerde categorieën worden opgeslagen en geselecteerd wanneer u de segmentvoorwaarden weergeeft/bewerkt.

<u> Ware resultaten </u>:

De geselecteerde categorieën ontbreken en zijn niet goed opgeslagen. U krijgt de volgende fout in console:

```text
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

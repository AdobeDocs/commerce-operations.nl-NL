---
title: 'ACSD-56515: Admin with website-level permissions cannot edit [!UICONTROL Dynamic Block]'
description: Pas de ACSD-56515-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de beheerder met bevoegdheden op websiteniveau het [!UICONTROL Dynamic Block] niet kan toevoegen of bewerken.
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-56515: Admin with website-level permissions cannot edit [!UICONTROL Dynamic Block]

De ACSD-56515-patch verhelpt het probleem waarbij de beheerder met bevoegdheden op websiteniveau de [!UICONTROL Dynamic Block] niet kan toevoegen of bewerken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56515. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder met bevoegdheden op websiteniveau kan [!UICONTROL Dynamic Block] niet toevoegen of bewerken.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire website met opslag en voorvertoning.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** en maak een gebruikersrol die beperkt is tot het secundaire websitebereik met alle beschikbare bronnen.
1. Maak een beheerder met de hierboven gemaakte rol.
1. Meld u aan met de beperkte beheerder en maak een [!UICONTROL Dynamic Block] .

<u> Verwachte resultaten </u>:

De beheerder met beperkingen voor de website kan een [!UICONTROL Dynamic Block] maken.

<u> Ware resultaten </u>:

U krijgt de volgende fout: *Meer toestemmingen zijn nodig om dit punt* te bekijken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

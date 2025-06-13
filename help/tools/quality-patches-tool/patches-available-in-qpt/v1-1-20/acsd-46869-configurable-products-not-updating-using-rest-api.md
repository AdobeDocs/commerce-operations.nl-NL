---
title: 'ACSD-46869: configureerbare producten die niet worden bijgewerkt met REST API bij het uitchecken'
description: De ACSD-46869-patch verhelpt het probleem waarbij de configureerbare producten niet worden bijgewerkt met behulp van REST API bij het uitchecken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46869. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: configureerbare producten die niet worden bijgewerkt met REST API bij het uitchecken

De ACSD-46869-patch verhelpt het probleem waarbij configureerbare producten niet worden bijgewerkt met behulp van REST API bij het uitchecken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 wordt geïnstalleerd. De patch-id is ACSD-46869. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren als het flard met uw versie van Adobe Commerce compatibel is, werk het `magento/quality-patches` pakket aan de recentste versie bij en controleer de verenigbaarheid op de [[!DNL QPT]  landende pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Configureerbare producten worden niet bijgewerkt met REST API tijdens het uitchecken.

<u> Stappen om </u> te reproduceren:

1. Maak een configureerbaar product met kleur- en formaatkenmerken.
1. Selecteer **[!UICONTROL Options]** en voeg het product aan de kar toe.
1. Ga naar **[!UICONTROL Checkout]**, werk de grootte meerdere keren bij behalve hoeveelheid, en controleer het verzoek en de reactie.
1. U krijgt de volgende reactie wanneer u de grootte bijwerkt.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u> Verwachte resultaten </u>:

De waarde wordt bijgewerkt op basis van de wijzigingen.

<u> Ware resultaten </u>:

`option_value` wordt niet bijgewerkt, dus wanneer de volgorde wordt geplaatst, heeft deze de waarde voor de oude grootte.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tools] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

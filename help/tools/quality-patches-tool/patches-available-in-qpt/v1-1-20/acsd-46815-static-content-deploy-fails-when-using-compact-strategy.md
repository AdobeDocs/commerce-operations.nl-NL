---
title: 'ACSD-46815: Statische content implementeert werkt niet volgens compacte strategie'
description: Pas de ACSD-46815-patch toe om het Adobe Commerce-probleem op te lossen waarbij de implementatie van statische inhoud mislukt bij gebruik van een compacte strategie.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-46815: De statische inhoud stelt ontbreekt op wanneer het gebruiken van compacte strategie

De ACSD-46815-patch verhelpt het probleem waarbij de implementatie van statische inhoud mislukt wanneer de compacte strategie wordt gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 wordt geïnstalleerd. De patch-id is ACSD-46815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De statische plaatsing van de inhoud ontbreekt wanneer het opstellen met een compacte strategie.

<u> Stappen om </u> te reproduceren:

1. Implementeer de statische inhoud met een compacte strategie door de volgende opdracht uit te voeren:

```shell
bin/magento setup:static-content:deploy -f -s compact
```

<u> Verwachte resultaten </u>:

De statische plaatsing van de inhoud wordt voltooid zonder enige fout.

<u> Ware resultaten </u>:

De statische plaatsing van de inhoud ontbreekt met een compacte strategie. De volgende fout komt tijdens het plaatsingsproces voor: *de inhoud van /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css dossier kan niet worden gelezen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

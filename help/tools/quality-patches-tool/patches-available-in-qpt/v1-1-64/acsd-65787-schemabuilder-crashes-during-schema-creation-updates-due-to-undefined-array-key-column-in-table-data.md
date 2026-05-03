---
title: 'ACSD-65787: SchemaBuilder crasht tijdens het maken of bijwerken van het schema als gevolg van een niet-gedefinieerde arraysleutel ''column'' in tabelgegevens'
description: Pas de ACSD-65787-patch toe om het Adobe Commerce-probleem op te lossen waarbij de SchemaBuilder-klasse vastloopt tijdens het maken van een schema of updates vanwege een niet-gedefinieerde arraysleutel 'column' bij het verwerken van tabelgegevens.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 93bf12af83dbaf37c51a9730f2d2a6089000b3f0
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` crasht tijdens het maken of bijwerken van het schema als gevolg van niet-gedefinieerde &#39;kolom&#39; van de arraysleutel in tabelgegevens

De ACSD-65787-patch verhelpt het probleem waarbij de `SchemaBuilder` -klasse vastloopt tijdens het maken van het schema of tijdens updates vanwege een niet-gedefinieerde arraysleutel &#39;column&#39; bij het verwerken van tabelgegevens. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65787. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `SchemaBuilder` -klasse loopt vast tijdens het maken van het schema of tijdens updates vanwege een niet-gedefinieerde arraysleutel &#39;column&#39; bij het verwerken van tabelgegevens.

<u> Stappen om </u> te reproduceren:

1. Voer het volgende bevel uit:

```shell
bin/magento setup:upgrade
```

<u> Verwachte resultaten </u>:

Geen fouten.

<u> Ware resultaten </u>:

```text
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

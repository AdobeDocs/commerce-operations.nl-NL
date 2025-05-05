---
title: 'ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen'
description: Pas de ACSD-51892-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen, waarbij configuratiebestanden tijdens de implementatie meerdere keren worden geladen.
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen

De ACSD-51892-patch verhelpt het prestatieprobleem dat ontstaat wanneer de `app/etc/env.php` - en `app/etc/config.php` -bestanden worden geladen telkens wanneer implementatieconfiguratiewaarden binnen één aanvraag worden benaderd. Door de te grote aflezing van bestanden wordt het systeem onder druk gezet, wat de algehele prestaties nadelig beïnvloedt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51892. De kwestie is opgelost in Adobe Commerce 2.4.6-p2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een prestatieprobleem waarbij de configuratiebestanden meerdere keren worden geladen.

<u> Stappen om </u> te reproduceren:

1. Voer implementatie of upgrade uit naar Adobe Commerce 2.4.6 of hoger.
1. Controleer tijdens de implementatie de bestandssysteemlogboeken op toegang tot `app/etc/env.php` - en `app/etc/config.php` -bestanden.

<u> Verwachte resultaten </u>:

Implementatie is voltooid binnen de normale tijdsperiode.

<u> Ware resultaten </u>:

* De servers hebben moeite om te reageren op opdrachten die u invoert. Dit resulteert in *Fout 503 eerste byteonderbreking* wanneer het toegang tot van de website.
* Er zijn meerdere vermeldingen in logbestanden die toegang hebben tot `app/etc/env.php` - en `app/etc/config.php` -bestanden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

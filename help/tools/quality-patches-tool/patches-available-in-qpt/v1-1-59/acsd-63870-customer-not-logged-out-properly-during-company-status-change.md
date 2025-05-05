---
title: 'ACSD-63870: Klant wordt niet correct afgemeld tijdens de statuswijziging van het bedrijf'
description: Pas de ACSD-63870-patch toe om het Adobe Commerce-probleem op te lossen waarbij een bedrijfsklant niet correct wordt afgemeld wanneer de status van het bedrijf tijdens een actieve klantensessie verandert.
feature: Customers, B2B, Companies
role: Admin, Developer
source-git-commit: 3544eaef7812524a098e851ac8a2c140f33f7668
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# ACSD-63870: Klant wordt niet correct afgemeld tijdens de statuswijziging van het bedrijf

De ACSD-63870-patch lost het probleem op waarbij een bedrijfsklant niet correct wordt afgemeld wanneer de status van het bedrijf tijdens een actieve klantensessie verandert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-63870. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afmeldingsfout van de klant wanneer de bedrijfsstatus tijdens een actieve klantensessie wordt gewijzigd.

<u> Stappen om </u> te reproduceren:

1. B2B-functionaliteit inschakelen.
1. Maak een eenvoudig product.
1. Creeer een nieuw bedrijf en merk het als *Actief*.
1. Meld u aan als de gebruiker van het bedrijf en voeg een product toe aan het winkelwagentje.
1. Ga door met het uitchecken tot de stap [!UICONTROL Shipping Address] . Voer het adres niet in.
1. Ga naar admin en verander de bedrijfstatus in *In afwachting van Goedkeuring*.
1. Ga terug naar de frontend en vul het verzendadres in.

<u> Verwachte resultaten </u>:

De klant is afgemeld.

<u> Ware resultaten </u>:

* De gebruikers krijgen het *Iets ging fout* verkeerd.
* `var/log/exception.log` bevat:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.


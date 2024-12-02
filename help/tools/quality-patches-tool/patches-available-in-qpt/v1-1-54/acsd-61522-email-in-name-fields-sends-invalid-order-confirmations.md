---
title: 'ACSD-61522: E-mailadressen in *Voornaam en Achternaam* verzenden ongeldige orderbevestigingen'
description: Pas ACSD-61522 flard toe om de kwestie van Adobe Commerce te bevestigen waar het mogelijk is om e-mailadressen in de gebieden *[!UICONTROL First Name] * en * [!UICONTROL Last Name] * van een gastklant in te gaan, leidend tot ongeldige de bevestigingse-mails die van de ordbevestiging worden verzonden.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
source-git-commit: a5dda25e502889ee0a23e99b412aeeb863de452c
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: De e-mailadressen in *Voornaam en de gebieden van de Achternaam* verzenden ongeldige ordesbevestigingen

De ACSD-61522-patch verhelpt het probleem waarbij e-mailadressen kunnen worden ingevoerd in de velden *[!UICONTROL First Name]* en *[!UICONTROL Last Name]* van een gastklant, zodat een e-mail met een ongeldige orderbevestiging kan worden verzonden. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61522. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p9

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Op dit systeem kunnen e-mailadressen worden ingevoerd in de velden *[!UICONTROL First Name]* en *[!UICONTROL Last Name]* van een gast-klant. Dit leidt tot het verzenden van e-mails ter bevestiging van een ongeldige bestelling.

<u> Stappen om </u> te reproduceren:

1. Voeg om het even welk product aan de kar als gastklant toe.
1. Ga naar **[!UICONTROL Checkout]** .
1. Vul het *[!UICONTROL Email Address]* gebied met *test1@example.com*.
1. Vul het veld *[!UICONTROL First Name]* met *<test2@example.com>* .
1. Vul *[!UICONTROL Last Name]* met *<test3@example.com>* .
1. Vul andere vereiste velden in.
1. Plaats de bestelling.

<u> Verwachte resultaten </u>:

Het is niet mogelijk e-mailadressen te gebruiken in de velden *[!UICONTROL First Name]* en *[!UICONTROL Last Name]* .

<u> Ware resultaten </u>:

1. De volgorde wordt geplaatst.
1. *[!UICONTROL First Name]* - en *[!UICONTROL Last Name]* -velden worden opgeslagen als ingevoerde velden.
1. Bevestigingse-mails voor bestellingen worden naar alle drie e-mails verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

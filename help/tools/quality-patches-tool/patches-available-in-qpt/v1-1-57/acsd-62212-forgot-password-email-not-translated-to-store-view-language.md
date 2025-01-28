---
title: 'ACSD-62212: [!UICONTROL Forgot Password] e-mail niet vertaald naar weergavetaal van winkel'
description: Pas de ACSD-62212-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de inhoud van het *[!UICONTROL Forgot Password]*-e-mailbericht niet naar de taal van de winkelweergave wordt vertaald.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
source-git-commit: 8f39f7838d5c98a1dcc584edf766393012ec8820
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]* e-mail niet vertaald naar weergavetaal van winkel

De ACSD-62212-patch verhelpt het probleem dat de inhoud van het e-mailbericht van *[!UICONTROL Forgot Password]* niet naar de taal van de winkelweergave wordt vertaald. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62212. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het opnieuw instellen van het wachtwoord via GraphQL in een andere winkelweergave dan de geregistreerde, komt de koppeling Wachtwoord voor opnieuw instellen niet overeen met de winkelweergave van waaruit het is gestart.

<u> Stappen om </u> te reproduceren:

1. Maak een tweede winkelweergave onder de *[!UICONTROL Main Website Store]* .
1. Schakel *[!UICONTROL Locale]* over naar *[!UICONTROL French (France)]* in het weergavebereik van de secundaire opslagruimte.
1. Installeer het Franse taalpakket voor vertalingen.
1. Maak een klantenaccount.
1. Gebruik de volgende mutatie van GraphQL met *opslag* kopbal met de secundaire code van de opslagmening.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Controleer het e-mailbericht.

<u> Verwachte resultaten </u>:

* De taal van het onderwerp, de koppeling en de inhoud van de e-mail van de e-mail is consistent met de landinstelling van de winkelweergave.
* Het verzoek om het opnieuw instellen van het wachtwoord wordt verzonden van de opslag waar de rekening van de klant eigenlijk, ongeacht de opslagkopbal in het verzoek wordt geregistreerd.

<u> Ware resultaten </u>:

In de e-mail kan het volgende worden opgemerkt:

* De koppeling Wachtwoord opnieuw instellen heeft de &quot;standaard&quot; opslagcode.
* Het onderwerp is in het Engels.
* De inhoud is in het Frans.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

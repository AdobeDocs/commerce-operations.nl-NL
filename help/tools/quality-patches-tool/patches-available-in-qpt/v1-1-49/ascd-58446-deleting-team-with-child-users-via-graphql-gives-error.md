---
title: 'ACSD-5846: Het verwijderen van een team met onderliggende gebruikers of teams via GraphQL geeft een foutbericht zonder informatie'
description: Pas de ACSD-58446-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het verwijderen van een team met onderliggende gebruikers of teams via GraphQL een niet-informatief foutbericht retourneert dat niet overeenkomt met de gebruikersinterface.
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-5846: Het verwijderen van een team met onderliggende gebruikers of teams via GraphQL geeft een foutbericht zonder informatie

De ACSD-58446-patch verhelpt het Adobe Commerce-probleem waarbij als een team met onderliggende gebruikers of teams via GraphQL wordt verwijderd, een foutbericht wordt geretourneerd dat niet informatief is en niet overeenkomt met de gebruikersinterface. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58446. Het probleem wordt volgens de planning opgelost in Adobe Commerce B2B 1.5.1

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een team met onderliggende gebruikers of teams verwijdert via GraphQL, wordt een foutbericht geretourneerd dat niet informatief is en niet overeenkomt met de gebruikersinterface.

## Vereisten:

Adobe Commerce B2B-modules geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Schakel de functie *[!UICONTROL Company]* in.
1. Maak een nieuw bedrijfsaccount.
1. Meld u aan bij **[!UICONTROL Admin]** en activeer de bedrijfsaccount.
1. Controleer de e-mail en stel een wachtwoord in voor het nieuwe bedrijfsaccount.
1. Creeer een nieuw team voor het bedrijf.
1. Login als bedrijfgebruiker op de Storefront en voeg een nieuwe gebruiker voor het gecreeerde team toe.
1. Login aan **[!UICONTROL Admin]**, maak de bedrijfgebruiker onbruikbaar, en reeks *[!UICONTROL Customer Active]* = *Nr*
1. Verwijder het nieuwe team via GraphQL.

   ```graphql
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u> Verwachte resultaten </u>:

Er wordt een informatief foutbericht geretourneerd dat consistent is met de gebruikersinterface.

<u> Ware resultaten </u>:

Er wordt een algemeen intern foutbericht voor de server geretourneerd dat niet overeenkomt met de interface.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

---
title: 'ACSD-47027: langzame vraag B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  update'
description: Pas ACSD-47027 flard toe om de kwestie van Adobe Commerce te bevestigen waar er een langzame vraag B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  update is.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] bijwerken

De ACSD-47027-patch lost het probleem op waarbij de langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -update niet werkt zoals u had verwacht. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 wordt geïnstalleerd. De patch-id is ACSD-47027. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De langzame B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -update voor query werkt niet zoals verwacht.

<u> Eerste vereisten </u>:

Installeer de B2B-module.

<u> Stappen om </u> te reproduceren:

1. In Adobe Commerce Admin, ga **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** en reeks **[!UICONTROL Enable Company]** aan _ja_.
1. Ga naar de frontend en creeer een bedrijf.
1. Nadat u zich hebt aangemeld als bedrijfsgebruiker, gaat u naar **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** en voegt u een nieuwe rol toe.
1. Schakel [!UICONTROL dev] querylogboek in met `bin/magento dev:que:enab` .
1. Verzend nu de onderstaande aanvraag [!DNL GraphQL] (id is de [!UICONTROL base64] gecodeerde rol-id):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Controleer het querylogboek.
1. U ziet dat de bovenstaande query is uitgevoerd. Deze query wordt uitgevoerd in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` .

<u> Verwachte resultaten </u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` moet worden geoptimaliseerd om te voorkomen dat alle gegevens in de **[!UICONTROL company_permissions]** DB-tabel worden geladen.

<u> Ware resultaten </u>:

Adobe Commerce voert een query uit zonder filter. Als er een groot aantal records is, kost het veel tijd voor Adobe Commerce om de gegevensverzameling voor te bereiden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

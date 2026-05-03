---
title: 'ACSD-47004: BTW niet van toepassing op factuuradres zonder BTW-identificatienummer'
description: Pas de ACSD-47004-patch toe om het Adobe Commerce-probleem op te lossen dat BTW niet wordt geheven op een factuuradres zonder BTW-identificatienummer.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-47004: BTW niet van toepassing op factuuradres zonder BTW-identificatienummer

Met de ACSD-47004-patch is het probleem opgelost dat btw niet wordt toegepast op een factuuradres zonder BTW-identificatienummer. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-47004. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

BTW wordt niet toegepast op een factuuradres zonder BTW-identificatienummer.

<u> Stappen om </u> te reproduceren:

1. Open [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** en stel **[!UICONTROL Enable Automatic Assignment to Customer Group]** in op *[!UICONTROL Yes]* .
1. Stel verschillende groepen in voor BTW-ID-validaties. Bijvoorbeeld:

   ![&#x200B; de bevestiging van identiteitskaart van de BTW interface die configuratieopties voor belastingbevestiging toont &#x200B;](/help/assets/tools/vat-id-validations.png)

1. Registreer een nieuwe klant.
1. Voeg een nieuw standaardadres zonder BTW toe. Bijvoorbeeld:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Controleer of de groep van de klant [!UICONTROL General] blijft.
1. Bewerk dit adres en voeg een geldig BTW-nummer toe:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Controleer of de groep van de klant is gewijzigd in [!UICONTROL Retailer] .
1. Bewerk het adres en verwijder het BTW-nummer:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u> Verwachte resultaten </u>:

De klantengroep wordt automatisch gewijzigd in de standaardgroep [!UICONTROL General] .

<u> Ware resultaten </u>:

De klantengroep wordt niet automatisch gewijzigd in de standaardgroep [!UICONTROL General] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

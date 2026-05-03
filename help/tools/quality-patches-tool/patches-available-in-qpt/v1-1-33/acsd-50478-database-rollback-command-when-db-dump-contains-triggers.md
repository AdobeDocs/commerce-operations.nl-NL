---
title: 'ACSD-50478: JS-probleem voor terugdraaiactie in back-upraster en terugdraaiopdracht voor database'
description: Pas ACSD-50478 flard toe om de JS kwestie voor de het terugschroeven van prijzenactie in het steunen net en het gegevensbestand terugschroeven bevel voor een geval te bevestigen wanneer de stortplaats van DB trekkers en een *delimiter* SQL bevel bevat.
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-50478: JS-probleem voor terugdraaiactie in back-upraster en terugdraaiopdracht voor database

Het ACSD-50478 flard lost de JS kwestie voor de het terugschroeven van prijzenactie in het steunen net en het gegevensbestand terugschroeven bevel voor een geval op wanneer de stortplaats van DB trekkers en a *delimiter* SQL bevel bevat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-50478. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

JS kwestie voor de het terugschroeven van prijzenactie in het net van Steunen en het gegevensbestand terugschroeven bevel voor een geval wanneer de stortplaats van DB trekkers en a *delimiter* SQL bevel bevat.

<u> Stappen om </u> te reproduceren:

1. Stel indexeerders in op de modus [!UICONTROL Update on Schedule] , zodat er triggers worden gemaakt in de database.
1. Schakel de back-upfunctionaliteit vanaf de opdrachtregel in:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Ga naar **Systeem** > **Hulpmiddelen** > **Steunen** en produceer een steun van DB.
1. Open de browserconsole; de volgende fout wordt weergegeven:

   ```text
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Probeer de database te importeren vanaf de opdrachtregel:

   `bin/magento setup:rollback --db-file="<filename>"`

1. De volgende fout wordt weergegeven:

   ```graphql
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u> Verwachte resultaten </u>:

Het herstellen van de database is geslaagd via zowel de beheerfunctie als de opdrachtregel.

<u> Ware resultaten </u>:

U hebt de fouten waargenomen die in stap 4 en 6 worden genoemd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

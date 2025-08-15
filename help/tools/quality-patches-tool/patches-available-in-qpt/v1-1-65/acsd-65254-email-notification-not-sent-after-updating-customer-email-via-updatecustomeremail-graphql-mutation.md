---
title: 'ACSD-65254: E-mailbericht niet verzonden na het bijwerken van klantene-mail via updateCustomerEmail  [!DNL GraphQL]  mutatie'
description: Pas ACSD-65254 flard toe om de kwestie van Adobe Commerce te bevestigen waar de e-mailberichten niet werden verzonden naar klanten na met succes hun e-mailadressen op hun rekeningen gebruikend updateCustomerEmail  [!DNL GraphQL]  mutatie.
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: E-mailmelding wordt niet verzonden na het bijwerken van de e-mail van de klant via `updateCustomerEmail` [!DNL GraphQL] -mutatie

De ACSD-65254-patch verhelpt het probleem dat e-mailmeldingen niet naar klanten zijn verzonden nadat ze hun e-mailadressen op hun accounts hadden bijgewerkt met de mutatie `updateCustomerEmail` [!DNL GraphQL] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-65254. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailmeldingen zijn niet naar klanten verzonden nadat ze hun e-mailadressen hadden bijgewerkt met de mutatie `updateCustomerEmail` [!DNL GraphQL] .

<u> Stappen om </u> te reproduceren:

1. Gebruiker maken met onderstaande mutatie:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. Genereer een token voor de eerder gemaakte gebruiker en gebruik dit als token voor toonder:

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Probeer het e-mailbericht voor de eerder gemaakte gebruiker bij te werken met de laatst gemaakte token voor toonder:

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u> Verwachte resultaten </u>:

Klanten moeten e-mailmeldingen ontvangen nadat ze de e-mailadressen op hun accounts hebben bijgewerkt.

<u> Ware resultaten </u>:

Alleen een e-mailbericht met abonnement wordt naar het nieuwe adres verzonden. Het bevestigingsbericht voor de wijziging van het e-mailadres wordt niet verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

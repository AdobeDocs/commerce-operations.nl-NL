---
title: Het tabblad [!UICONTROL Security]
description: Leer meer over het [!UICONTROL Security] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Het tabblad [!UICONTROL Security]

Op het tabblad **[!UICONTROL Security]** worden beveiligingsproblemen uitgelegd en worden de mogelijke oorzaken van deze problemen geïsoleerd. Verder worden de frames van de tab beschreven.

## [!UICONTROL API calls by IP, details by URL]

In het frame **[!UICONTROL API calls by IP, details by URL]** wordt een aantal API-aanroepen door IP over een geselecteerd tijdsbestek weergegeven. Dit kader toont het IP adres en API URL die door dat IP adres werden betreden.

![ API vraag door IP ](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Het toegangsframe van **[!UICONTROL Forgot Password]** toont het aantal pogingen om een wachtwoord te vergeten over een geselecteerd tijdsbestek. De hoge activiteit tegen een IP adres kan een aanval op de plaats zijn.

![ vergeten wachtwoord ](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

In het **[!UICONTROL Create Account access]** -frame wordt het aantal nieuwe accountactiviteiten in een geselecteerd tijdsbestek weergegeven. De hoge activiteit van één enkel IP adres kan op een aanval wijzen.

![ creeer-rekening-toegang ](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

In het frame **[!UICONTROL POST activities]** worden de `POST` -activiteiten voor de site weergegeven, die in `client_ip` via de [!DNL Fastly] -logboeken zijn geactiveerd. Het toont ook URL die door het IP adres wordt betreden.

![ POST-activiteiten ](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

In het frame **[!UICONTROL POST activities summary table]** worden de samengevatte `POST` -activiteiten voor de site weergegeven, die in `client_ip` zijn opgenomen in de [!DNL Fastly] -logboeken. Het toont ook de telling voor URL die door het IP adres wordt betreden. Het aantal is voor het geselecteerde tijdframe.

![ POST-activiteiten-samenvatting ](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

In het frame **[!UICONTROL POST activities details table]** worden de `POST` -activiteiten voor de site uit de [!DNL Fastly] -logboeken weergegeven. Ook worden alle details uit het [!DNL Fastly] -logbestand voor deze aanvragen weergegeven. Het is beperkt tot de laatste 2000 verzoeken.
![ POST-activiteiten-details ](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

Het **[!UICONTROL Guest Carts activities]** kader toont het aantal activiteiten van het gastwinkelwagentje over een geselecteerd tijdskader, beperkt door IP adres en URL betreden. Gastkaarten kunnen worden gebruikt bij een tekenaanval. Dit kader toont het totale aantal verzoeken waar gast-winkelwagentjes&#39; URLs worden betreden.

![ gast-winkels-activiteiten ](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

In het frame **[!UICONTROL API – forgot password, create account by Countries]** ziet u het aantal gemaakte accounts en verzoeken om een vergeten wachtwoord opnieuw in te stellen gedurende een geselecteerd tijdsbestek. Ook het land van oorsprong van het verzoek kan worden vermeld. Dit kader is gericht op het land van oorsprong van het verzoek.

![ api-vergeten-landen ](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

In het frame **[!UICONTROL API - forgot password, create account by Countries and IP address]** ziet u het aantal gemaakte accounts en verzoeken om een vergeten wachtwoord opnieuw in te stellen gedurende een geselecteerd tijdsbestek. Het kan het IP-adres, de benaderde URL en het land van oorsprong van het verzoek ook weergeven. Dit kader wordt geconcentreerd op de telling van IP.

![ api-vergeten-landen-ip ](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

Het **[!UICONTROL Guest cart activities by IP]** kader toont de activiteiten van het gastwinkelwagentje door IP over een geselecteerd tijdkader.

![ gast-kar-ip ](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

In het frame **[!UICONTROL Guest cart activities by Countries]** worden de activiteiten van gastwinkelwagentjes per land gedurende een geselecteerd tijdsbestek weergegeven.

![ gast-kar-land ](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)

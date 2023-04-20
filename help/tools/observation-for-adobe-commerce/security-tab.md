---
title: "De [!UICONTROL Security] tab"
description: Meer informatie over de [!UICONTROL Security] tabblad van [!DNL Observation for Adobe Commerce].
source-git-commit: 5e4ab9e62f395b0967c3a632659c70a22770e9db
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# De [!UICONTROL Security] tab

De **[!UICONTROL Security]** tab geeft uitleg over beveiligingsproblemen en isoleert de mogelijke oorzaken ervan. Verder worden de frames van de tab beschreven.

## [!UICONTROL API calls by IP, details by URL]

De **[!UICONTROL API calls by IP, details by URL]** frame toont een aantal API-aanroepen door IP over een geselecteerd tijdframe. Dit kader toont het IP adres en API URL die door dat IP adres werden betreden.

![API-aanroepen door IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

De **[!UICONTROL Forgot Password]** het toegangskader toont het aantal pogingen van het vergeten wachtwoord over een geselecteerd tijdsbestek. De hoge activiteit tegen een IP adres kan een aanval op de plaats zijn.

![Wachtwoord vergeten](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

De **[!UICONTROL Create Account access]** frame geeft het aantal nieuwe accountactiviteiten weer over een geselecteerd tijdsbestek. De hoge activiteit van één enkel IP adres kan op een aanval wijzen.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

De **[!UICONTROL POST activities]** frame toont de `POST` activiteiten voor de site, aangestuurd op `client_ip` van de [!DNL Fastly] logboeken. Het toont ook URL die door het IP adres wordt betreden.

![POST](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

De **[!UICONTROL POST activities summary table]** frame toont overzicht `POST` activiteiten voor de site, aangestuurd op `client_ip` van de [!DNL Fastly] logboeken. Het toont ook de telling voor URL die door het IP adres wordt betreden. Het aantal is voor het geselecteerde tijdframe.

![POST-activiteiten-overzicht](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

De **[!UICONTROL POST activities details table]** frame toont de `POST` activiteiten voor de locatie vanuit de [!DNL Fastly] logboeken. Het toont ook alle details van [!DNL Fastly] logboek voor deze verzoeken. Het is beperkt tot de laatste 2000 verzoeken.
![POST-activiteiten-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

De **[!UICONTROL Guest Carts activities]** Het kader toont het aantal activiteiten van het gastwinkelwagentje over een geselecteerd tijdskader, beperkt door IP adres en URL betreden. Gastkaarten kunnen worden gebruikt bij een tekenaanval. Dit kader toont het totale aantal verzoeken waar gast-winkelwagentjes&#39; URLs worden betreden.

![gastwinkels](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

De **[!UICONTROL API – forgot password, create account by Countries]** frame toont het aantal gemaakte accounts en verzoeken om een vergeten wachtwoord opnieuw in te stellen over een geselecteerd tijdsbestek. Ook het land van oorsprong van het verzoek kan worden vermeld. Dit kader is gericht op het land van oorsprong van het verzoek.

![api-vergeten-landen](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

De **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame toont het aantal gemaakte accounts en verzoeken om een vergeten wachtwoord opnieuw in te stellen over een geselecteerd tijdsbestek. Het kan het IP-adres, de benaderde URL en het land van oorsprong van het verzoek ook weergeven. Dit kader wordt geconcentreerd op de telling van IP.

![api-vergeten-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

De **[!UICONTROL Guest cart activities by IP]** het kader toont de activiteiten van het gastwinkelwagentje door IP over een geselecteerd tijdkader.

![gast-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

De **[!UICONTROL Guest cart activities by Countries]** frame toont gastcartactiviteiten per land over een geselecteerd tijdsbestek.

![gastland](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)

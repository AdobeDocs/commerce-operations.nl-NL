---
title: Opmerkingen bij de release Adobe Commerce 2.4.7 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

De Adobe Commerce 2.4.7-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-40 Adobe](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Beveiligingsmarkering

Deze release bevat een update van de [instellingen voor eenmalige wachtwoorden (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) voor Google Authenticator om een fout op te lossen die door een [achterwaartse incompatibele wijziging](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7. De beschrijving van de **[!UICONTROL OTP Window]** veld bevat nu een nauwkeurige uitleg van de instelling en de standaardwaarde is gewijzigd van `1` tot `29`.

---
title: Opmerkingen bij de release Adobe Commerce 2.4.7 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

De Adobe Commerce 2.4.7-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB24-40 Adobe](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Beveiligingsmarkeringen

* **Bijwerken [instellingen voor eenmalige wachtwoorden (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) voor Google Authenticator**-Deze update is vereist om een fout op te lossen die door een [achterwaartse incompatibele wijziging](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7. De beschrijving van de **[!UICONTROL OTP Window]** veld bevat nu een nauwkeurige uitleg van de instelling en de standaardwaarde is gewijzigd van `1` tot `29`.

* **B2B-versiecompatibiliteit**—Voor compatibiliteit met Commerce versie 2.4.7-p1 moeten handelaren met de Adobe Commerce B2B-extensie een upgrade uitvoeren naar [B2B versie 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.7-p1 verhelpt een probleem dat is ontstaan in het bereik van de migratie van UPS-integratie van SOAP naar REST API. Dit probleem betrof klanten die buiten de VS verschepen en belette hen de Metric System/SI-metingen van kilo en centimeters voor pakketten te gebruiken om zendingen met UPS te maken. Zie de [Integratie van UPS-verzendmethoden van SOAP naar RESTful-API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) kennisbank voor meer informatie .

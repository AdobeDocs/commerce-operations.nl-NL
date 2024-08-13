---
title: Opmerkingen bij de release Adobe Commerce 2.4.7 Security Patch
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p2

De Adobe Commerce 2.4.7-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 worden geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB24-61 ](https://helpx.adobe.com/security/products/magento/apsb24-61.html).[

### Hooglichten

{{$include /help/_includes/release-notes/2024-08/security.md}}

### Hotfixes die in deze release zijn opgenomen

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

De Adobe Commerce 2.4.7-p1 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies van 2.4.7 zijn geïdentificeerd.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie {het Bulletin van de Veiligheid van de Adobe APSB24-40 ](https://helpx.adobe.com/security/products/magento/apsb24-40.html).[

### Hotfix toepassen voor CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Hooglichten

Deze release bevat de volgende hooglichten:

* [ eenmalig wachtwoord van de Update **(OTP) montages ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) voor de Authenticator van Google** - Deze update wordt vereist om een fout op te lossen die door a [ achteruit-onverenigbaar verandering ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) in 2.4.7 werd geïntroduceerd. De beschrijving van het veld **[!UICONTROL OTP Window]** bevat nu een nauwkeurige uitleg van de instelling en de standaardwaarde is gewijzigd van `1` in `29` .

* **B2B versiecompatibiliteit** - voor verenigbaarheid met versie 2.4.7-p1 van Commerce, de verkopers die de uitbreiding hebben van Adobe Commerce B2B moeten aan [ B2B versie 1.4.2-p1 ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) bevorderen.

### Hotfixes die in deze release zijn opgenomen

Adobe Commerce 2.4.7-p1 verhelpt een probleem dat is ontstaan in het bereik van de migratie van UPS-integratie van SOAP naar REST API. Dit probleem betrof klanten die buiten de VS verschepen en belette hen de Metric System/SI-metingen van kilo en centimeters voor pakketten te gebruiken om zendingen met UPS te maken. Zie [ UPS die de migratie van de methodeintegratie van SOAP aan RESTful API ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) kennisbankartikel voor details verschepen.

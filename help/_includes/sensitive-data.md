---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Gevoelige gegevens

Adobe Commerce en Magento Open Source gebruiken uw coderingssleutel om het volgende te coderen:

* Creditcardgegevens
* Gebruikersnamen en wachtwoorden die zijn opgegeven in de beheerconfiguratie (bijvoorbeeld aanmelden bij betaalgateways)
* CAPTCHA-waarden die via het netwerk worden verzonden

Adobe Commerce en Magento Open Source doen *niet* versleutelen:

* Administratieve en klantengebruikersnamen en wachtwoorden (deze wachtwoorden worden gehakt)
* Adres
* Telefoonnummer
* Andere soorten persoonlijk identificeerbare informatie, behalve creditcardnummers

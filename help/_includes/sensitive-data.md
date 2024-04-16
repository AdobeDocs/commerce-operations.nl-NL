---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---
# Gevoelige gegevens

Adobe Commerce gebruikt uw coderingssleutel om het volgende te coderen:

* Creditcardgegevens
* Gebruikersnamen en wachtwoorden die zijn opgegeven in de beheerconfiguratie (bijvoorbeeld aanmelden bij betaalgateways)
* CAPTCHA-waarden die via het netwerk worden verzonden

Adobe Commerce do *niet* versleutelen:

* Administratieve en klantengebruikersnamen en wachtwoorden (deze wachtwoorden worden gehakt)
* Adres
* Telefoonnummer
* Andere soorten persoonlijk identificeerbare informatie, behalve creditcardnummers

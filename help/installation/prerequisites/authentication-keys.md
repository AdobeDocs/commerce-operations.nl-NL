---
title: Uw verificatietoetsen ophalen
description: Voer de volgende stappen uit om referenties op repo.magento.com op te halen en toegang te krijgen tot Adobe Commerce- en Magento Open Source Composer-pakketten.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Uw verificatietoetsen ophalen

De `repo.magento.com` In de opslagplaats worden Adobe Commerce- en Magento Open Source- en Composer-pakketten van derden opgeslagen en vereist verificatie. Gebruik uw Commerce Marketplace-account om een paar van 32 tekens te genereren *verificatietoetsen* om toegang te krijgen tot de repository.

>[!NOTE]
>
>Voor toegangsrechten voor Adobe Commerce- en Magento Open Source-pakketten moet u sleutels gebruiken die zijn gekoppeld aan een MAGEID die toegang heeft gekregen tot deze pakketten. De MAGEID is doorgaans de **Factureringscontactpersoon** op de Adobe Commerce-rekening en is wellicht niet altijd de **Projecteigenaar** van het Adobe Commerce-project inzake cloudinfrastructuur. Als u [fouten](https://support.magento.com/hc/en-us/articles/360040296392), hebt u mogelijk geen toestemming om het pakket te openen of de toegangsrechten zijn verlopen vanwege een openstaande factuur op de account. Contact [Adobe Commerce-ondersteuning](https://support.magento.com/hc/en-us) voor hulp met je MAGEID.

Zo maakt u verificatietoetsen:

1. Aanmelden bij de [Commerce Marketplace](https://marketplace.magento.com). Als u geen account hebt, klikt u op **Registreren**.
1. Klik op de naam van uw account rechtsboven op de pagina en selecteer **Mijn profiel**.

1. Klikken **Toegangstoetsen** op het tabblad Marktplaats.

   ![Krijg uw veilige toegangstoetsen op Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Klikken **Een nieuwe toegangstoets maken**. Voer een specifieke naam in voor de toetsen (bijvoorbeeld de naam van de ontwikkelaar die de toetsen ontvangt) en klik op **OK**.

1. Nieuwe openbare en persoonlijke sleutels zijn nu gekoppeld aan uw account waarop u kunt klikken om te kopiëren. Sla deze gegevens op of open de pagina wanneer u met uw project werkt. Gebruik de **Openbare sleutel** als uw gebruikersnaam en **Persoonlijke sleutel** als uw wachtwoord.

## De verificatietoetsen beheren

U kunt verificatietoetsen ook uitschakelen of verwijderen. U kunt bijvoorbeeld toetsen uit veiligheidsoverwegingen uitschakelen of verwijderen nadat iemand uw organisatie heeft verlaten.

* Toetsen uitschakelen: Klikken **Uitschakelen**. U kunt dit doen als u het gebruik van uw sleutels wilt onderbreken.
* Een eerder uitgeschakelde toets inschakelen: Klikken **Inschakelen**.
* Toetsen verwijderen: Klikken **Verwijderen**.

### SSH-toegangstoken beheren

Als u Adobe Commerce-releases wilt downloaden met behulp van SSH, moet u een Toegangstoken voor downloads genereren. Een token genereren:

1. Meld u aan bij uw [magento.com-account](https://account.magento.com/customer/account/login).
1. Klikken **Mijn account** boven aan de pagina.
1. Klikken **Accountinstellingen** > **Downloadtoken**.

   ![Toegang tot uw toetsen](../../assets/installation/connect_keys1.png)

1. Klikken **Nieuw token genereren** om een bestaand token te vervangen en uit te schakelen.

U moet uw MAGEID plus uw token gebruiken om een release te downloaden. Je GEID wordt linksboven op je rekeningpagina weergegeven.

Bijvoorbeeld:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Gebruik uw verificatietoetsen om:

* [Haal het pakket metapakketten op (integrators, packagers)](../composer.md)
* [Clone the GitHub repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (alleen voor bijdragende ontwikkelaars)
* [Modules upgraden en beheren](../../upgrade/modules/upgrade.md)

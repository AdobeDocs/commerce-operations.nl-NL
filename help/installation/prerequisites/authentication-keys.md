---
title: Uw verificatietoetsen ophalen
description: Ga als volgt te werk om referenties op te halen voor toegang tot Adobe Commerce Composer-pakketten op repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Uw verificatietoetsen ophalen

De `repo.magento.com` In de opslagplaats worden Adobe Commerce- en Composer-pakketten van derden opgeslagen en vereist verificatie. Gebruik uw rekening van de Commerce Marketplace om een paar van 32 karakter te produceren *verificatietoetsen* om toegang te krijgen tot de gegevensopslagruimte.

Voor toegangsrechten voor Adobe Commerce-pakketten moet u sleutels gebruiken die zijn gekoppeld aan een MAGEID die toegang heeft gekregen tot die pakketten. De MAGEID is doorgaans de primaire contactpersoon op de Adobe Commerce-account en is mogelijk niet altijd de projecteigenaar van de Adobe Commerce voor het infrastructuurproject in de cloud.

>[!TIP]
>
>Als u [fouten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), hebt u mogelijk geen toestemming om het pakket te openen of de toegangsrechten zijn verlopen vanwege een openstaande factuur op uw account.
>
>* Als je de primaire contactpersoon voor de account bent, zorg er dan voor dat er geen openstaande factuur op de account wordt vermeld.
>* Als de sleutels die door de Primaire Contact worden verstrekt niet werken en er geen uitstaande facturen op de rekening zijn, zou de Primaire Contact [Adobe Commerce-ondersteuning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) voor hulp.

Zo maakt u verificatietoetsen:

1. Aanmelden bij de [Commerce Marketplace](https://commercemarketplace.adobe.com/). Als u geen account hebt, klikt u op **Registreren**.

1. Klik op de naam van uw account rechtsboven op de pagina en selecteer **Mijn profiel**.

1. Klikken **Toegangssleutels** op het tabblad Marktplaats.

   ![Krijg uw veilige toegangstoetsen op Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Klikken **Een nieuwe toegangstoets maken**. Voer een specifieke naam in voor de toetsen (bijvoorbeeld de naam van de ontwikkelaar die de toetsen ontvangt) en klik op **OK**.

1. Nieuwe openbare en persoonlijke sleutels zijn nu gekoppeld aan uw account waarop u kunt klikken om te kopiëren. Sla deze gegevens op of open de pagina wanneer u met uw project werkt. Gebruik de **Openbare sleutel** als uw gebruikersnaam en de **Persoonlijke sleutel** als uw wachtwoord.

## De verificatietoetsen beheren

U kunt verificatietoetsen ook uitschakelen of verwijderen. U kunt bijvoorbeeld toetsen uit veiligheidsoverwegingen uitschakelen of verwijderen nadat iemand uw organisatie heeft verlaten.

* Om toetsen uit te schakelen: klik **Uitschakelen**. U kunt dit doen als u het gebruik van uw sleutels wilt onderbreken.
* Een eerder uitgeschakelde toets inschakelen: klik op **Inschakelen**.
* Als u toetsen wilt verwijderen, klikt u op **Verwijderen**.

### SSH-toegangstoken beheren

Als u Adobe Commerce-releases wilt downloaden met behulp van SSH, moet u een Toegangstoken voor downloads genereren. Een token genereren:

1. Aanmelden bij uw [magento.com](https://account.magento.com/customer/account/login).
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

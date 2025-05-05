---
title: Overzicht van installatie op locatie
description: Leer meer over het installatieproces voor een Adobe Commerce-uitrol op locatie.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Overzicht van installatie op locatie

>[!NOTE]
>
>Het volgende diagram verstrekt een overzicht op hoog niveau van _&#x200B;**op-gebouw**&#x200B;_ installaties van Adobe Commerce:

![ hoe de installatie ](../assets/installation/install-diagram-24.svg) werkt

De algemene installatiestroom is als volgt:

1. Stel uw serveromgeving in.

   Installeer de vereiste software, waaronder PHP, Apache, MySQL en de zoekmachine. Zie de [ systeemvereisten ](system-requirements.md) voor meer informatie.

1. Krijg [ authentificatietoetsen ](prerequisites/authentication-keys.md) aan de bewaarplaats van de Composer van Commerce.

1. Haal de Adobe Commerce-software op.

   * (Geadviseerd) Krijg het [ metapakket van de Composer ](composer.md) om modules en hun gebiedsdelen te beheren.

   * Als u aan de codebase van de Magento Open Source wilt bijdragen of de toepassing aanpassen, [ kloon ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) de bewaarplaats GitHub. Deze methode vereist vertrouwdheid met zowel GitHub als Composer.

1. Installeer de toepassing met de opdrachtregel.

   Als de stap ontbreekt omdat de in de eerste plaats vereiste software niet opstelling correct is, herzie de [ eerste vereisten ](prerequisites/overview.md).

1. [ verifieer ](next-steps/verify.md) de installatie door uw storefront en Admin te bekijken.

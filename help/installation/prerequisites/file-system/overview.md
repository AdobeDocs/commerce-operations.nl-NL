---
title: Bestandseigendom en machtigingen
description: Leer over het belang van de toestemmingen van het dossiersysteem wanneer het werken met op-gebouw installaties van Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Bestandseigendom en machtigingen

Het is belangrijk om uw installatie van Adobe Commerce in een ontwikkelomgeving te beveiligen om problemen met betrekking tot onbevoegde personen of processen die toegang hebben tot uw systeem (en mogelijk schade kunnen toebrengen) te helpen voorkomen. Gebruik de volgende richtlijnen voor eigendom van en machtigingen voor het bestandssysteem om uw installatie te beveiligen.

## Eigenaar van bestandssysteem

De eigenaar van het bestandssysteem is een gebruiker die eigenaar is van en beschikt over schrijfmachtigingen voor bestanden in het bestandssysteem.

Er zijn twee typen bestandssysteemeigenaars:

- **Gedeeld die met één enkele gebruiker** ontvangt

  Via gedeelde hostingproviders kunt u zich als één gebruiker aanmelden bij de toepassingsserver. Als enkele gebruiker kunt u zich aanmelden, bestanden overbrengen met FTP en de webserver uitvoeren. U kunt een [`umask`](#restrict-access-with-a-umask) instellen om de toegang verder te beperken, met name in een productieomgeving.

- **Privé het ontvangen met twee gebruikers**

  Persoonlijk hosten is nuttig als u een toepassingsserver beheert. Elke gebruiker heeft een specifieke verantwoordelijkheid:

   - De _gebruiker van de Webserver_ stelt Admin en opslag in werking.

   - De _bevel-lijn gebruiker_ stelt gezamenlijke banen en bevel-lijn nut in werking.

  Beide gebruikers vereisen de zelfde toestemmingen aan het dossiersysteem, zodat is het best om a [&#x200B; gedeelde groep &#x200B;](configure-permissions.md#set-ownership-and-permissions-for-two-users) te gebruiken en a [`umask`](#restrict-access-with-a-umask) te plaatsen.

### Toegang beperken met een masker

Als u de beveiliging wilt verscherpen, met name in een productieomgeving op een gedeeld hostsysteem, kunt u `umask` gebruiken om de toegang te beperken. A `umask` - die ook als masker van de de creatie van het a _dossiersysteem_ wordt bedoeld - is een reeks beetjes die controleert hoe de dossiertoestemmingen voor pas gecreëerde dossiers worden geplaatst.

>[!WARNING]
>
>Beveiliging van bestandssystemen is complex en belangrijk. Wij adviseren sterk dat u een ervaren systeembeheerder of netwerkbeheerder raadpleegt alvorens u het niveau van toestemmingen beslist te plaatsen. Wij bieden u een mechanisme dat u kunt gebruiken, maar het maken van een machtigingsstrategie is uw verantwoordelijkheid.

Adobe Commerce gebruikt een 3-bits standaardmasker: `002` . Trek het standaardmasker van de gebreken van UNIX van 666 voor dossiers en 777 voor folders af.

Bijvoorbeeld:

- **775 voor folders** - Volledige controle door de gebruiker, volledige controle door de groep, en laat iedereen toe om de folder over te steken. Deze machtigingen worden doorgaans vereist door gedeelde hostingproviders.

- **664 voor dossiers** - Schrijfbaar door de gebruiker, schrijfbaar door de groep, en read-only voor iedereen anders.

Voor meer informatie over het creëren van a `magento_umask` dossier, zie [&#x200B; Plaats een masker &#x200B;](../../next-steps/set-umask.md).

## Machtigingen, eigendom en toepassingsmodi

We raden verschillende machtigingen en eigendom aan wanneer u de verschillende Adobe Commerce-toepassingsmodi gebruikt:

- Standaard
- Ontwikkelaar
- Productie

Zie [&#x200B; Ongeveer wijzen &#x200B;](../../../configuration/bootstrap/application-modes.md) in de _gids van de Configuratie_.

Wij bespreken verder toestemmingsaanbevelingen in [&#x200B; de toegangstoestemmingen van de systeemtoegang van het Dossier &#x200B;](../../../configuration/deployment/file-system-permissions.md) in de _gids van de Configuratie_.

>[!TIP]
>
>Alvorens u Adobe Commerce installeert, overzicht [&#x200B; vormt dossiereigendom en toestemmingen &#x200B;](configure-permissions.md).

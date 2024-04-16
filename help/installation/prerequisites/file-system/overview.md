---
title: Bestandseigendom en machtigingen
description: Leer over het belang van de toestemmingen van het dossiersysteem wanneer het werken met op-gebouw installaties van Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Bestandseigendom en machtigingen

Het is belangrijk om uw installatie van Adobe Commerce of Magento Open Source in een ontwikkelomgeving te beveiligen om problemen met betrekking tot onbevoegde personen of processen die toegang hebben tot uw systeem (en mogelijk schade toebrengen) te helpen voorkomen. Gebruik de volgende richtlijnen voor eigendom van en machtigingen voor het bestandssysteem om uw installatie te beveiligen.

## Eigenaar van bestandssysteem

De eigenaar van het bestandssysteem is een gebruiker die eigenaar is van en beschikt over schrijfmachtigingen voor bestanden in het bestandssysteem.

Er zijn twee typen bestandssysteemeigenaars:

- **Gedeeld hosten met één gebruiker**

  Via gedeelde hostingproviders kunt u zich als één gebruiker aanmelden bij de toepassingsserver. Als enkele gebruiker kunt u zich aanmelden, bestanden overbrengen met FTP en de webserver uitvoeren. U kunt een [`umask`](#restrict-access-with-a-umask) de toegang verder te beperken , met name in een productieomgeving .

- **Privéhosting met twee gebruikers**

  Persoonlijk hosten is nuttig als u een toepassingsserver beheert. Elke gebruiker heeft een specifieke verantwoordelijkheid:

   - De _webservergebruiker_ voert Admin en storefront uit.

   - De _opdrachtregelgebruiker_ Hiermee worden uitsnijdtaken en opdrachtregelprogramma&#39;s uitgevoerd.

  Beide gebruikers vereisen de zelfde toestemmingen aan het dossiersysteem, zodat is het best te gebruiken [gedeelde groep](configure-permissions.md#set-ownership-and-permissions-for-two-users) en stelt een [`umask`](#restrict-access-with-a-umask).

### Toegang beperken met een masker

Als u de beveiliging wilt verscherpen, met name in een productieomgeving op een gedeeld hostsysteem, kunt u `umask` om de toegang te beperken. A `umask`—ook aangeduid als a _ontwerpmasker van bestandssysteem_—is een reeks beetjes die controleert hoe de dossiertoestemmingen voor pas gecreëerde dossiers worden geplaatst.

>[!WARNING]
>
>Beveiliging van bestandssystemen is complex en belangrijk. Wij adviseren sterk dat u een ervaren systeembeheerder of netwerkbeheerder raadpleegt alvorens u het niveau van toestemmingen beslist te plaatsen. Wij bieden u een mechanisme dat u kunt gebruiken, maar het maken van een machtigingsstrategie is uw verantwoordelijkheid.

Adobe Commerce gebruikt een 3-bits standaardmasker: `002`. Trek het standaardmasker van de gebreken van UNIX van 666 voor dossiers en 777 voor folders af.

Bijvoorbeeld:

- **775 voor directory&#39;s**—Volledige controle door de gebruiker, volledige controle door de groep, en laat iedereen toe om de folder over te steken. Deze machtigingen worden doorgaans vereist door gedeelde hostingproviders.

- **664 voor bestanden**—Schrijfbaar door de gebruiker, beschrijfbaar door de groep, en read-only voor alle anderen.

Voor meer informatie over het maken van een `magento_umask` bestand, zie [Een masker instellen](../../next-steps/set-umask.md).

## Machtigingen, eigendom en toepassingsmodi

We raden verschillende machtigingen en eigendom aan wanneer u de verschillende Adobe Commerce-toepassingsmodi gebruikt:

- Standaard
- Ontwikkelaar
- Productie

Zie [Modus Info](../../../configuration/bootstrap/application-modes.md) in de _Configuratiegids_.

We bespreken verder machtigingsaanbevelingen in [Toegangsrechten voor bestandssystemen](../../../configuration/deployment/file-system-permissions.md) in de _Configuratiegids_.

>[!TIP]
>
>Voordat u Adobe Commerce of Magento Open Source installeert, moet u controleren [Eigendom en machtigingen van bestanden configureren](configure-permissions.md).

---
title: Een masker instellen (optioneel)
description: Verbeter de veiligheidshouding van uw Adobe Commerce of Magento Open Source op-gebouw installatie door de toestemmingen van het dossiersysteem te beperken.
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Een masker instellen (optioneel)

De webservergroep moet schrijfmachtigingen hebben voor bepaalde mappen in het bestandssysteem. maar u wilt misschien een betere beveiliging , vooral in de productie . We bieden u de flexibiliteit om deze machtigingen verder te beperken met behulp van een [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Onze oplossing is u in staat te stellen naar keuze een bestand te maken met de naam `magento_umask` in de hoofdmap van de toepassing die machtigingen beperkt voor de webservergroep en voor alle andere gebruikers.

>[!NOTE]
>
>We raden u aan het masker alleen te wijzigen op een hostsysteem voor één gebruiker of een gedeeld hostsysteem. Als u een privétoepassingsserver hebt, moet de groep schrijftoegang hebben tot het bestandssysteem. Met het masker verwijdert u schrijftoegang uit de groep.

Het standaardmasker (zonder `magento_umask` gespecificeerd) is `002`, hetgeen betekent:

* 775 voor folders, wat volledige controle door de gebruiker, volledige controle door de groep betekent, en iedereen toelaat om de folder over te steken. Deze machtigingen worden doorgaans vereist door gedeelde hostingproviders.

* 664 voor dossiers, wat door de gebruiker te schrijven betekent, schrijfbaar door de groep, en read-only voor alle anderen

Een algemene suggestie is om een waarde van `022` in de `magento_umask` bestand, dat wil zeggen:

* 755 voor directory&#39;s: de volledige controle voor de gebruiker, en iedereen anders kan folders oversteken.
* 644 voor bestanden: lees-schrijf toestemmingen voor de gebruiker, en read-only voor iedereen anders.

In te stellen `magento_umask`:

1. In een bevel-lijn terminal, login aan uw toepassingsserver als [eigenaar van bestandssysteem](../prerequisites/file-system/overview.md).
1. Ga naar de installatiemap van de toepassing:

   ```bash
   cd <Application install directory>
   ```

1. Gebruik de volgende opdracht om een bestand te maken met de naam `magento_umask` en schrijven `umask` waarderen.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   U moet nu een bestand hebben met de naam `magento_umask` in de `<Magento install dir>` waarbij de enige inhoud de `umask` getal.

1. Log uit en log terug in als de [eigenaar van bestandssysteem](../prerequisites/file-system/overview.md) om de wijzigingen toe te passen.

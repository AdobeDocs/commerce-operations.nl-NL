---
title: Een masker instellen (optioneel)
description: Verbeter de beveiligingspositie van uw Adobe Commerce-installatie op locatie door de machtigingen voor het bestandssysteem te beperken.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Een masker instellen (optioneel)

De webservergroep moet schrijfmachtigingen hebben voor bepaalde mappen in het bestandssysteem. Het is echter verstandig de beveiliging te verbeteren, met name in de productie. Wij verstrekken de flexibiliteit voor u om die toestemmingen verder te beperken gebruikend a [ masker ](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Het is onze oplossing om u desgewenst in staat te stellen een bestand met de naam `magento_umask` in de hoofdmap van de toepassing te maken dat machtigingen beperkt voor de webservergroep en voor alle anderen.

>[!NOTE]
>
>We raden u aan het masker alleen te wijzigen op een hostsysteem voor één gebruiker of een gedeeld hostsysteem. Als u een privétoepassingsserver hebt, moet de groep schrijftoegang tot het bestandssysteem hebben. Het masker verwijdert schrijftoegang van de groep.

Het standaardmasker (zonder `magento_umask` opgegeven) is `002` , wat betekent:

* 775 voor folders, wat volledige controle door de gebruiker, volledige controle door de groep betekent, en iedereen toelaat om de folder over te steken. Deze machtigingen worden doorgaans vereist door gedeelde hostingproviders.

* 664 voor dossiers, wat door de gebruiker te schrijven betekent, schrijfbaar door de groep, en read-only voor alle anderen

Een algemene suggestie is om de waarde `022` in het `magento_umask` -bestand te gebruiken, wat betekent:

* 755 voor directory&#39;s: volledige controle voor de gebruiker, en alle anderen kunnen folders doorlopen.
* 644 voor bestanden: lees- en schrijfmachtigingen voor de gebruiker en alleen-lezen voor alle anderen.

Ga als volgt te werk om `magento_umask` in te stellen:

1. In een bevel-lijn terminal, login aan uw toepassingsserver als eigenaar van het a [ dossiersysteem ](../prerequisites/file-system/overview.md).
1. Navigeer naar de installatiemap van de toepassing:

   ```bash
   cd <Application install directory>
   ```

1. Gebruik de volgende opdracht om een bestand met de naam `magento_umask` te maken en de waarde `umask` eraan te schrijven.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   U moet nu een bestand met de naam `magento_umask` in de `<Magento install dir>` hebben, waarbij de enige inhoud het `umask` -nummer is.

1. Logout en logboek terug binnen als [ eigenaar van het dossiersysteem ](../prerequisites/file-system/overview.md) om de veranderingen toe te passen.

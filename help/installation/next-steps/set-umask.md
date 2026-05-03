---
title: Een masker instellen (optioneel)
description: Verbeter de beveiligingspositie van uw Adobe Commerce-installatie op locatie door de machtigingen voor het bestandssysteem te beperken.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Een masker instellen (optioneel)

De webservergroep moet schrijfmachtigingen hebben voor bepaalde mappen in het bestandssysteem. maar u wilt misschien een betere beveiliging , met name in de produktie . Wij verstrekken de flexibiliteit voor u om die toestemmingen verder te beperken gebruikend a [ masker ](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Het is onze oplossing om u desgewenst in staat te stellen een bestand met de naam `magento_umask` in de hoofdmap van de toepassing te maken dat machtigingen beperkt voor de webservergroep en voor alle anderen.

>[!NOTE]
>
>We raden u aan het masker alleen te wijzigen op een hostsysteem voor één gebruiker of een gedeeld hostsysteem. Als u een privétoepassingsserver hebt, moet de groep schrijftoegang hebben tot het bestandssysteem. Met het masker verwijdert u schrijftoegang uit de groep.

Het standaardmasker (zonder `magento_umask` opgegeven) is `002` , wat betekent:

* 775 voor folders, wat volledige controle door de gebruiker, volledige controle door de groep betekent, en iedereen toelaat om de folder over te steken. Deze machtigingen worden doorgaans vereist door gedeelde hostingproviders.

* 664 voor dossiers, wat door de gebruiker te schrijven betekent, schrijfbaar door de groep, en read-only voor alle anderen

Een algemene suggestie is om de waarde `022` in het `magento_umask` -bestand te gebruiken, wat betekent:

* 755 voor directory&#39;s: de volledige controle voor de gebruiker, en iedereen anders kan folders doorkruisen.
* 644 voor bestanden: lees-schrijf toestemmingen voor de gebruiker, en read-only voor iedereen anders.

Ga als volgt te werk om `magento_umask` in te stellen:

1. In een bevel-lijn terminal, login aan uw toepassingsserver als eigenaar van het a [ dossiersysteem ](../prerequisites/file-system/overview.md).
1. Navigeer naar de installatiemap van de toepassing:

   ```shell
   cd <Application install directory>
   ```

1. Gebruik de volgende opdracht om een bestand met de naam `magento_umask` te maken en de waarde `umask` eraan te schrijven.

   ```shell
   echo <desired umask number> > magento_umask
   ```

   U moet nu een bestand met de naam `magento_umask` in de `<Magento install dir>` hebben, waarbij de enige inhoud het `umask` -nummer is.

1. Logout en logboek terug binnen als [ eigenaar van het dossiersysteem ](../prerequisites/file-system/overview.md) om de veranderingen toe te passen.

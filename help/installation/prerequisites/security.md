---
title: Beveiliging van installatie op locatie
description: Meer informatie over manieren om de beveiligingspositie van uw Adobe Commerce-installatie op locatie te verbeteren.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Beveiliging van installatie op locatie

[&#x200B; Veiligheid Verbeterde Linux (SELinux) &#x200B;](https://selinuxproject.org/page/Main_Page) laat CentOS en de beheerders van Ubuntu grotere toegangsbeheer over hun servers toe. Als u SELinux *en* Apache gebruikt moet een verbinding aan een andere gastheer in werking stellen, moet u de bevelen in werking stellen die in deze sectie worden besproken.

>[!NOTE]
>
>Adobe heeft geen aanbeveling over het gebruik van SELinux. U kunt deze desgewenst gebruiken voor uitgebreide beveiliging. Als u SELinux gebruikt, moet u het op de juiste wijze configureren of kan de Adobe Commerce onvoorspelbaar werken. Als u verkiest om SELinux te gebruiken, raadpleeg een middel zoals de [&#x200B; wiki CentOS &#x200B;](https://wiki.centos.org/HowTos/SELinux) aan opstellingsregels om mededeling toe te laten.

## Suggesties voor installatie met Apache

Als u verkiest om SELinux toe te laten, zou u kwesties kunnen hebben die het installatieprogramma in werking stellen tenzij u de *veiligheidscontext* van sommige folders als volgt verandert:

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

De voorgaande opdrachten werken alleen met de Apache-webserver. Wegens de verscheidenheid van configuraties en veiligheidsvereisten, waarborgen wij deze bevelen werk in alle situaties niet. Zie voor meer informatie:

* [man page](https://linux.die.net/man/8/httpd_selinux)
* [Server Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Communicatie tussen servers inschakelen

Als Apache en de databaseserver zich op dezelfde host bevinden, gebruikt u de volgende opdracht als u integraties wilt gebruiken die `curl` gebruiken (bijvoorbeeld Paypal en USPS).
Om Apache in staat te stellen een verbinding met een andere gastheer met toegelaten SELinux in werking te stellen:

1. Gebruik de volgende opdracht om te bepalen of SELinux is ingeschakeld:

   ```shell
   getenforce
   ```

   `Enforcing` wordt weergegeven om te bevestigen dat SELinux wordt uitgevoerd.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Poorten openen in uw firewall

Afhankelijk van uw veiligheidsvereisten, zou u het noodzakelijk kunnen vinden om haven 80 en andere havens in uw firewall te openen. Vanwege de gevoelige aard van netwerkbeveiliging raadt Adobe u ten zeerste aan uw IT-afdeling te raadplegen voordat u verdergaat. Hier volgen enkele suggesties voor verwijzingen:

* Ubuntu: [&#x200B; de documentatiepagina van Ubuntu &#x200B;](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [&#x200B; CentOS hoe-aan &#x200B;](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

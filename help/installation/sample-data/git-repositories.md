---
title: Voorbeeldgegevensopslagruimten klonen
description: Voer de volgende stappen uit om Adobe Commerce-voorbeeldgegevens te installeren door Git-opslagplaatsen te klonen.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Voorbeeldgegevensopslagruimten klonen

Dit onderwerp bespreekt hoe te om steekproefgegevens te klonen en toe te voegen als u de bewaarplaats van Magento Open Source GitHub kloond. Deze methode is alleen bedoeld voor ontwikkelaars die een bijdrage leveren (dat wil zeggen ontwikkelaars die een bijdrage willen leveren aan de codebase van de Magento Open Source).

Als u geen bijdragende ontwikkelaar bent, kies één van de andere opties die in de inhoudstafel op de linkerkant van de pagina worden getoond.

De bijdragende ontwikkelaars kunnen deze methode gebruiken om steekproefgegevens *slechts* te installeren als het volgende waar is:

* U gebruikt Magento Open Source
* U [ gekloond de bewaarplaats GitHub ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>U kunt voorbeeldgegevens gebruiken met de `develop` -vertakking (huidiger) of een vrijgegeven vertakking (zoals `2.4` (stabieler)). We raden u aan een vrijgegeven vertakking te gebruiken omdat deze stabieler is. Gebruik de `develop` -vertakking als u code toevoegt aan de repository en u de meest recente code nodig hebt. Ongeacht de tak u kiest, moet u [ klonen ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) de overeenkomstige tak van de bewaarplaats van Magento Open Source GitHub. Bijvoorbeeld, kunnen de steekproefgegevens voor de `develop` tak *slechts* met de Magento Open Source `develop` tak worden gebruikt.

## De gegevensopslagplaats van de voorbeeldgegevens klonen

In deze sectie wordt beschreven hoe u voorbeeldgegevens kunt installeren door de gegevensopslagruimte voor voorbeeldgegevens te klonen. U kunt de gegevensopslagplaats van de steekproef op om het even welke volgende manieren klonen:

* Klonen met het [ protocol van SSH ](#clone-with-ssh)
* Klonen met het [ protocol HTTPS ](#clone-with-https)

### Klonen met SSH

Om de bewaarplaats van GitHub van steekproefgegevens te klonen gebruikend het protocol van SSH:

1. In Webbrowser, ga naar de [ bewaarplaats van steekproefgegevens ](https://github.com/magento/magento2-sample-data).
1. Naast de naam van de tak, klik **SSH** van de lijst.
1. Klik **Exemplaar aan klembord**

   In de volgende afbeelding ziet u een voorbeeld.

   ![ Kloon de bewaarplaats GitHub gebruikend SSH ](../../assets/installation/install_mage2_clone-ssh.png)

1. Wijzig de hoofdmap van de webserver.

   Voor Ubuntu is dit doorgaans `/var/www` en voor CentOS is het `/var/www/html` .

1. Voer `git clone` in en plak de eerder verkregen waarde.

   Hier volgt een voorbeeld:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Wacht tot de opslagplaats op uw server heeft gekloond.

   >[!NOTE]
   >
   >Als de volgende foutenvertoningen, zorg ervoor u [ uw sleutel van SSH ](https://docs.github.com/articles/generating-ssh-keys/) met GitHub deelde:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Zorg ervoor dat u de vertakking van de gegevensopslagruimte met voorbeeldgegevens uitcheckt die overeenkomt met de vertakking die u hebt gebruikt vanuit de hoofdopslagplaats van `magento2` .

   Bijvoorbeeld:

   Als u de `2.4-develop` -vertakking van de Magento Open Source GitHub-opslagplaats hebt gebruikt, moet de vertakking Voorbeeldgegevens `2.4-develop` zijn.

   Als u de juiste vertakking wilt uitchecken, voert u de volgende opdracht uit vanuit de hoofdmap van de gegevensopslagruimte van het voorbeeld (ervan uitgaande dat u de vertakking `2.4-develop` nodig hebt):

   ```bash
   git checkout 2.4-develop
   ```

1. Wijzigen in `<app_root>` .
1. Voer de volgende opdracht in om symbolische koppelingen te maken tussen de bestanden die u hebt gekloond, zodat voorbeeldgegevens correct werken:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Wacht tot de opdracht is voltooid.

1. Zie [ plaatsen de toestemmingen en de eigendom van het dossiersysteem ](#set-file-system-ownership-and-permissions).

1. Voer de volgende opdracht uit:

   ```bash
   bin/magento setup:upgrade
   ```

### Klonen met HTTPS

U kunt als volgt de GitHub-voorbeeldgegevens klonen met behulp van het HTTPS-protocol:

1. In Webbrowser, ga naar de [ bewaarplaats van steekproefgegevens ](https://github.com/magento/magento2-sample-data).
1. Op de rechterkant van de pagina, onder het **kloon URL** gebied, klik **HTTPS**.
1. Klik **Exemplaar aan klembord**.

   In de volgende afbeelding ziet u een voorbeeld.

   ![ Kloon de bewaarplaats GitHub gebruikend HTTPS ](../../assets/installation/install_mage2_clone-https.png)

1. Wijzig de hoofdmap van de webserver.

   Voor Ubuntu is dit doorgaans `/var/www` en voor CentOS is het `/var/www/html` .

1. Voer `git clone` in en plak de eerder verkregen waarde.

   Hier volgt een voorbeeld:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Wacht tot de opslagplaats op uw server heeft gekloond.
1. Zorg ervoor dat u de vertakking van de gegevensopslagruimte met voorbeeldgegevens uitcheckt die overeenkomt met de vertakking die u hebt gebruikt vanuit de hoofdopslagplaats van `magento2` .

   Bijvoorbeeld:

   Als u de `2.4-develop` -vertakking van de Magento Open Source GitHub-opslagplaats hebt gebruikt, moet de vertakking Voorbeeldgegevens `2.4-develop` zijn.

   Als u de juiste vertakking wilt uitchecken, voert u de volgende opdracht uit vanuit de hoofdmap van de gegevensopslagruimte van het voorbeeld (ervan uitgaande dat u de vertakking `2.4-develop` nodig hebt):

   ```bash
   git checkout 2.4-develop
   ```

1. Wijzigen in `<magento_root>` .
1. Voer de volgende opdracht in om symbolische koppelingen te maken tussen de bestanden die u hebt gekloond, zodat voorbeeldgegevens correct werken:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Bijvoorbeeld:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Wacht tot de opdracht is voltooid.
1. Zie de volgende sectie.

>[!WARNING]
>
>Als u steekproefgegevens *na* het installeren van Adobe Commerce installeert, moet u het volgende bevel ook in werking stellen om het gegevensbestand en het schema bij te werken:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Eigendom en machtigingen van bestandssysteem instellen

Omdat het `php build-sample-data.php` -script symlinks creëert tussen de gegevensopslagplaats van het voorbeeld en de gegevensopslagplaats van de Magento Open Source, moet u de machtigingen voor het bestandssysteem en de eigendom in de gegevensopslagplaats van het voorbeeld instellen. Als u dit niet doet, treedt de storefront op in fouten.

U kunt als volgt de machtigingen en het eigendom van het bestandssysteem instellen in de gegevensopslagruimte van het voorbeeld:

1. Ga naar de kloonmap met voorbeeldgegevens.
1. Eigendom instellen:

   ```bash
   chown -R :<your web server group name> .
   ```

   Typische voorbeelden:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Rechten instellen:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Statische bestanden wissen:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## De installatie van voorbeeldgegevens voltooien

{{$include /help/_includes/sample-data-complete.md}}

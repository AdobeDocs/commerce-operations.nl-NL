---
title: Voorbeeldgegevensopslagruimten klonen
description: Voer de volgende stappen uit om Adobe Commerce- en Magento Open Source-voorbeeldgegevens te installeren door Git-opslagruimten te klonen.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# Voorbeeldgegevensopslagruimten klonen

Dit onderwerp bespreekt hoe te om steekproefgegevens te klonen en toe te voegen als u de bewaarplaats van Magento Open Source GitHub kloond. Deze methode is alleen bedoeld voor ontwikkelaars die een bijdrage leveren (dat wil zeggen ontwikkelaars die een bijdrage willen leveren aan de codebase Magento Open Source).

Als u geen bijdragende ontwikkelaar bent, kies één van de andere opties die in de inhoudstafel op de linkerkant van de pagina worden getoond.

Medewerkers kunnen deze methode gebruiken om voorbeeldgegevens te installeren *alleen* indien het volgende waar is:

* U gebruikt Magento Open Source
* U [gekloond de bewaarplaats van GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>U kunt voorbeeldgegevens gebruiken met `develop` vertakking (meer huidig) of een vrijgegeven vertakking (zoals `2.4` (stabieler). We raden u aan een vrijgegeven vertakking te gebruiken omdat deze stabieler is. Als u code aan de bewaarplaats bijdraagt en u de meest recente code nodig hebt, gebruik `develop` vertakking. Ongeacht de vertakking die u kiest, moet u [klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) de overeenkomstige tak van de bewaarplaats van Magento Open Source GitHub. Voorbeeldgegevens voor de `develop` vertakking kan worden gebruikt *alleen* met de Magento Open Source `develop` vertakking.

## De gegevensopslagplaats van de voorbeeldgegevens klonen

In deze sectie wordt beschreven hoe u voorbeeldgegevens kunt installeren door de gegevensopslagruimte voor voorbeeldgegevens te klonen. U kunt de gegevensopslagruimte van het voorbeeld op de volgende manieren klonen:

* Klonen met de opdracht [SSH-protocol](#clone-with-ssh)
* Klonen met de opdracht [HTTPS-protocol](#clone-with-https)

### Klonen met SSH

Om de bewaarplaats van GitHub van steekproefgegevens te klonen gebruikend het protocol van SSH:

1. Ga in een webbrowser naar de [gegevensopslagplaats](https://github.com/magento/magento2-sample-data).
1. Klik naast de naam van de vertakking op **SSH** in de lijst.
1. Klikken **Kopiëren naar klembord**

   In de volgende afbeelding ziet u een voorbeeld.

   ![Kloon de bewaarplaats van GitHub gebruikend SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Wijzig de hoofdmap van de webserver.

   Voor Ubuntu is het meestal `/var/www` en voor CentOS is dit `/var/www/html`.

1. Enter `git clone` en plak de eerder verkregen waarde.

   Hier volgt een voorbeeld:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Wacht tot de opslagplaats op uw server heeft gekloond.

   >[!NOTE]
   >
   >Als de volgende fout wordt weergegeven, controleert u of [gedeelde SSH-sleutel](https://docs.github.com/articles/generating-ssh-keys/) met GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Zorg ervoor dat u de vertakking van de gegevensopslagruimte van het voorbeeld uitcheckt die overeenkomt met de vertakking die u hebt gebruikt vanuit de hoofdmap `magento2` opslagplaats.

   Bijvoorbeeld:

   Als u het `2.4-develop` vertakking van de Magento Open Source GitHub bewaarplaats, zou de tak van Gegevens van de Steekproef moeten zijn `2.4-develop`.

   Als u het `2.4.3` vertakking van de Magento Open Source GitHub bewaarplaats, zou de tak van Gegevens van de Steekproef moeten zijn `2.4.3`.

   Als u de juiste vertakking wilt uitchecken, voert u de volgende opdracht uit vanuit de hoofdmap van de gegevensopslagruimte van het voorbeeld (ervan uitgaande dat u de opdracht `2.4.3` vertakking):

   ```bash
   git checkout 2.4.3
   ```

1. Wijzigen in `<app_root>`.
1. Voer de volgende opdracht in om symbolische koppelingen te maken tussen de bestanden die u hebt gekloond, zodat voorbeeldgegevens correct werken:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Wacht tot de opdracht is voltooid.

1. Zie [Machtigingen en eigendom van bestandssysteem instellen](#set-file-system-ownership-and-permissions).

1. Voer de volgende opdracht uit:

   ```bash
   bin/magento setup:upgrade
   ```

### Klonen met HTTPS

U kunt als volgt de GitHub-voorbeeldgegevens klonen met behulp van het HTTPS-protocol:

1. Ga in een webbrowser naar de [gegevensopslagplaats](https://github.com/magento/magento2-sample-data).
1. Aan de rechterkant van de pagina, onder de **URL klonen** veld, klikken **HTTPS**.
1. Klikken **Kopiëren naar klembord**.

   In de volgende afbeelding ziet u een voorbeeld.

   ![De GitHub-opslagplaats klonen met HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Wijzig de hoofdmap van de webserver.

   Voor Ubuntu is het meestal `/var/www` en voor CentOS is dit `/var/www/html`.

1. Enter `git clone` en plak de eerder verkregen waarde.

   Hier volgt een voorbeeld:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Wacht tot de opslagplaats op uw server heeft gekloond.
1. Zorg ervoor dat u de vertakking van de gegevensopslagruimte van het voorbeeld uitcheckt die overeenkomt met de vertakking die u hebt gebruikt vanuit de hoofdmap `magento2` opslagplaats.

   Bijvoorbeeld:

   Als u het `2.4-develop` vertakking van de Magento Open Source GitHub bewaarplaats, zou de tak van Gegevens van de Steekproef moeten zijn `2.4-develop`.

   Als u het `2.4.3` vertakking van de Magento Open Source GitHub bewaarplaats, zou de tak van Gegevens van de Steekproef moeten zijn `2.4.3`.

   Als u de juiste vertakking wilt uitchecken, voert u de volgende opdracht uit vanuit de hoofdmap van de gegevensopslagruimte van het voorbeeld (ervan uitgaande dat u de opdracht `2.4.3` vertakking):

   ```bash
   git checkout 2.4.3
   ```

1. Wijzigen in `<magento_root>`.
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
>Als u voorbeeldgegevens installeert *na* wanneer u Adobe Commerce of Magento Open Source installeert, moet u ook de volgende opdracht uitvoeren om de database en het schema bij te werken:
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## Eigendom en machtigingen van bestandssysteem instellen

Omdat `php build-sample-data.php` het script zorgt voor symlinks tussen de gegevensopslagplaats van het voorbeeld en uw gegevensopslagplaats van de Magento Open Source. U moet de machtigingen en het eigendom van het bestandssysteem instellen in de gegevensopslagplaats van het voorbeeld. Als u dit niet doet, treedt de storefront op in fouten.

U kunt als volgt de machtigingen en het eigendom van het bestandssysteem instellen in de gegevensopslagruimte van het voorbeeld:

1. Ga naar de kloonmap met voorbeeldgegevens.
1. Eigendom instellen:

   ```bash
   chown -R :<your web server group name> .
   ```

   Typische voorbeelden:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Machtigingen instellen:

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

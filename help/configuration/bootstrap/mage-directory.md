---
title: Basismappaden aanpassen
description: Gebruik de variabele MAGE_DIRS om een array van absolute paden in te stellen.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Basismappaden

De `MAGE_DIRS` Met een omgevingsvariabele kunt u aangepaste basismappaden en fragmenten van basis-URL&#39;s opgeven die door de toepassing Commerce worden gebruikt om absolute paden naar verschillende bestanden te maken of om URL&#39;s te genereren.

## MAGE_DIRS instellen

Een associatieve array opgeven waarvan de sleutels constanten zijn [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] en waarden zijn absolute paden van mappen of hun URL-paden.

U kunt instellen `MAGE_DIRS` op een van de volgende manieren:

- [De waarde van bootstrap-parameters instellen](../bootstrap/set-parameters.md)
- Gebruik een aangepast script voor het ingangspunt, zoals:

  ```php
  <?php
  /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

In het voorgaande voorbeeld worden paden ingesteld voor `[cache]` en `[media]` mappen naar `/mnt/nfs/cache` en `/mnt/nfs/media`, respectievelijk.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php

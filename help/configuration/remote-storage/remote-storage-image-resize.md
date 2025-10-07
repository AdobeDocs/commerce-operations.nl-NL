---
title: Afbeeldingsgrootte configureren voor externe opslag
description: U kunt schijfbronnen optimaliseren door de grootte van afbeeldingen op de server te configureren.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# Afbeeldingsgrootte configureren voor externe opslag

Adobe Commerce biedt standaard ondersteuning voor het vergroten of verkleinen van afbeeldingen aan de toepassingszijde. Door de externe opslagmodule in te schakelen kunt u Nginx echter gebruiken om de grootte van de afbeelding te verschuiven naar de serverzijde, waar u schijfbronnen kunt opslaan en schijfgebruik kunt optimaliseren.

In het volgende diagram ziet u hoe Nginx afbeeldingen in het cachegeheugen ophaalt, vergroot of verkleint en opslaat. Het formaat wordt bepaald door de parameters die in de URL zijn opgenomen, zoals hoogte en breedte.

![&#x200B; Nginx configuratie voor het verre beeld van de opslag resizing die de montages van het serverblok &#x200B;](../../assets/configuration/remote-storage-nginx-image-resize.png) tonen

>[!TIP]
>
>Voor Adobe Commerce op de projecten van de wolkeninfrastructuur, zie [&#x200B; verre opslag voor Commerce op de infrastructuur van de Wolk vormen &#x200B;](cloud-support.md)

## URL-indeling configureren in Adobe Commerce

Als u het formaat van afbeeldingen aan de serverzijde wilt wijzigen, moet u Adobe Commerce zodanig configureren dat er argumenten worden opgegeven voor de hoogte, breedte en locatie (URL) van de afbeelding.

**om Commerce voor server-zijbeeld te vormen resizing**:

1. In het _Admin_ paneel, klik **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Vouw **[!UICONTROL Url options]** uit in het rechterdeelvenster.

1. In de _media URL van de Catalogus formaat_ sectie, ontruim **[!UICONTROL Use system value]**.

1. Selecteer `Image optimization based on query parameters` URL in het **_media URL formaat van de Catalogus_** gebied.

1. Klik op **[!UICONTROL Save Config]**.

1. Ga aan de [&#x200B; configuratie Nginx &#x200B;](#configure-nginx) verder.

## Nginx configureren

Als u de grootte van afbeeldingen aan de serverzijde wilt blijven configureren, moet u het `nginx.conf` -bestand voorbereiden en een `proxy_pass` -waarde voor de door u gekozen adapter opgeven.

**om Nginx toe te laten om beelden** resize:

1. Installeer de [ Nginx module van de beeldfilter ][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Maak een `nginx.conf` -bestand op basis van het opgenomen sjabloon `nginx.conf.sample` -bestand. Bijvoorbeeld:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Facultatieve_] vorm een `proxy_pass` waarde voor uw specifieke adapter.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html

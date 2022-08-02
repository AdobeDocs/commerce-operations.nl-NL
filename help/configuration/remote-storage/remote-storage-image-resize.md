---
title: Afbeeldingsgrootte configureren voor externe opslag
description: U kunt schijfbronnen optimaliseren door de grootte van afbeeldingen op de server te configureren.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Afbeeldingsgrootte configureren voor externe opslag

Standaard, [!DNL Commerce] ondersteunt het vergroten/verkleinen van afbeeldingen aan de toepassingszijde. Door de externe opslagmodule in te schakelen kunt u Nginx echter gebruiken om de grootte van de afbeelding te verschuiven naar de serverzijde, waar u schijfbronnen kunt opslaan en schijfgebruik kunt optimaliseren.

In het volgende diagram ziet u hoe Nginx afbeeldingen in het cachegeheugen ophaalt, vergroot of verkleint en opslaat. Het formaat wordt bepaald door de parameters inbegrepen in URL, zoals hoogte en breedte.

![afbeelding vergroten/verkleinen](../../assets/configuration/remote-storage-nginx-image-resize.png)

## URL-indeling configureren in [!DNL Commerce]

Als u de grootte van afbeeldingen aan de serverzijde wilt wijzigen, moet u de optie Handel configureren om argumenten voor de hoogte, breedte en locatie (URL) van de afbeelding op te geven.

**Om Commerce voor server-kant beeld resizing te vormen**:

1. In de _Beheer_ deelvenster, klikt u op **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Vouw in het rechterdeelvenster uit **[!UICONTROL Url options]**.

1. In de _URL-indeling van catalogusmedia_ sectie, duidelijk **[!UICONTROL Use system value]**.

1. Selecteer `Image optimization based on query parameters` URL in de **_URL-indeling van catalogusmedia_** veld.

1. Klik op **[!UICONTROL Save Config]**.

1. Doorgaan naar de [Nginx-configuratie](#configure-nginx).

## Nginx configureren

Als u de grootte van afbeeldingen op de server wilt blijven configureren, moet u de knop `nginx.conf` en een `proxy_pass` waarde voor de door u gekozen adapter.

**Nginx inschakelen om het formaat van afbeeldingen te wijzigen**:

1. Installeer de [Filtermodule Nginx-afbeelding][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Een `nginx.conf` bestand op basis van de opgenomen sjabloon `nginx.conf.sample` bestand. Bijvoorbeeld:

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

1. [_Optioneel_] Een `proxy_pass` waarde voor uw specifieke adapter.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html

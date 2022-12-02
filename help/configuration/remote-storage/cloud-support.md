---
title: Externe opslag voor handel in cloudinfrastructuur
description: Zie de richtlijnen voor het instellen van externe opslag voor Adobe Commerce op cloudinfrastructuur.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Externe opslag configureren voor handel op Cloud-infrastructuur

Als u ervoor kiest om de oplossing voor externe opslag te gebruiken met een Adobe Commerce-project voor cloudinfrastructuur, gebruikt u de [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) richtsnoeren in de _Snel_ documentatie om ervoor te zorgen dat Fastly Image Optimization werkt met AWS S3.

Wees voorbereid met uw [Snelle referenties](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Bij Pro-projecten gebruikt u SSH om verbinding te maken met uw server en krijgt u de snelste referenties van de `/mnt/shared/fastly_tokens.txt` bestand. Staging- en productieomgevingen hebben unieke gegevens. U moet de geloofsbrieven voor elke milieu krijgen.

De externe opslag voor cloudprojecten blijven instellen met de volgende taken:

1. Een [Snelle ondersteuning voor integratie](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. VCL-logica maken voor [AWS S3-verificatie](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. VCL-logica maken voor [back-endverzoeken aan de AWS S3 bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).

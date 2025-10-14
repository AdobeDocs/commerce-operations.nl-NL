---
title: Hoe te om tot  [!DNL Cloud Automation Patching Service (CAPS)] toegang te hebben
description: Leer hoe te om tot toegang te hebben en te gebruiken  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Toegang krijgen tot [!DNL Cloud Automation Patching Service (CAPS)]

## Vereisten

[!DNL CAPS] gebruikt het op rollen gebaseerde toegangsbeheer van Adobe Commerce Cloud. Het toegangsniveau in de Cloud Console bepaalt wat u kunt doen met [!DNL CAPS].

### Wie kan [!DNL CAPS] gebruiken?

* **Admin van het Project** - kan flarden op alle milieu&#39;s toepassen of terugkeren
* **Medewerker** - kan flarden op hun toegewezen milieu&#39;s toepassen of terugkeren
* **Kijker** - kan slechts het project en de milieu&#39;s bekijken, geen toegestane acties

### Hoe te om toegang tot een project te verzoeken

Als u geen projecten ziet in de gebruikersinterface van [!DNL CAPS] , moet u toegang aanvragen bij de juiste persoon:

* Neem contact op met de eigenaar van de account of de projectbeheerder van het project
* Ze geven u de juiste rol via de Cloud Console
* Nadat u toegang hebt verleend, kunt u zich aanmelden bij de Cloud Console voor gebruik van [!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS] volgt hetzelfde machtigingsmodel als Adobe Commerce Cloud, dus uw toegangsniveau in de Cloud Console bepaalt wat u kunt doen met [!DNL CAPS] .

## Toegang verkrijgen tot [!DNL CAPS]

Het hulpmiddel CAPS is beschikbaar van het plaats-brede dashboard van het Hulpmiddel van de Analyse in [ https://supportinsights.adobe.com/commerce/ ](https://supportinsights.adobe.com/commerce/). Onder het tabblad Patchautomatisering kunt u uw project en omgeving selecteren.

1. Navigeer aan het Hulpmiddel van de Analyse van plaats-brede in [ https://supportinsights.adobe.com/commerce/ ](https://supportinsights.adobe.com/commerce/).
1. Klik op het tabblad [!UICONTROL Patching Automation] in de interface.
1. Selecteer het project en de omgeving waarop u patches wilt toepassen.
1. Bekijk de beschikbare patches en hun compatibiliteitsstatus.
1. Selecteer de patches die u wilt toepassen of herstellen.

## Toegang tot productieomgeving

Voor productieomgevingen zijn aanvullende waarborgen van toepassing:

* **wijze van het Onderhoud** - moet worden toegelaten
* **Cron banen** - moet worden onbruikbaar gemaakt
* **de dialoog van de Bevestiging** - moet vóór het werk worden voltooid

>[!IMPORTANT]
>
>Voor het aanbrengen van patches in de productieomgeving is een goede voorbereiding en bescherming vereist om onbedoelde verstoringen te voorkomen.

## Verwante onderwerpen

* [CAPS-introductie](intro.md)
* [Workflow](workflow.md)
* [Aanbevolen procedures](best-practices.md)
* [Problemen oplossen](troubleshooting.md)

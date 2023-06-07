---
title: Toegang krijgen [!DNL Site-Wide Analysis Tool]
description: Leer hoe u toegang krijgt tot de [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Hoe te om tot [!DNL Site-Wide Analysis Tool]

Er zijn twee manieren waarop u toegang kunt krijgen tot [!DNL Site-Wide Analysis Tool Dashboard].

U hebt toegang tot de [!DNL dashboard] van [[!DNL Site-Wide Analysis Tool] Website](https://supportinsights.adobe.com/commerce) rechtstreeks **(alleen voor Adobe Commerce op cloudinfrastructuur)** en meld u aan bij uw Adobe ID of open de [!DNL dashboard] van je winkel [!DNL Admin Panel].

De [!DNL Site-Wide Analysis Tool] service is beschikbaar in [productiemodus](https://docs.magento.com/user-guide/magento/installation-modes.html) for [!DNL Admin] gebruikers met toegangsrechten voor gebruikers [rolbronnen](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Als u een installatie van Adobe Commerce in de bedrijfsruimten hebt, moet u een [agent](../site-wide-analysis-tool/installation.md) op uw infrastructuur om het hulpmiddel te gebruiken.

![Analysedashboard voor de hele site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## Optie 1: Aanmelden bij uw [!DNL Site-Wide Analysis Tool Dashboard] rechtstreeks van de [!DNL Site-Wide Analysis Tool] domein (alleen voor Adobe Commerce op cloudinfrastructuur)

An **[!DNL Adobe ID]is vereist** toegang tot [!DNL Commerce] account.
Als u al een [!DNL Commerce] account, maar u hebt geen [!DNL Adobe ID]kunt u er een maken tijdens het aanmeldingsproces.

1. Ga naar [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Klik op de knop **[!UICONTROL Sign in with Adobe ID]** en volgt u de aanwijzingen.

   ![Analysedashboard voor de hele site](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]aanmeldingsscherm*

1. Accepteer de voorwaarden.

1. **<u>Opmerking</u>:** Je account moet het recht hebben op **[!DNL Support Permissions]** om toegang te krijgen tot [!DNL Site-Wide Analysis Tool Dashboard].
Meer informatie vindt u in [Delen a [!DNL Commerce] account](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) in onze gebruikershandleiding.

## Optie 2: Aanmelden bij uw [!DNL Site-Wide Analysis Tool Dashboard] van je winkel [!DNL Admin Panel]

### Stap 1: Machtigingen verifiëren

Controleer of de [!DNL Admin] gebruikersaccount heeft toegang tot [!DNL Site-Wide Analysis Tool] via hun [toegewezen gebruikersrol](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>De [!DNL Site-Wide Analysis Tool] rolinebron (machtiging) is **niet** automatisch toegewezen. Het MOET geactiveerd worden voor de gebruikersrol en de rol die afzonderlijk is toegewezen aan elke gebruikersaccount in de [!UICONTROL Admin].

Voor de aangepaste rol die nodig is [!DNL Site-Wide Analysis Tool] toegang, doe het volgende:

1. Selecteer **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** rolbron.

   ![Analysedashboard voor de hele site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]machtiging geselecteerd voor de rol*

1. Klikken **[!UICONTROL Save Role]**.

1. Melden aan gebruikers aan wie die rol is toegewezen om zich af te melden bij de [!DNL Admin]en meld u opnieuw aan.

>[!NOTE]
>
>Als u hebt gecontroleerd dat de gebruikersaccount gemachtigd is om toegang te krijgen tot de [!DNL Site-Wide Analysis Tool] en de gebruiker ontvangt een fout van 403 wanneer hij probeert toegang te krijgen tot het gereedschap van de [!DNL Admin], uw instantie van Adobe Commerce op cloudinfrastructuur kan HTTP-toegangsbeheer hebben ingeschakeld. De [!DNL Site-Wide Analysis Tool] Het dashboard wordt NIET ondersteund als HTTP Auth is ingeschakeld. Raadpleeg voor meer informatie over het oplossen van dit probleem onze [Ondersteuningsartikel](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Stap 2: Toegang [!DNL Site-Wide Analysis Tool]

1. Op de *[!UICONTROL Admin]* zijbalk, ga naar **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Analysedashboard voor de hele site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]locatie in de [!DNL Admin Panel] in Adobe Commerce*

1. Lees de *Gebruiksvoorwaarden* voor de [!DNL Site-Wide Analysis Tool] en klik op **[!UICONTROL Accept]** om door te gaan.

   Elke gebruiker moet de Gebruiksvoorwaarden voor de sessie accepteren. Deze stap wordt herhaald voor elke het programma geopende zitting.


1. Klik boven aan het dashboard op de tab die u wilt zien.

   ![Analysedashboard voor de hele site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informatie*

## Rapporten genereren op basis van het dialoogvenster [!DNL Site-Wide Analysis Tool Dashboard]

1. Klik in de rechterbovenhoek van het dashboard op **[!UICONTROL Generate Report]**.

1. Schakel het selectievakje voor elk **[!UICONTROL Type]** en **[!UICONTROL Priority]** het plaatsen die u in het rapport wilt omvatten.

1. Klikken **[!UICONTROL Generate Report]**.

   ![Analysedashboard voor de hele site](../../assets/tools/swat-report-settings.png)
   *Rapportinstellingen*

| TAB | BESCHRIJVING |
| --- | --- |
| Dashboard | Toont de gezondheid van uw systeem met huidige berichten en aanbevelingen door prioriteit. |
| Informatie | Verstrekt de informatie van het klantencontact en een samenvatting van huidige kaartjes, met gedetailleerde informatie over elk geïnstalleerd product van Adobe Commerce. |
| Recommendations | Hier worden aanbevelingen weergegeven op basis van best practices voor het oplossen van problemen die op uw site zijn aangetroffen. |
| Uitzonderingen | Hiermee worden fouten weergegeven die door de toepassing worden gegenereerd als gevolg van abnormale omstandigheden zonder een fouthandler. |
| Extensies | Hier worden alle extensies van derden en bibliotheken van derden weergegeven. |

>[!NOTE]
>
>Na toepassing van een aanbeveling kan het een paar dagen duren voordat de aanbeveling in de [!DNL Site-Wide Analysis Tool Dashboard] of gegenereerd rapport.

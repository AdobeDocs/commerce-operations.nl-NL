---
title: Hoe te om tot  [!DNL Site-Wide Analysis Tool] toegang te hebben
description: Leer hoe u het dashboard Analysehulpprogramma voor de hele site opent vanuit het Adobe Commerce-beheerdeelvenster. Ontdek gebruikerstoestemmingen en rolvereisten.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Toegang tot de [!DNL Site-Wide Analysis Tool]

U hebt toegang tot het dashboard van [!DNL Site-Wide Analysis Tool] via het [!UICONTROL Admin Panel] -bestand van uw winkel.

De [!DNL Site-Wide Analysis Tool] dienst is beschikbaar op [&#x200B; productiemodus &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes) voor [!UICONTROL Admin] gebruikers met toestemming om tot gebruiker [&#x200B; rolmiddelen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) toegang te hebben.

>[!NOTE]
>
>Vanaf 23 april 2024 is [!DNL Site-Wide Analysis Tool] buiten bedrijf gesteld en is het niet langer beschikbaar voor Adobe Commerce-klanten op locatie.


![&#x200B; plaats-brede het dashboard van de Analyse &#x200B;](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

>[!NOTE]
>
>Uw account moet het recht hebben op **[!DNL Support Permissions]** om toegang te krijgen tot [!DNL Site-Wide Analysis Tool Dashboard] .
>&#x200B;>Zie meer details in [&#x200B; Deel a  [!DNL Commerce]  rekening &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) in onze gebruikersgids.

## Aanmelden bij [!DNL Site-Wide Analysis Tool Dashboard] vanuit de winkel [!UICONTROL Admin Panel]

### Stap 1: Machtigingen verifiëren

Verifieer dat de [!UICONTROL Admin] gebruikersrekening toestemming heeft om tot [!DNL Site-Wide Analysis Tool] door hun [&#x200B; toegewezen gebruikersrol &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) toegang te hebben.

>[!IMPORTANT]
>
>Het [!DNL Site-Wide Analysis Tool] rolmiddel (toestemming) is **niet** auto-toegewezen. Het MOET worden geactiveerd voor de gebruikersrol en de rol die afzonderlijk wordt toegewezen aan elke gebruikersaccount in de [!UICONTROL Admin] .

Ga als volgt te werk voor de aangepaste rol die [!DNL Site-Wide Analysis Tool] toegang nodig heeft:

1. Selecteer de rolbron **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** .

   ![&#x200B; plaats-brede het dashboard van de Analyse &#x200B;](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]machtiging geselecteerd voor de rol*

1. Klik op **[!UICONTROL Save Role]**.

1. Meld gebruikers aan aan wie die rol is toegewezen om zich af te melden bij de [!DNL Admin] en meld u opnieuw aan.

>[!NOTE]
>
>Als u hebt gecontroleerd dat de gebruikersaccount toestemming heeft om toegang te krijgen tot [!DNL Site-Wide Analysis Tool] en de gebruiker een fout van 403 ontvangt wanneer deze probeert toegang te krijgen tot het hulpprogramma vanuit [!UICONTROL Admin] , kan het zijn dat in uw Adobe Commerce-instantie in de cloudinfrastructuur HTTP-toegangsbeheer is ingeschakeld. Het dashboard van [!DNL Site-Wide Analysis Tool] wordt NIET ondersteund als u HTTP Auth hebt ingeschakeld. Voor meer informatie over het oplossen van deze kwestie, zie ons [&#x200B; artikel van de Steun &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento).

### Stap 2: Toegang [!DNL Site-Wide Analysis Tool]

1. Ga op de zijbalk van *[!UICONTROL Admin]* naar **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** .

   ![&#x200B; plaats-brede het dashboard van de Analyse &#x200B;](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]-locatie in de [!UICONTROL Admin Panel] in Adobe Commerce*

1. Lees de *Voorwaarden van Gebruik* voor [!DNL Site-Wide Analysis Tool] en klik **[!UICONTROL Accept]** om verder te gaan.

   Elke gebruiker moet de Gebruiksvoorwaarden voor de sessie accepteren. Deze stap wordt herhaald voor elke het programma geopende zitting.


1. Klik boven aan het dashboard op de tab die u wilt zien.

   ![&#x200B; plaats-brede het dashboard van de Analyse &#x200B;](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]information*

## Rapporten genereren vanuit de [!DNL Site-Wide Analysis Tool Dashboard]

1. Klik in de rechterbovenhoek van het dashboard op **[!UICONTROL Generate Report]** .

1. Schakel het selectievakje in voor elke instelling **[!UICONTROL Type]** en **[!UICONTROL Priority]** die u in het rapport wilt opnemen.

1. Klik op **[!UICONTROL Generate Report]**.

   ![&#x200B; plaats-brede het dashboard van de Analyse &#x200B;](../../assets/tools/swat-report-settings.png)
   *Montages van het Rapport*

| TAB | BESCHRIJVING |
| --- | --- |
| Dashboard | Toont de gezondheid van uw systeem met huidige berichten en aanbevelingen door prioriteit. |
| Informatie | Verstrekt de informatie van het klantencontact en een samenvatting van huidige kaartjes, met gedetailleerde informatie over elk geïnstalleerd product van Adobe Commerce. |
| Aanbevelingen | Hier worden aanbevelingen weergegeven op basis van best practices voor het oplossen van problemen die op uw site zijn aangetroffen. |
| Uitzonderingen | Hiermee worden fouten weergegeven die door de toepassing worden gegenereerd als gevolg van abnormale omstandigheden zonder een fouthandler. |
| Extensies | Hier worden alle extensies van derden en bibliotheken van derden weergegeven. |

>[!NOTE]
>
>Nadat u een aanbeveling hebt toegepast, kan het een paar dagen duren voordat deze wordt bijgewerkt in het [!DNL Site-Wide Analysis Tool Dashboard] -rapport of het gegenereerde rapport.

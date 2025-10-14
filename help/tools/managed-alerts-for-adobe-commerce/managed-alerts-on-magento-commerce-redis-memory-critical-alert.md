---
title: 'Beheerde alarm op Adobe Commerce: [!DNL Redis]  geheugen kritieke alarm'
description: Dit artikel verstrekt het oplossen van problemenstappen voor wanneer u a  [!DNL Redis]  geheugen kritieke alarm voor Adobe Commerce in  [!DNL New Relic] ontvangt. Er is onmiddellijke actie vereist om het probleem op te lossen.
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: 1233889e-8c02-4ad6-b12c-683010b7bf35
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Beheerde waarschuwingen over Adobe Commerce: [!DNL Redis] kritieke geheugenwaarschuwing

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een [!DNL Redis] kritieke waarschuwing voor Adobe Commerce ontvangt in [!DNL New Relic] . Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![&#x200B; new_relic_redis_memory_critical.png &#x200B;](../../assets/managed-alerts/new_relic_redis_memory_critical.png)

## Betrokken producten en versies

Alle versies van Adobe Commerce op de Pro-planarchitectuur van de cloud-infrastructuur

## Probleem

U zult een alarm in [!DNL New Relic] ontvangen als u tot [&#x200B; Beheerde alarm voor Adobe Commerce &#x200B;](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om handelaren een standaardreeks waarschuwingen te geven met behulp van inzichten van support en engineering.

**<u>doe!</u>**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen verwijzen naar [&#x200B; toelaten of onbruikbaar maken onderhoudswijze &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [&#x200B; handhaaf de lijst van vrijgestelde IP adressen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) in de Gids van de Installatie van Commerce.

**<u>niet!</u>**

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexeerders of extra kranen uit die extra druk op CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (d.w.z. belangrijke acties in de Admin van Commerce zoals gegevensinvoer/uitvoer, het spoelen van media, het redden van categorieën met een groot aantal toegewezen producten, en massa-updates).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

**omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u Stap 1 voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.**

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar [&#x200B; Spoor uw steunkaartjes &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) in de Kennisbank van de Steun van Commerce. Ondersteuning heeft mogelijk al een drempelwaardewaarschuwing van [!DNL New Relic] ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:

   * Reden van contactpersoon: selecteer **[!UICONTROL New Relic CRITICAL alert received]**.
   * Beschrijving van de signalering.
   * [[!DNL New Relic]  inherente verbinding &#x200B;](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Dit is inbegrepen in uw [&#x200B; Beheerde Alarm voor Adobe Commerce &#x200B;](managed-alerts-for-magento-commerce.md).

1. Als geen steunkaartje bestaat, controleer als [!DNL Redis] Gebruikt Geheugen stijgt of daalt door [&#x200B; te gaan one.newrelic.com &#x200B;](https://login.newrelic.com) > **[!UICONTROL Infrastructure]** > **[!UICONTROL Third-party services]** pagina, selecteer het [!DNL Redis] dashboard. Als het stabiel of het verhogen is, [&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) om uw cluster te hebben, of verhoog de `maxmemory` grens aan het volgende niveau.
1. Als u niet de oorzaak van verhoogd [!DNL Redis] geheugengebruik kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Controleren op onjuiste extensies van derden:

   * Probeer een correlatie te vinden met recent geïnstalleerde extensies van derden en de tijd waarop de uitgave is gestart.
   * Controleer extensies die mogelijk van invloed zijn op de Adobe Commerce-cache en zorgen dat de cache snel groter wordt. Bijvoorbeeld, de blokken van de douanelay-out, het met voeten treden van geheim voorgeheugenfunctionaliteit, en het opslaan van grote hoeveelheden gegevens in geheim voorgeheugen.

1. Als er geen bewijs van misleidende uitbreidingen is, [&#x200B; installeer recentste flarden om  [!DNL Redis]  kwesties voor Adobe Commerce op wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues) te bevestigen.
1. Als de bovenstaande stappen u niet helpen de bron van de uitgave te identificeren of problemen op te lossen, denk na toelatend L2 geheime voorgeheugen om netwerkverkeer tussen app en [!DNL Redis] te verminderen. Voor algemene informatie over wat L2 geheime voorgeheugen is, verwijs naar [&#x200B; L2 caching in de toepassing van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cache/level-two-cache) in de Gids van de Configuratie van Commerce. Ga als volgt te werk om L2-cache in te schakelen voor cloudinfrastructuur:

   * Voer een upgrade uit voor ECE-gereedschappen als de versie onder 2002.1.2 valt.
   * Vorm L2 Geheime voorgeheugen door [&#x200B; te gebruiken REDIS \_BACKEND veranderlijke &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) en het bijwerken van het `.magento.env.yaml` dossier:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```

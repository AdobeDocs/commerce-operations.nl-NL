---
title: 'Beheerde alarm op Adobe Commerce: [!DNL Redis]  geheugenalarm'
description: Dit artikel verstrekt het oplossen van problemenstappen voor wanneer u a  [!DNL Redis]  waarschuwingsalarm voor Adobe Commerce in  [!DNL New Relic] ontvangt. Er is onmiddellijk actie vereist.
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: f71b5e83-fb6c-4183-87c7-f41cbdf4c684
source-git-commit: 882bc7a8747f38a7721d2e61befc4e2acef2d998
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Beheerde waarschuwingen over Adobe Commerce: [!DNL Redis] waarschuwing voor het geheugen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een [!DNL Redis] waarschuwingsbericht voor Adobe Commerce ontvangt in [!DNL New Relic] . Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd:

![ new_relic_redis_memory_warning.png ](../../assets/managed-alerts/new_relic_redis_memory_warning.png)

## Betrokken producten en versies

Alle versies van Adobe Commerce op cloudinfrastructuur Pro plannen.

## Probleem

U zult een alarm in [!DNL New Relic] ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe ontwikkeld om handelaren een standaardreeks waarschuwingen te geven met behulp van inzichten van support en engineering.

**<u>doe!</u>**

* U wordt aangeraden de geplande implementatie af te breken totdat deze waarschuwing wordt gewist.
* Als uw site niet reageert of volledig reageert, zet u uw site onmiddellijk in de onderhoudsmodus. Voor stappen, verwijs naar [ toelaten of onbruikbaar maken onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in de Gids van de Installatie van Commerce.
* Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) in de Gids van de Installatie van Commerce.

**<u>niet!</u>**

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexeerders of extra kranen uit die extra druk op CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (d.w.z. belangrijke acties in Commerce Admin zoals invoer/uitvoer van gegevens, het spoelen van media, het redden van categorieën met een groot aantal toegewezen producten, en massa-updates).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

1. Controle als [!DNL Redis] Gebruikt Geheugen stijgt of door [ te gaan one.newrelic.com ](https://login.newrelic.com/login) > **Infrastructuur** > **de diensten van de Derde** pagina daalt, selecteer het [!DNL Redis] dashboard. Als het stabiel of het verhogen is, [ voorlegt een steunkaartje ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) om uw cluster te hebben, of verhoog de `maxmemory` grens aan het volgende niveau.
1. Als u niet de oorzaak van verhoogd [!DNL Redis] geheugengebruik kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Controleren op onjuiste extensies van derden:
   * Probeer een correlatie te vinden met recent geïnstalleerde extensies van derden en de tijd waarop de uitgave is gestart.
   * Controleer extensies die mogelijk van invloed zijn op de Adobe Commerce-cache en zorgen dat de cache snel groter wordt. Bijvoorbeeld, de blokken van de douanelay-out, het met voeten treden van geheim voorgeheugenfunctionaliteit, en het opslaan van grote hoeveelheden gegevens in geheim voorgeheugen.
1. Als de bovenstaande stappen u niet helpen de bron van de uitgave te identificeren of problemen op te lossen, denk na toelatend L2 geheime voorgeheugen om netwerkverkeer tussen app en [!DNL Redis] te verminderen. Voor algemene informatie over wat L2 geheime voorgeheugen is, verwijs naar [ L2 caching in de toepassing van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/level-two-cache) in de Gids van de Configuratie van Commerce. Ga als volgt te werk om L2-cache in te schakelen voor cloudinfrastructuur:
   * Voer een upgrade uit voor ECE-gereedschappen als de versie onder 2002.1.2 valt.
   * Vorm L2 Geheime voorgeheugen door [ te gebruiken REDIS \_BACKEND veranderlijke ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) en het bijwerken `.magento.env.yaml` dossier:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```

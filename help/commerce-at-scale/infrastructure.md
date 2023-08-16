---
title: Adobe Commerce en Adobe Experience Manager Infrastructure Alignment
description: Lijn uw Adobe Commerce- en Adobe Experience Manager-infrastructuur uit om acceptabele time-outs en verbindingslimieten in te stellen.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Infrastructuuruitlijning (time-outs en verbindingslimieten)

Er zijn instellingen met AEM en Adobe Commerce en omringende infrastructuur, zoals taakverdelingsmechanisme, die moeten worden uitgelijnd. Deze instellingen hebben betrekking op verbindingslimieten en time-outinstellingen.

Een verkeerde afstemming tussen deze limieten zou betekenen dat verbindingen aan AEM kant zouden kunnen worden vertraagd, terwijl Adobe Commerce in staat is om meer verbindingen af te handelen. Voor de time-outinstellingen kan een verkeerde uitlijning betekenen dat er time-outfouten optreden aan AEM kant, terwijl Adobe Commerce nog steeds een aanvraag verwerkt.

Voor de time-outinstellingen moeten de instellingen worden gecontroleerd en uitgelijnd om te voorkomen dat er 503 time-outfouten verschijnen wanneer deze onder belasting zijn. Er zijn verschillende instellingen voor de infrastructuur en time-out van de toepassing die u wilt controleren:

![Genummerd diagram dat de onderbrekingen en verbindingsgrenzen voor AEM beschrijft](../assets/commerce-at-scale/timeout-settings.svg)

## AEM taakverdelingsmechanisme

Ervan uitgaande dat er een taakverdelingsmechanisme voor AWS-toepassingen in de infrastructuur en meerdere verzenders/uitgevers is, moet voor het taakverdelingsmechanisme rekening worden gehouden met de volgende instellingen:

1. De gezondheidscontroles van uitgevers moeten worden herzien om te voorkomen dat verzenders onnodig vroeg uit de dienst vallen vanwege de oplaadpieken. De time-outinstellingen van de taakverdelingscontrole moeten worden afgestemd op de time-outinstellingen van de uitgever.

   ![Screenshot met AEM health checks van taakverdelingsmechanisme](../assets/commerce-at-scale/health-checks.png)

1. De doelgroepkleverheid van de Dispatcher kan worden uitgeschakeld en het taakverdelingsalgoritme van de Round Robin kan worden gebruikt. Hierbij wordt ervan uitgegaan dat er geen AEM specifieke functionaliteit is of AEM gebruikerssessies worden gebruikt waarvoor de sessiestandaardigheid moet worden ingesteld. Hierbij wordt ervan uitgegaan dat gebruikersaanmelding en sessiebeheer alleen op Adobe Commerce via GraphQL plaatsvinden.

   ![Schermafbeelding met kenmerken voor AEM sessievasthouding](../assets/commerce-at-scale/session-stickiness.png)

1. Houd er rekening mee dat als u sessiestandaardigheid inschakelt, aanvragen naar Snelheid niet in de cache kunnen worden opgeslagen. Standaard worden pagina&#39;s niet met de koptekst Set-Cookies in de cache geplaatst. Adobe Commerce stelt cookies in, zelfs op cacheable pages (TTL > 0), maar de standaard snelle VCL stript deze cookies op cacheable pages zodat Fastly caching werkt. Als pagina&#39;s niet in cache worden geplaatst, controleert u eventueel gebruikte aangepaste cookies en uploadt u ook de Fastly VCL en controleert u de site opnieuw.

## Time-outinstellingen voor verzending

De /timeout in de verzender &quot;renders&quot;opties specificeert de verbindingstijd die tot de AEM publicatieinstantie in milliseconden toegang heeft. Deze moet worden gecontroleerd en de standaardinstelling &quot;0&quot; (onbepaalde time-out) moet worden gebruikt als er een afzonderlijk taakverdelingsmechanisme aanwezig is voor het afhandelen van de time-outinstellingen.

Als er geen taakverdelingsmechanisme in de infrastructuur is, zouden de onderbrekingsmontages in plaats daarvan in de verzender /timeout montages moeten worden gespecificeerd, met een waarde die de onderbrekingsmontages van GraphQL in de uitgever aanpast.

## Uitgevers

GraphQL-verbindingslimieten en time-outs voor uitgevers: aanvankelijk zouden de Max HTTP-verbindingen in de Adobe Commerce CIF GraphQL Client Configuration Factory OSGI-instellingen moeten worden ingesteld op de standaard snelste maximale verbindingslimiet, die momenteel is ingesteld op 200. Zelfs als er meerdere uitgevers in het AEM bedrijf zijn, moet de limiet voor elke uitgever hetzelfde zijn, overeenkomstig de instelling Snelst. De reden hiervoor is dat in sommige gevallen één uitgever meer verkeer zou kunnen verwerken dan de andere uitgevers, als een verbonden verzender bijvoorbeeld uit het landbouwbedrijf wordt gehaald. Dit zou betekenen dat al verkeer door de enige resterende verzender en uitgevers zou worden verpletterd, in dit geval kan één enkele uitgever alle verbindingen van HTTP dan nodig hebben.

De &quot;standaardmethode van HTTP&quot;zou van POST aan GET moeten worden geplaatst. Alleen aanvragen van GET worden in de cache van Adobe Commerce GraphQL opgeslagen en daarom moet de standaardmethode altijd worden ingesteld op GET.

De time-out van de http-verbinding en de http-socket moet worden ingesteld op een waarde die overeenkomt met de time-out Fastly.

De volgende afbeelding toont de Magento CIF GraphQL Client Configuration Factory. De hier getoonde instellingen zijn alleen voorbeelden en moeten per geval worden aangepast:

![Screenshot van de configuratieinstellingen van het Commerce-integratieframework](../assets/commerce-at-scale/cif-config.png)

In de volgende afbeeldingen ziet u de snelste achtergrondconfiguraties. De hier getoonde instellingen zijn alleen voorbeelden en moeten per geval worden aangepast:

![Schermafbeelding van de configuratie-instellingen voor Admin-beheer voor handel voor snel](../assets/commerce-at-scale/cif-config-advanced.png)

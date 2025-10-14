---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Leer over  [!DNL Cloud Automation Patching Service (CAPS)], zijn gebruik, hoe te om tot het toegang te hebben, en beste praktijken voor geautomatiseerde het opsluiten
hide: true
hidefromtoc: true
source-git-commit: 6db46ef802edaeeec8a6986d4621ea647b171b0c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

[!DNL Cloud Automation Patching Service] ([!DNL CAPS]) is een hulpmiddel dat het proces automatiseert om flarden voor Adobe Commerce op Cloud milieu&#39;s toe te passen en terug te keren. Het biedt Commerce-projectbeheerders een gestroomlijnde workflow voor het toepassen en herstellen van patches met ingebouwde validatie- en health checks om ervoor te zorgen dat de cloudomgevingen stabiel en veilig blijven.

Deze handleiding is ontworpen voor Adobe Commerce Cloud-handelaren en -partners die hun patchproces willen stroomlijnen, het risico op patchgerelateerde problemen willen verminderen, de beveiliging en stabiliteit van hun omgeving willen verbeteren en routinematige patchbewerkingen willen automatiseren.

## [!DNL CAPS] onderwerpen

* **[hoe te om tot](access.md)** toegang te hebben
* **[Werkschema](workflow.md)**
* **[Beste praktijken](best-practices.md)**
* **[het Oplossen van problemen](troubleshooting.md)**

## Overzicht van gereedschappen

* **Interface UI**
   * Realtime flardbeschikbaarheid en statusvertoning voor specifieke project en omgevingscombinaties
   * Uitgebreide patchstatusinformatie die voortgang, fouten en andere relevante berichten weergeeft
   * [!UICONTROL Patch Management Dashboard] for:
      * Beschikbare patches weergeven
      * Patches toepassen met één muisklik
      * Eerder toegepaste patches herstellen
      * Status en resultaten van patchbewerkingen controleren

* **Geautomatiseerde het patchen dienst met gestructureerd werkschema**
   * **Voorlopige controle** - bevestigt flardverenigbaarheid en omgevingsbereidheid
   * **het Patching** - past of keert automatisch flarden in integratiemilieu&#39;s toe terug
   * **Bevestiging** - voert gezondheidscontroles uit en verzekert kritieke functionaliteit niet wordt beïnvloed

* **de eigenschappen van de Veiligheid**
   * Maakt tijdelijke integratieomgevingen voor testen
   * Valideert flardverenigbaarheid vóór toepassing
   * Biedt automatische terugdraaiing van validatiefouten
   * Past patches toe op de `m2-hotfixes` -map, waarbij deze automatisch worden verwijderd tijdens het omkeren

## Integratie met Adobe Commerce Cloud

[!DNL CAPS] is volledig geïntegreerd met de Adobe Commerce Cloud-infrastructuur en werkt naadloos met uw bestaande cloudomgevingen. Het gebruikt cloud-native functies voor optimale prestaties, biedt gedetailleerde registratie en controle en integreert met de ondersteuningsprogramma&#39;s van Adobe Commerce Cloud.

## Vaak voorkomende gevallen

* **de flarden van de Veiligheid** - pas snel kritieke veiligheidsupdates toe
* **het terugschroeven van prijzen van de Reparatie** - keer veilig problematische die flarden terug door [!DNL CAPS] worden toegepast
* **de naleving van de Veiligheid** - handhaaf veiligheidsnormen met geautomatiseerd het opsluiten
* **Operationele stabiliteit** - verzeker milieustabiliteit door geautomatiseerde bevestiging

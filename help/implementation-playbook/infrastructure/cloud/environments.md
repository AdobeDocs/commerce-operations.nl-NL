---
title: Cloud-infrastructuuromgevingen
description: Gebruik de juiste omgevingen voor de juiste gebruiksscenario's.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Omgevingen

Adobe Commerce on cloud Infrastructure Pro-architectuur ondersteunt omgevingen die u kunt gebruiken voor het ontwikkelen, testen en starten van uw winkel. Elke omgeving bevat een database en een webserver. De vier omgevingen die door Adobe Commerce worden gebruikt zijn:

- **Integratie**—Verstrekt één enkele milieutak en u kunt tot vier extra milieutakken tot stand brengen. Dit staat voor een maximum van vijf actieve takken toe die aan Platform-as-a-Dienst (PaaS) containers worden opgesteld.

- **Staging**—Verstrekt één enkele milieutak die aan specifieke infrastructuur-as-a-Dienst (IaaS) containers wordt opgesteld.

- **Productie**—Verstrekt één enkele milieutak die aan specifieke infrastructuur-as-a-Dienst (IaaS) containers wordt opgesteld.

- **Algemeen Master**—Verstrekt een master tak die aan Platform-as-a-Dienst (PaaS) containers wordt opgesteld.

![Diagram van de relatie tussen Adobe Commerce-cloudomgevingen](../../../assets/playbooks/environment-diagram.svg)

## Git-vertakkingen

Het milieu van de Integratie verstrekt één enkele tak van de basisintegratie die uw code van Adobe Commerce bevat die aan Platform-as-a-Dienst (PaS) containers wordt opgesteld.

De Adobe Commerce op cloudinfratumingevingen ondersteunt een flexibel, continu integratieproces. Begin door de integratietak aan uw lokale projectomslag te klonen. Maak een nieuwe vertakking of meerdere vertakkingen om nieuwe functies te ontwikkelen, wijzigingen te configureren en extensies toe te voegen. Met een ontwikkelde codetak en de overeenkomstige configuratiedossiers, zijn uw codeveranderingen klaar om aan de integratietak voor uitvoeriger het testen samen te voegen.

![Diagram van de op git gebaseerde vertakkingsstrategie voor Adobe Commerce-cloudomgevingen](../../../assets/playbooks/branching-diagram.svg)

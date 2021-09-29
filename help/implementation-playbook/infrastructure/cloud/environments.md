---
title: Cloud-infrastructuuromgevingen
description: Gebruik de juiste omgevingen voor de juiste gebruiksscenario's.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Omgevingen

Adobe Commerce op cloudinfrastructuur Pro ondersteunt omgevingen die u kunt gebruiken om uw winkel te ontwikkelen, te testen en te starten. Elke omgeving bevat een database en een webserver. De vier omgevingen die door Adobe Commerce worden gebruikt zijn:

- **Integratie** - Verstrekt één enkele milieutak en u kunt tot vier extra milieutakken tot stand brengen. Dit staat voor een maximum van vijf actieve takken toe die aan Platform-as-a-Dienst (PaaS) containers worden opgesteld.

- **Het opvoeren**-verstrekt één enkele milieutak die aan specifieke infrastructuur-as-a-Dienst (IaaS) containers wordt opgesteld.

- **Productie**-verstrekt één enkele milieutak die aan specifieke infrastructuur-as-a-Dienst (IaaS) containers wordt opgesteld.

- **Globaal Master**-verstrekt een master tak die aan Platform-as-a-Dienst (PAAS) containers wordt opgesteld.

![Diagram dat het verband tussen de wolkenmilieu&#39;s van de Handel van de Adobe toont](../../../assets/playbooks/environment-diagram.svg)

## Git-vertakkingen

Het milieu van de Integratie verstrekt één enkele tak van de basisintegratie die uw code van de Handel van Adobe bevat die aan Platform-as-a-Dienst (PaaS) containers wordt opgesteld.

De Adobe Commerce op cloudinframingevingen ondersteunt een flexibel, continu integratieproces. Begin door de integratietak aan uw lokale projectomslag te klonen. Maak een nieuwe vertakking of meerdere vertakkingen om nieuwe functies te ontwikkelen, wijzigingen te configureren en extensies toe te voegen. Met een ontwikkelde codetak en de overeenkomstige configuratiedossiers, zijn uw codeveranderingen klaar om aan de integratietak voor uitvoeriger het testen samen te voegen.

![Diagram van de op git gebaseerde vertakkingsstrategie voor Adobe Commerce-cloudomgevingen](../../../assets/playbooks/branching-diagram.svg)

---
title: Methodologie voor projectuitvoering
description: Ga vertrouwd met de werking van Adobe Commerce-software.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
feature: Build, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Methode voor projectuitvoering

Nu u een beter idee hebt van de instrumenten die hierbij betrokken zijn, zullen we nu onze leverings- en testprocessen afbreken.

## Continuous Integration (CI)

Bij voortdurend integreren worden automatisch de volgende handelingen uitgevoerd:

- Bouw de broncode om compilatiefouten te controleren.
- Voer tests uit wanneer een trekkingsverzoek wordt gecreeerd/bijgewerkt. Op dit moment worden PHP eenheidstests uitgevoerd.

De baan plaatst zijn uitvoeringsstatus aan het trekkingsverzoek. Ontwikkelaars kunnen de details van de uitvoering van de taak weergeven, zodat ze bestaande code kunnen herstellen of verbeteren.

## Continuous Delivery (CD)

Met Continuous Delivery (CD) wordt direct broncode naar de server geïmplementeerd nadat alle tests succesvol zijn uitgevoerd. De ontwikkelaars kunnen hun functies snel controleren en dan de taak toewijzen aan het team QA voor overzicht.

Aangezien de bouwstijl op het bouwstijlsysteem uitvoert, minimaliseert het niet alleen de plaatsingsonderbreking, maar vermindert ook de lading op de server. Dientengevolge, worden de activiteiten QA, die op de server gebeuren, minder beïnvloed.

![Doorlopende leveringsinfografisch](../../assets/playbooks/cicd.svg)

Het CI/CD-proces in het vorige diagram kan als volgt kort worden beschreven:

- Bitmap host de Git-opslagplaats.
- Docker-afbeeldingen worden gerepliceerd op basis van productietechnologiestapelconfiguraties.
- Docker-containers worden gebruikt voor alle ontwikkelings- en testomgevingen. Andere omgevingen kunnen deze configuraties indien nodig benutten.
- De ontwikkelaars voeren een controle van de relevante codetak voor elke nieuwe taak/kaartje uit.
- Voor alle commit takken, automatisch:
   - Een standaardscan uitvoeren.
   - Een codecompilatietest uitvoeren.
   - Een statische codescanfunctie uitvoeren (bijvoorbeeld SonarQube).
- Alle doorgevoerde scanbewerkingen worden samengevoegd met de doelvertakking.
- Een nieuwe vrijgegeven markering wordt geduwd aan AWS S3 voor het toepassingspakket.
- De nieuwe plaatsing wordt teweeggebracht door het team van de plaatsingstechniek.
   - Een plaatsingsbaan stelt het nieuwe pakket aan het doelmilieu op.
   - De de structuurupdates van het gegevensbestand vereisen een pauze om nieuwe verzoeken van de klant over te nemen.
- Het implementatieproces eindigt met een e-mail-/Slack-/Teams-melding die automatisch door de server wordt verzonden naar het ontwikkelingsteam voor implementatie.

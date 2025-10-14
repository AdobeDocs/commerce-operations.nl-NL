---
title: Beta-releases
description: Leer meer over de bètareleases van Adobe Commerce en hoe u hieraan kunt deelnemen.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: a15422e4e135eba01931172960dfb0a6b359cde8
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Adobe Commerce bèta-releases

bètaprogramma&#39;s van Adobe Commerce zijn een manier voor handelaren om toegang te krijgen tot pre-releasefuncties en -code, feedback te geven en de toekomst van Adobe Commerce te begeleiden. Er zijn twee typen bètaprogramma&#39;s:

- Openbare Beta: alle klanten en partners van Adobe Commerce hebben een openbaar bètaprogramma
- Private Beta: een particulier bètaprogramma vereist mogelijk goedkeuring op basis van kwalificatiecriteria voor deelname

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Voordelen van deelname

Het krijgen van vroege toegang tot eigenschappen die Adobe ontwikkelt verstrekt klanten en partners de capaciteit om terugkoppelen te verstrekken, productontwikkeling te vormen, en zich voor te bereiden om nieuwe mogelijkheden vóór algemene beschikbaarheid aan te nemen.

## Huidige Beta-programma&#39;s

Zie de volgende secties voor een lijst van actieve bètaprogramma&#39;s.

### Cloud Automation Patching Service (Private Beta)

De [&#x200B; Dienst van het Patching van de Automatisering van de Wolk &#x200B;](../tools/caps-tool/intro.md) automatiseert het proces om geïsoleerde veiligheidspatches op uw [&#x200B; Adobe Commerce op de milieu&#39;s van de Infrastructuur van de Wolk toe te passen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/overview).

In oktober 2025, zal de bètaversie van de het Patcheren van de Automatisering van de Wolk de Dienst aan het [&#x200B; het hulpmiddeldashboard van de Analyse van plaats-brede &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard) worden toegevoegd. Deze service biedt ondersteuning voor Commerce-projectbeheerders met een gestroomlijnde patchworkflow die het volgende omvat:

- Geautomatiseerde patchinstallatie
- Terugwinning terugdraaien
- Verificatie na de implementatie.

De service zorgt ervoor dat u veilige, stabiele en bijgewerkte omgevingen kunt onderhouden met minimale handmatige inspanningen en risico&#39;s.

De bètaversie bevat de volgende functies:

- **automatiseer flardinstallatie**: Vereenvoudig en automatiseer het proces om kritieke kwetsbaarheid over milieu&#39;s te patchen.
- **minimaliseer risico**: Vermijd plaatsstroomonderbrekingen met post-plaatsingsgezondheidscontrole en terugdraaimogelijkheden.

>[!NOTE]
>
>Aangezien de Dienst van het Patching van de Automatisering van de Wolk automatisch geïsoleerde veiligheidspatches toepast, moet u de [&#x200B; Medewerker of rol van Admin van het Project hebben &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/project/user-access) om het te gebruiken.

Om aan deze bèta deel te nemen, voltooi en voorleg de [&#x200B; Dienst van het Patching van de Automatisering van de Wolk - de Vorm van de Registratie van Beta &#x200B;](https://forms.office.com/r/3Wfxj5nPdB).

### IBM Sterling Order Management System Integration (Private Beta)

Met deze integratieversneller voor IBM Sterling Order Management kunnen Adobe Commerce-klanten aan de slag gaan met geavanceerde mogelijkheden voor orderbeheer, aangedreven door IBM Sterling OMS. Met deze integratie krijgen handelaren:

- Real-time zichtbaarheid in inventarisniveaus en nauwkeurige leveringsdatums voor uw klanten.
- Geautomatiseerde sourcing voor bestellingen op basis van configureerbare regels, zodat u uw uitvoeringsnetwerk en inventaris kunt optimaliseren.
- Een universele weergave van bestellingen tussen kanalen vanaf één dashboard, zodat uw supportteams de uitzonderlijke service kunnen leveren en uitzonderingen snel kunnen identificeren en afhandelen.
- Een getemplitste stroom van het terugkeerbeheer om terugkeerbeheer te vereenvoudigen.

Om aan deze bèta deel te nemen, verzend een e-mailverzoek naar [&#x200B; sbieber@adobe.com &#x200B;](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Public Alpha/Beta)

Elke Adobe Commerce Foundation alfa- en bètaversie bevat alle wijzigingen die tegen de geplande releasedatum aan de Adobe Commerce core-code worden geleverd, inclusief maar niet beperkt tot de volgende functionele gebieden:

- Laatste beveiligingsoplossingen
- Prestatieverbeteringen
- GraphQL-verbeteringen
- Oplossingen voor algemene problemen met kwaliteit
- Communautaire bijdragen
- Veranderingen die worden vereist om verenigbaarheid met [&#x200B; de diensten van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/user-guides/home) te steunen

#### Naamgevingsconventie en -schema

Adobe geeft doorgaans meerdere keren per jaar alfa- en bètapatches uit.

Alpha-releasepakketten hebben het achtervoegsel `-alphaX` . Voor de alfareleasepakketten van Adobe Commerce 2.4.7 wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta-releasepakketten hebben het achtervoegsel `-betaX` . Voor de release van Adobe Commerce 2.4.7 beta wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-beta1`
- `2.4.7-beta2`

Zie het [&#x200B; versieschema &#x200B;](schedule.md) voor de lijst van aanstaande openbare alpha en bètaversiedata.

#### Geen toegang

Adobe Commerce alfa- en bètareleases worden op dezelfde manier gedistribueerd als elke andere Adobe Commerce-patchrelease: als Composer-metapakketten op `https://repo.magento.com` . De broncode is beschikbaar op [&#x200B; GitHub &#x200B;](https://github.com/magento/magento2).

Zie [&#x200B; Snel begin van de Installatie Composer &#x200B;](../installation/composer.md) voor meer details.

#### Melding van problemen

Adobe biedt de standaard Adobe Support Service niet voor alfa- en bètareleases.

Om terugkoppelen met betrekking tot alpha- en bètaversies voor te leggen, volg de [&#x200B; regelmatige kwestie die stroom &#x200B;](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) op [&#x200B; GitHub &#x200B;](https://github.com/magento/magento2) meldt.

Adobe houdt toezicht op alle kritieke problemen die zijn gemeld in vergelijking met de nieuwste alfa- of bètaversie en geeft prioriteit aan deze problemen om te worden opgelost vóór de GA-releasedatum.

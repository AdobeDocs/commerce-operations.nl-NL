---
title: Gedeelde verantwoordelijkheid
description: Leer meer over de beveiligingsverantwoordelijkheden van elke partij die betrokken is bij uw Adobe Commerce-project voor cloudinfrastructuur.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Beveiligingsmodel voor gedeelde verantwoordelijkheid

Adobe Commerce on cloud Infrastructure is een platform-as-a-service (PaaS) die is gebaseerd op een beveiligingsmodel met gedeelde verantwoordelijkheid. Adobe, de handelaar, de clouddienstverlener, en de leverancier van het inhoudsleveringsnetwerk (CDN) elk hebben afzonderlijke verantwoordelijkheid voor het handhaven van de veiligheid van Adobe Commerce op de toepassing van de wolkeninfrastructuur en de handel-specifieke code en uitbreidingen.

Deze benadering laat verkopers toe om een hoogst flexibele, klantgerichte, en scalable oplossing te ontwerpen en uit te voeren die het best aan hun bedrijfsvereisten aanpast terwijl het minimaliseren van operationele verantwoordelijkheden en kosten.

In het algemeen is Adobe verantwoordelijk voor het ontwikkelen en onderhouden van veilige kerntoepassingscode, het handhaven van de veiligheid van het platform, het verzekeren van de naleving SOC 2 en PCI van het platform en zijn verenigbaarheid met PCI-volgzame technologiecomponenten (bijvoorbeeld, PHP, Redis), en het antwoorden op veiligheidskwesties betreffende het kernplatform. Adobe is ook verantwoordelijk voor het werken met cloudserviceproviders en CDN-partners om problemen op te lossen die zich kunnen voordoen.

De handelaren zijn verantwoordelijk voor het handhaven van veilige douanecode en integratie met derdetoepassingen, het verzekeren van veilige toepassingsontwikkeling, het verkrijgen van certificatie PCI indien gevraagd door de betalingsverwerker van de handelaar, en het reageren en het antwoorden op veiligheidsincidenten.

## Verantwoordelijkheden van de Adobe

Adobe is verantwoordelijk voor de beveiliging en beschikbaarheid van de Adobe Commerce op het gebied van cloudinfrastructuur en de kerncode van Adobe Commerce op de oplossing van cloudinfrastructuur. Daarnaast is de Adobe verantwoordelijk voor de noodzakelijke activiteiten en mechanismen die de beveiliging van de Adobe Commerce inzake cloudinfrastructuuroplossing waarborgen, waaronder:

- Beveiliging en patches op serverniveau toepassen op toepassingen die door Adobe Commerce worden ondersteund op cloudinfrastructuur, zoals opslag van cloudgegevens en zoekmogelijkheden
- Het uitvoeren van penetratietests en het scannen van de kern-Adobe Commerce op code voor cloudinfrastructuur
- Halfjaarlijkse beoordelingen/audits uitvoeren van de oplossing en het beheer van machtigingen van openbare cloudserviceproviders voor identiteits- en toegangsbeheer (IAM) (PCI-compatibiliteitseis)
- Halfjaarlijkse beoordelingen/audits uitvoeren van erkende gebruikers, waaronder Adobe werknemers en contractanten (PGB-nalevingsvereiste)
- Jaarlijkse tests en documentatie van back-up- en herstelfuncties uitvoeren
- Vormen server en perimeterfirewalls
- De Adobe Commerce aansluiten en configureren op de opslagplaats voor cloudinfrastructuur
- Noodherstelplannen (Disaster Recovery, DR) definiëren, testen, implementeren en documenteren voor de gebieden die onder de bevoegdheid van de Adobe vallen
- WAF-regels (global platform web application firewall) definiëren
- Besturingssysteem (OS) versterken
- Implementeren en onderhouden van de integratie van CDN-oplossingen (Content Distribution Network) en APM-oplossingen (Application Performance Management) met Adobe Commerce op cloudinfrastructuur
- Periodieke beveiliging en andere updates voor de kerncode van Adobe Commerce over cloudinfrastructuur (het toepassen van patches valt onder de verantwoordelijkheid van de handelaar)
- Het beheren van bedrijfs steun en steun toegangscontroles (bijvoorbeeld, Zendesk)
- Beveiligingsincidenten met betrekking tot de Adobe Commerce op de infrastructuur van het wolkeninfrastructuurplatform bewaken, registreren en verhelpen
- Bewaking van platformactiviteiten en 24x7 ondersteuning voor Adobe Commerce op producten van cloudinfrastructuur
- De productie- en staging-omgevingen voorzien
- Het beoordelen van potentiële veiligheidsbedreigingen voor platformverrichtingen en infrastructuur
- Het schrapen van gegevensverwerking, opslag, net, en andere middelen, zoals die in de dienst-vlakke overeenkomst (SLA) met de handelaar worden beschreven
- DNS instellen (alleen Adobe Commerce voor infrastructuur van cloudinfrastructuur)
- Het platform testen op beveiligingsproblemen

Hoewel Adobe PCI-certificering onderhoudt voor de infrastructuur en services die worden gebruikt bij de exploitatie van de Adobe Commerce-oplossing voor cloudinfrastructuur, zijn handelaren verantwoordelijk voor de naleving van aangepaste code, systeem- en netwerkprocessen en de organisatie.

Adobe garandeert ook de beschikbaarheid van de infrastructuur van de handelaar, zoals overeengekomen in de toepasselijke SLA.

## Handelstaken

De handelaar is verantwoordelijk voor het volgen van best practices op het gebied van beveiliging voor hun specifieke, aangepaste instantie van Adobe Commerce op cloudinfrastructuuroplossing, en voor:

- De benodigde Adobe Commerce toevoegen aan configuratiebestanden van de cloud-infrastructuur aan de opslagplaats
- Beveiliging en andere patches direct na hun release door Adobe toepassen op hun aangepaste Adobe Commerce op cloudinfrastructuuroplossing
- Beveiliging en andere patches worden toegepast op alle aangepaste extensies en code, direct na de release ervan door de leverancier
- Aangepaste VCL-bestanden voor Varnish maken, implementeren en testen
- Het ontwerpen, ontwerpen, installeren, integreren en beveiligen van de aangepaste Adobe Commerce op cloudinfrastructuuroplossing, inclusief alle aangepaste extensies en code
- Gebruikerstoegang verlenen en intrekken tot het exemplaar van de Adobe Commerce van de handelaar op de configuratie, de toepassing, en het platform van de wolkeninfrastructuur
- Behandeling van beveiligingsproblemen met betrekking tot het interne netwerk, de servers, de infrastructuur en eventuele aangepaste toepassingen van de leverancier die op het Adobe Commerce-platform voor cloudinfrastructuur zijn gebouwd
- Adobe Commerce installeren op opdrachtregelprogramma voor integratie in de cloud-infrastructuur (CLI)
- Het vereiste niveau van naleving PCI van de aangepaste toepassing en andere interne processen handhaven, zoals die door de richtlijnen PCI-DSS worden bepaald

  >[!NOTE]
  >
  >De PCI-compatibiliteit van de handelaar bouwt voort op de PCI-certificeringen van Adobe Commerce op cloudinfrastructuur en de cloudhostingprovider om de gebieden die moeten worden gecontroleerd, tot een minimum te beperken.

- PCI ASV-scans uitvoeren en problemen verhelpen in de kern-Adobe Commerce met code en platform voor cloudinfrastructuur
- Alle toepassingsactiviteiten volgen die een potentiële veiligheidsbedreiging, met inbegrip van penetratie het testen, kwetsbaarheidsscans, en logboeken kunnen onthullen
- Bewaking van en reactie op beveiligingsincidenten, waaronder forensische incidenten, herstel en rapportage in verband met de Adobe Commerce van de handelaar over cloudinfrastructuuroplossing en gebruikersaccounts
- Een DNS-provider verkrijgen en handelsspecifieke DNS-records configureren en onderhouden
- Prestatietests uitvoeren op de aangepaste toepassing
- Toegang tot platformaccounts, toegang tot instanties en toepassingen beveiligen
- Testen en QA van de aangepaste toepassing
- Behoud van de beveiliging van systemen of netwerken die de handelaar op een cloudinfrastructuurtoepassing verbindt met de Adobe Commerce

## Verantwoordelijkheden van cloudserviceproviders

Adobe is afhankelijk van gevestigde cloudserviceproviders die de cloudserverinfrastructuur voor Adobe Commerce hosten op cloudinfrastructuur. Deze leveranciers zijn verantwoordelijk voor veiligheid van het netwerk, met inbegrip van het verpletteren, het schakelen, en de veiligheid van het perimeternetwerk via firewallsystemen en de systemen van de binnendringenopsporing (IDS). Cloud-serviceproviders zijn ook verantwoordelijk voor de fysieke beveiliging van datacenters die de Adobe Commerce hosten voor cloudinfrastructuuroplossingen en de milieubeveiliging van datacenters.

Ook cloudserviceproviders zijn verantwoordelijk voor:

- Behoud van PCI DSS-, SOC 2- en ISO 27001-certificeringen voor hun cloudservices
- De hypervisor beveiligen
- Het gegevenscentrum beveiligen, met inbegrip van zowel fysieke als netwerktoegang

## CDN-providerverantwoordelijkheden

De Adobe Commerce on cloud Infrastructure-oplossing gebruikt CDN-providers om de laadtijd van pagina&#39;s, cacheinhoud en direct verouderde inhoud te versnellen. Deze leveranciers zijn ook verantwoordelijk voor veiligheidskwesties direct verwant met of beïnvloedend hun CDN, en voor het bepalen van en het handhaven van CDN WAF regels.

## Beveiligingsverantwoordelijkheden

In het volgende diagram wordt het RACI-model (R — Responsible, A — Accountable, C — Consulted, I — Informed) gebruikt om elke partij in de beveiligingsverantwoordelijkheden van het ecosysteem met betrekking tot de Adobe Commerce op het model van gedeelde verantwoordelijkheid voor de cloudinfrastructuur visueel weer te geven:

<table>
<thead>
  <tr>
    <th>Taak</th>
    <th>Adobe</th>
    <th>Merchant</th>
    <th>Cloud-serviceprovider</th>
    <th>CDN-provider</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Adobe Commerce toepassen op patches voor cloudinfrastructuur</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Patches toepassen op ondersteunende services<br>(bijvoorbeeld Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>WAF-regels voor oorsprong definiëren</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF-regels definiëren</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>WAF-regels voor platforms implementeren</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF-regels implementeren</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Corefouten in Adobe Commerce corrigeren op code voor cloudinfrastructuur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce vrijgeven op patches voor cloudinfrastructuur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Schalen (berekenen en opslaan)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Schalen (PaaS/raster)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Toegang tot broncode garanderen, inclusief repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce installeren op de CLI-tool voor cloudinfrastructuur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce op configuratiebestanden van de cloud-infrastructuur toevoegen aan de opslagplaats</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Een project voor de handelaar maken (onboarding UI)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Opslagplaats(en) verbinden met Adobe Commerce op cloudinfrastructuur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bronopslagplaats configureren<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Een gebruiker voor de releasebeheerder maken (onboarding UI)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Code implementeren in productie</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Code implementeren in fasering</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Externe toepassingen en extensies integreren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Extensies installeren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce aanpassen op cloudinfrastructuur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testprestaties van aangepaste Adobe Commerce op cloudinfrastructuur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aangepaste toepassing testen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Thema en ontwerp van aangepaste toepassingen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Het creëren van, het opstellen van, en het testen van douane VCLs van Varnish</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS configureren (alleen platforminfrastructuur)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN-extensie ontwikkelen en bugs corrigeren</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Onboarding CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN wordt ondersteund<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APM/infrastructuur configureren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM/Infrastructure installeren</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ondersteuning voor New Relic APM/infrastructuur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Nginx configureren<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS-provider verkrijgen (alleen Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Het besturingssysteem versterken</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>De productie- en staging-omgevingen voorzien</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Toegang tot Zendesk voor Adobe Commerce via cloudinfrastructuur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Oplossen van zakelijke beveiligingsproblemen</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Adobe Commerce oplossen over beveiligingsproblemen met cloudinfrastructuur</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN-beveiligingsproblemen oplossen</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Beveiligingsproblemen met APM oplossen</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe met beveiligingsonderzoek (software) ondersteunen</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe met veiligheidsonderzoek ondersteunen (scans/audits)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PCI ASV-scans uitvoeren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce verhelpen op PCI-scans met cloudinfrastructuur<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PaaS PCI-scans herstellen</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Besturings- en platformgeheimen beheren</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce beheren op coderingssleutels voor cloudinfrastructuur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aangepaste Adobe Commerce scannen op cloud-infrastructuurinstanties</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beveiligingslogboeken controleren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>IAM beheren en machtigingen voor Adobe Commerce beheren voor cloudinfrastructuur</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheren van de controles van de steuntoegang (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Zakelijke ondersteuning en toegang beheren</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Jaarlijkse tests en documentatie van noodherstelplan en back-up en herstel van Adobe</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Jaarlijkse tests en documentatie van het noodherstelplan</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Alleen als de Adobe Commerce op de gegevensopslagplaats voor cloudinfrastructuur wordt gebruikt als de hoofdopslagplaats. Het gebruik van andere externe opslagplaatsen valt uitsluitend onder de verantwoordelijkheid van de handelaar.</p>
      <p><sup><strong>2</strong></sup> Adobe biedt ondersteuning op niveau 1 voor problemen met CDN-providers.</p>
      <p><sup><strong>3</strong></sup> Sommige controles Ngnix worden gevormd door de handelaar voor hun toepassingen en zijn hun verantwoordelijkheid.</p>
      <p><sup><strong>4</strong></sup> Voor PCI worden de vereisten voor penetratietests gedeeld tussen Adobe en de handelaar.</p>
    </td>
  </tr>
</tfoot>
</table>

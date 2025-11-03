---
title: Beveiliging en operationeel model van gedeelde verantwoordelijkheid
description: Leer meer over de beveiligingsverantwoordelijkheden van elke partij die betrokken is bij uw Adobe Commerce-project voor cloudinfrastructuur.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: aac78fc95b86951f352a636eef33e0b79b22a183
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 0%

---

# Beveiliging en operationeel model van gedeelde verantwoordelijkheid

Adobe Commerce op cloudinfrastructuur is een platform-as-a-service (PaS) die is gebaseerd op een beveiliging en operationeel model met gedeelde verantwoordelijkheid. Deze verantwoordelijkheden worden gedeeld door Adobe, de handelaar, de leverancier van de wolkendienst, en de leverancier van het inhoudsleveringsnetwerk (CDN). Elke partij draagt een duidelijke verantwoordelijkheid voor het beveiligen en exploiteren van de Adobe Commerce-toepassing en de specifieke code en uitbreidingen die op cloudinfrastructuur worden geïmplementeerd.

Dit gedeelde model laat verkopers toe om een hoogst flexibele, klantgerichte, en scalable oplossing te ontwerpen en uit te voeren om aan hun bedrijfsvereisten te voldoen terwijl het minimaliseren van operationele verantwoordelijkheden en kosten.

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

In het algemeen is Adobe verantwoordelijk voor het volgende:

- Veilige kerncode voor toepassingen ontwikkelen en onderhouden
- Behoud van de beveiliging van het platform
- Ervoor zorgen dat het platform voldoet aan SOC 2 en PCI en compatibel is met PCI-compatibele technologiecomponenten (bijvoorbeeld PHP, Redis)
- Reageren op beveiligingsproblemen met betrekking tot het kernplatform
- Werken met cloudserviceproviders en CDN-partners om problemen op te lossen

Merchants zijn verantwoordelijk voor:

- Beveiliging behouden voor aangepaste code en integratie met toepassingen van derden
- Zorgen voor veilige ontwikkeling van toepassingen
- Bezig met verkrijgen van PCI-certificering op verzoek van de betalingsprocessor van de handelaar
- Reageren op en reageren op beveiligingsincidenten

## Adobe-verantwoordelijkheden

Adobe is verantwoordelijk voor de beveiliging en beschikbaarheid van de Adobe Commerce op het gebied van cloudinfrastructuren en de kerncode voor oplossingen. Daarnaast is Adobe verantwoordelijk voor de noodzakelijke activiteiten en mechanismen die de veiligheid van de Adobe Commerce op het gebied van cloudinfrastructuuroplossing waarborgen, waaronder:

- Beveiliging en patches op serverniveau toepassen op toepassingen die door Adobe Commerce worden ondersteund op cloudinfrastructuur, zoals opslag van cloudgegevens en zoekmogelijkheden
- Het uitvoeren van penetratietests en het scannen van de kern-Adobe Commerce op code voor cloudinfrastructuur
- Halfjaarlijkse beoordelingen en audits uitvoeren van de identiteits- en toegangsbeheeroplossingen en het beheer van machtigingen van openbare cloudservicebureaus (IAM) (PCI-compatibiliteitseis)
- Halfjaarlijkse beoordelingen en audits uitvoeren van erkende gebruikers, waaronder Adobe-werknemers en contractanten (PGB-nalevingsvereiste)
- Jaarlijkse tests en documentatie van back-up- en herstelfuncties uitvoeren
- Vormen server en perimeterfirewalls
- De Adobe Commerce aansluiten en configureren op de opslagplaats voor cloudinfrastructuur
- Plannen voor noodherstel (Disaster Recovery, DR) definiëren, testen, implementeren en documenteren voor de gebieden die onder de verantwoordelijkheid van Adobe vallen
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

Adobe onderhoudt PCI-certificering voor de infrastructuur en services die worden gebruikt voor de Adobe Commerce-oplossing.  De handelaren zijn verantwoordelijk voor de naleving van douanecode, systeem en netwerkprocessen, en de organisatie.

Adobe zorgt ook voor de beschikbaarheid van de infrastructuur van de handelaar, zoals overeengekomen in het toepasselijke SLA.

## Handelstaken

De handelaar is verantwoordelijk voor het volgen van best practices op het gebied van beveiliging voor hun specifieke, aangepaste instantie van Adobe Commerce op cloudinfrastructuuroplossing:

- De benodigde Adobe Commerce toevoegen aan configuratiebestanden van de cloud-infrastructuur aan de opslagplaats
- Beveiliging en andere patches direct na hun release door Adobe toepassen op hun aangepaste Adobe Commerce on cloud Infrastructure-oplossing
- Beveiliging en andere patches worden toegepast op alle aangepaste extensies en code, direct na de release ervan door de leverancier
- Aangepaste VCL-bestanden voor Varnish maken, implementeren en testen
- Het ontwerpen, ontwerpen, installeren, integreren en beveiligen van de aangepaste Adobe Commerce op cloudinfrastructuuroplossing, inclusief alle aangepaste extensies en code
- Gebruikerstoegang verlenen en intrekken tot het exemplaar van de Adobe Commerce van de handelaar op de configuratie, de toepassing, en het platform van de wolkeninfrastructuur
- Behandeling van beveiligingsproblemen met betrekking tot het interne netwerk, de servers, de infrastructuur en eventuele aangepaste toepassingen van de leverancier die op het Adobe Commerce-platform voor cloudinfrastructuur zijn gebouwd
- Adobe Commerce installeren op opdrachtregelprogramma voor integratie in de cloud-infrastructuur (CLI)
- Het vereiste niveau van naleving PCI van de aangepaste toepassing en andere interne processen handhaven, zoals die door de richtlijnen PCI-DSS worden bepaald

  >[!NOTE]
  >
  >Om de gebieden te minimaliseren die moeten worden herzien, wordt de naleving PCI voor de handelaar voortgebouwd op de certificatie PCI van Adobe Commerce en de wolkenhostingleverancier.

- PCI ASV-scans uitvoeren en problemen verhelpen in de kern-Adobe Commerce met code en platform voor cloudinfrastructuur
- Alle toepassingsactiviteiten volgen die een potentiële veiligheidsbedreiging, met inbegrip van penetratie het testen, kwetsbaarheidsscans, en logboeken kunnen onthullen
- Bewaking van en reactie op beveiligingsincidenten, waaronder forensische incidenten, herstel en rapportage in verband met de Adobe Commerce van de handelaar over cloudinfrastructuuroplossing en gebruikersaccounts
- Een DNS-provider verkrijgen en handelsspecifieke DNS-records configureren en onderhouden
- Prestatietests uitvoeren op de aangepaste toepassing
- Toegang tot platformaccounts, toegang tot instanties en toepassingen beveiligen
- Testen en QA van de aangepaste toepassing
- Behoud van de beveiliging van systemen of netwerken die de handelaar op een cloudinfrastructuurtoepassing verbindt met de Adobe Commerce

## Cloud Service Provider-verantwoordelijkheden

Adobe vertrouwt op gevestigde cloudserviceproviders om de cloudserverinfrastructuur voor Adobe Commerce te hosten op cloudinfrastructuur. Deze leveranciers zijn verantwoordelijk voor veiligheid van het netwerk, met inbegrip van het verpletteren, het schakelen, en de veiligheid van het perimeternetwerk via firewallsystemen en de systemen van de binnendringenopsporing (IDS). Cloud-serviceproviders zijn ook verantwoordelijk voor de fysieke beveiliging van datacenters die de Adobe Commerce hosten voor cloudinfrastructuuroplossingen en de milieubeveiliging van datacenters.

Ook cloudserviceproviders zijn verantwoordelijk voor:

- Behoud van PCI DSS-, SOC 2- en ISO 27001-certificeringen voor hun cloudservices
- De hypervisor beveiligen
- Het gegevenscentrum beveiligen, met inbegrip van zowel fysieke als netwerktoegang

## CDN-providerverantwoordelijkheden

De Adobe Commerce on cloud Infrastructure-oplossing gebruikt CDN-providers om de laadtijd van pagina&#39;s, cacheinhoud en direct verouderde inhoud te versnellen. Deze leveranciers zijn ook verantwoordelijk voor veiligheidskwesties direct verwant met of het beïnvloeden van hun CDN, en voor het bepalen van en het handhaven van CDN WAF regels.

## Overzicht van beveiligingsverantwoordelijkheden

>[!BEGINSHADEBOX]

In de volgende overzichtstabel wordt het RACI-model gebruikt om de beveiligingsverantwoordelijkheden weer te geven die worden gedeeld tussen Adobe, de handelaar en de Cloud-serviceprovider:

**R** — Verantwoordelijk
**A** — Verantwoordelijk
**C** — Geconsulteerd
**I** — Informed

>[!ENDSHADEBOX]

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
    <td>Het toepassen van flarden op het steunen van de diensten <br> (Bijvoorbeeld, Nginx of MySQL.)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>WAF-oorsprongsregels definiëren</td>
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
    <td>Schalen (PaaS en raster)</td>
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
    <td>Depositorecentra verbinden met Adobe Commerce op cloudinfrastructuur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Het vormen van de bronbewaarplaats <sup> 1 </sup></td>
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
    <td>De aangepaste toepassing testen</td>
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
    <td>Het steunen CDN <sup> 2 </sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APM- en infrastructuurtoepassingen configureren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM- en infrastructuurtoepassingen installeren</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ondersteuning voor New Relic APM- en infrastructuurtoepassingen</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Het vormen Nginx <sup> 3 </sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Een DNS-provider verkrijgen (alleen Pro)</td>
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
    <td>Adobe helpen met beveiligingsonderzoek (software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe helpen met veiligheidsonderzoek (scans/audits)</td>
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
    <td>Het verhelpen van Adobe Commerce op de scans van wolkeninfrastructuur PCI <sup> 4 </sup></td>
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
      <p><sup><strong> 1 </strong></sup> slechts als Adobe Commerce op de bewaarplaats van de wolkeninfrastructuur als belangrijkste bewaarplaats wordt gebruikt. Het gebruik van andere externe opslagplaatsen valt uitsluitend onder de verantwoordelijkheid van de handelaar.</p>
      <p><sup><strong> 2 </strong></sup> Adobe verleent Niveau 1 steun voor kwesties met CDN leveranciers.</p>
      <p><sup><strong> 3 </strong></sup> De handelaar is verantwoordelijk voor om het even welke controles Ngnix die zij voor hun toepassingen vormen.</p>
      <p><sup><strong> 4 </strong></sup> voor PCI, worden de penetratietestvereisten gedeeld tussen Adobe en de handelaar.</p>
    </td>
  </tr>
</tfoot>
</table>

## Overzicht van de operationele verantwoordelijkheden

>[!BEGINSHADEBOX]

In de volgende overzichtstabellen worden de operationele verantwoordelijkheden voor Adobe en Merchants verduidelijkt bij het ontwikkelen, implementeren, onderhouden en beveiligen van Adobe Commerce op cloudinfrastructuur.

>[!ENDSHADEBOX]

### Codering en ontwikkeling

#### Core Adobe Commerce-code

|     | Adobe | Merchant |
| --- | --- | --- |
| Updates en patches publiceren naar Adobe Commerce Core | R |     |
| Beschikbaarheid en patches van het bestandssysteem | R |  |
| Updates en patches publiceren naar ECE-gereedschappen | R |     |
| Kwaliteit Adobe Commerce-toepassing | R |     |

{style="table-layout:auto"}

#### Codeopslagplaats

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van repo.magento.com | R |     |
| Beschikbaarheid van Adobe Commerce op Cloud Git-server | R |     |
| Andere door de handel geselecteerde opslagruimten voor code (GitHub, Bitbucket, gehoste Git-server) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Merchant |
| --- | --- | --- |
| Cloud Docker-containers beschikbaar maken voor downloaden | R |   |
| Implementatie en installatie van Cloud Docker (optioneel) |     | R |
| Andere lokale ontwikkelinstellingen |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Merchant |
| --- | --- | --- |
| Doorlopende kwaliteit en bijwerking van ECE-instrumenten | R |   |
| De nieuwste versie van ECE Tools installeren |     | R |

{style="table-layout:auto"}

#### Aanpassingen

|  | Adobe | Merchant |
| --- | --- | --- |
| Aangepaste Adobe Commerce-modules en code |     | R |
| Extensies |     | R |
| Aangepaste integratie |     | R |

{style="table-layout:auto"}

#### Inzet

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van infrastructuur voor het samenstellen en implementeren van code | R |   |
| Doorlopende kwaliteit van de infrastructuur bouwt-en-stelt configuratiepijpleiding op | R |   |
| Configuratie van build en implementatie van statische inhoud |     | R |
| Ontwikkeling en uitvoering van het beheerproces voor implementatie: criteria en wijzigingsbeheer |     | R |
| Distribueren naar een testomgeving |     | R |
| Distribueren naar productieomgeving |     | R |
| Terugdraaiversies van productie |     | R |

{style="table-layout:auto"}

#### Omgevingen synchroniseren

Merchants zijn verantwoordelijk voor het synchroniseren van gegevens tussen omgevingen.

#### Reparatie

|     | Adobe | Merchant |
| --- | --- | --- |
| Updates en patches installeren op ECE-gereedschappen |     | R |
| Updates en patches installeren op Adobe Commerce Core |     | R |

#### Beschikbaarheid website

|  | Adobe | Merchant |
| --- | --- | --- |
| Aangepaste Adobe Commerce-toepassing en bijbehorende websites |     | R |

#### Prestaties

|     | Adobe | Merchant |
| --- | --- | --- |
| Kerntoepassingen afstemmen en optimaliseren | R |   |
| Aangepaste afstemming en optimalisatie van code |     | R |
| Aangepaste Adobe Commerce-code |     | R |
| Testen laden |     | R |
| Prestatietests |     | R |

{style="table-layout:auto"}


#### Logboeken en controle

|     | Adobe | Merchant |
| --- | --- | --- |
| Logbestanden roteren | R |   |
| Aangepaste Adobe Commerce-toepassing | | R |
| Beschikbaarheid van de diensten van New Relic:<br> APM toepassing en agentenintegratie, de toepassing van de Infrastructuur, <br> Logging &amp; integratie | R |   |
| New Relic-waarschuwingen instellen |     | R |
| New Relic-agent implementeren op PaaS-servers | R |  |

{style="table-layout:auto"}

#### Foutopsporing en probleemoplossing

|     | Adobe | Merchant |
| --- | --- | --- |
| Foutopsporing en probleemoplossing | R | R |
| Tijdige ondersteuning voor foutopsporing en probleemoplossingsproces |     | R |

{style="table-layout:auto"}

### Toepassings- en serviceconfiguratie

#### Commerce-toepassing

|     | Adobe | Merchant |
| --- | --- | --- |
| Toepassingsconfiguratie |     | R |
| Domeinen toevoegen aan de Adobe Commerce-toepassing (basis-URL&#39;s) |     | R |
| Het vormen PaaS om de versies van de Diensten te gebruiken die door de opgestelde versie van Adobe Commerce <br><br> worden gesteund, bijvoorbeeld, zijn de verschillende versies van Commerce compatibel met specifieke versies van PHP, Redis, etc. |     | R |

{style="table-layout:auto"}

#### Taak plannen met snijtaken

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van standaard snijtaken | R | |
| Doorlopende kwaliteit van aangepaste uitsnijdtaken |  | R |

{style="table-layout:auto"}

#### Berichtenmakelaar voor framework voor berichtwachtrij

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de dienst RabbitMQ | R |   |
| Configuratie van standaard RabbitMQ-instellingen | R |   |
| Doorlopende kwaliteit en patching van KonijnMQ | R |   |
| Een serviceverzoek indienen om een RabbitMQ-versie te installeren die compatibel is met de geïnstalleerde Adobe Commerce-versie |   | R |

{style="table-layout:auto"}

#### PHP-service

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van PHP | R |   |
| Configuratie van standaard PHP-instellingen | R |     |
| Configuratie van aangepaste PHP-instellingen |     | R |
| Configuratie van YAML-bestand om PHP-versies uit te lijnen die compatibel zijn met de geïnstalleerde Adobe Commerce-versie |    | R |

{style="table-layout:auto"}

#### Databaseservices

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van Galera- en MariaDB-services | R | |
| Het lopende onderhoud van standaardgegevensbestandmontages <br><br> (indexerend en optimaliserend kernlijsten, optimaliserend standaard sys-admin montages) | R |   |
| Het voortdurende onderhoud van koopkrachtige gegevens en gewijzigde montages <br><br> (het vormen genormaliseerde versus vlakke lijsten, het indexeren en optimaliseren van douane en derdetabellen, het archiveren of het verwijderen van gegevens, het vormen systeembeleidsmontages) |     | R |
| Configuratie van Galera en MySQL | R |   |
| Doorlopende kwaliteit en patching van Galera en MariaDB | R |   |
| Doorlopende infrastructuuroptimalisatie | R |   |
| Langzame query&#39;s identificeren en corrigeren |     | R |
| Een serviceverzoek indienen om een MariaDB-versie te installeren die compatibel is met de geïnstalleerde Adobe Commerce-versie |     | R |
| Handelsspecifieke gedragslijnen voor gegevensbewaring instellen en onderhouden (het beleid voor gegevensbewaring van Adobe wordt gedefinieerd in de koopovereenkomst) |     | R |

{style="table-layout:auto"}

#### CDN-service

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid en Kwaliteit van CDN | R |   |
| Snelle serviceconfiguratie (via Extension / API) |     | R |
| Snelle extensiekwaliteit | R |   |
| VCL-fragmenten voor snelle integratie (gebundeld met de snelste extensie), kwaliteit | R |   |
| Optimalisatie van paginacache |     | R |
| Domeinen toevoegen aan services, CDN en infrastructuur | R |   |
| Aangepaste VCL-fragmenten |     | R |
| WAF- en WAF-regels | R |   |

{style="table-layout:auto"}

#### Cacheservice

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de Redis-service | R |   |
| Configuratie van standaardinstellingen voor Redis | R |   |
| Doorlopende kwaliteit en patches van Redis | R |   |
| Een serviceverzoek indienen om een Redis-versie te installeren die compatibel is met de geïnstalleerde Adobe Commerce-versie |     | R |

{style="table-layout:auto"}

#### Zoekservice

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van Elasticsearch of OpenSearch | R |   |
| Configuratie van standaard Elasticsearch- of OpenSearch-instellingen | R |   |
| Een serviceverzoek indienen om een Elasticsearch- of OpenSearch-versie te installeren die compatibel is met de geïnstalleerde Adobe Commerce-versie |  | R |

{style="table-layout:auto"}

#### E-mailservice

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de e-mailservice van SendGrid en de integratie ervan | R |   |
| Het gebruik van SendGrid van de handelaar van de monitor tegen grenzen | R |   |
| De handelaar is verantwoordelijk voor het gebruiken van de dienst slechts voor uitgaande transactie e-mails <br> De dienst steunt niet het verzenden van marketing e-mails. |     | R |
| Optionele e-mailservices van derden configureren |     | R |

{style="table-layout:auto"}

#### Diensten van derden

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid en kwaliteit van services van derden |     | R |

{style="table-layout:auto"}

### Commerce Services-extensies

#### Advance Reporting Service

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de Advanced Reporting Service | R |   |
| De configuratie van Geavanceerde Rapportering voldoet aan de Geavanceerde Voorwaarden van de Rapportering |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van Adobe Commerce Business Intelligence-services | R |   |
| MBI-synchronisatieprocessen | R |   |
| MBI-synchronisatieproblemen detecteren | R |   |
| Het vormen MBI de Synchronisatie van Gegevens aan de Wolk van de Handel van Adobe Pro, Starter, op Beelden, of niet-Adobe Commerce <br> (API, de kwaliteit en het formatteren van Gegevens, handelaarnetwerk, <br> verbindingen van DB zowel binnen als buiten de Wolk van de Koophandel van Adobe, over gegevensdrempels) |     | R |
| Synchronisatie van MBI-gegevens met Adobe Commerce Cloud Pro configureren <br> (databaseconfiguratie Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

>
>Handelaars moeten de meest recente versie van Live zoeken, productaanbevelingen en betalingsservices gebruiken om de hoogste stabiliteit, functionaliteit en geschiktheid voor ondersteuning te garanderen.
>Adobe biedt geen ondersteuning voor verouderde versies en upgrades om ervoor te zorgen dat u profiteert van de nieuwste verbeteringen en foutoplossingen.
>Voor details op gesteunde versies, zie de [ Matrijs van de Beschikbaarheid van het Product voor de Diensten van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability#commerce-services).

#### Aanbevelingen voor producten

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de dienst van de Aanbevelingen van het Product | R |   |
| Modules voor productaanbevelingen upgraden |   | R |

{style="table-layout:auto"}

#### Live zoeken

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van de service Live zoeken | R |   |
| Modules voor Live zoeken bijwerken |   | R |

{style="table-layout:auto"}

#### Kwaliteit van storefront-gebeurtenissen (gegevensverzameling) voor het aansturen van productaanbevelingen en Live Search-uitvoer

|     | Adobe | Merchant |
| --- | --- | --- |
| Basisthema (Luma) | R |   |
| Aangepast thema |  | R |
| Core PWA-implementatie | R |   |
| Aangepaste PWA-implementatie |  | R |
| Core AEM EDS-implementatie (Commerce Boilerplate) | R |   |
| Aangepaste AEM EDS-implementatie |  | R |
| Elke andere aangepaste implementatie van de winkel |  | R |

{style="table-layout:auto"}

#### Betalingsdiensten

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van betalingsdienst | R |   |
| Modules voor betalingen upgraden |   | R |

{style="table-layout:auto"}

### Netwerkdiensten

#### Afbeelding optimaliseren

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid en kwaliteit van optimalisatie van afbeeldingen | R |  |
| Configuratie van optimalisatie van afbeeldingen |     | R |

{style="table-layout:auto"}

#### SSL-certificaten

|     | Adobe | Merchant |
| --- | --- | --- |
| SSL toegewezen certificaat - verlopen | R |  |
| SSL-certificaten voor levering | R |  |
| Aankoop en onderhoud van EV/Specific SSL cert (andere dan opgegeven standaardwaarden) en verstrekken aan Adobe |     | R |

{style="table-layout:auto"}

#### Web Application Firewall (WAF)

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid en configuratie van WAF | R |  |
| Onjuiste positieven in WAF-regels aanpakken | R | |
| Onjuiste positieven in WAF-regel melden |     | R |
| WAF Rule Tuning (NIET ONDERSTEUND) |     |     |
| WAF/CDN-logbestanden |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Merchant |
| --- | --- | --- |
| Proactieve IP-blokkering |     | R |
| Botbescherming |     | R |
| DDOS-detectie - laag 3-4 | R |   |
| DDOS-detectie - laag 7 |     | R |
| DDOS-reactie | R |   |

{style="table-layout:auto"}

#### Persoonlijke koppeling

|     | Adobe | Merchant |
| --- | --- | --- |
| PrivateLink-verbindingen configureren en onderhouden (indien gebruikt) met een VPC in eigendom van Adobe | R |   |
| PrivateLink-verbindingen configureren en onderhouden (indien gebruikt) met een VPC die eigendom is van Merchant |     | R |
| Beschikbaarheid van SSH (niet-particuliere koppeling) | R |   |
| Configuratie van PrivateLink naar het eindpunt van de Adobe Commerce Cloud Service | R |   |
| Acceptatie van PrivateLink inkomend aan het eindpunt van de Adobe Commerce Cloud Service |     | R |
| Configuratie van PrivateLink naar het VPC Service-eindpunt van Merchant |     | R |
| Acceptatie van PrivateLink naar het VPC Service-eindpunt van Merchant | R |   |
| Configuratie van integratie PrivateLink (eindpunt voor account) |     | R |
| Configuratie van merchant-bezeten VPC voor het eindpunt PrivateLink <br><br> (met inbegrip van om het even welke verbindingen van VPN) |     | R |

{style="table-layout:auto"}

### Systeem en infrastructuur

#### Toepassingsserver

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van Nginx | R |   |
| Configuratie van Nginx | R |   |
| Doorlopende kwaliteit en patches van Nginx | R |   |

{style="table-layout:auto"}

#### Besturingssysteem

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van besturingssysteem | R |   |
| Doorlopende kwaliteit en patches van het besturingssysteem | R |   |

{style="table-layout:auto"}

#### Back-up, hoge beschikbaarheid en failover

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van momentopname- en back-upproces | R |   |
| Back-ups plannen voor Staging- en productieomgevingen in Cloud Pro | R |   |
| Back-ups plannen voor omgevingen met Cloud Starter en Pro Integration |     | R |
| Beschikbaarheid van HA/failover | R |   |

{style="table-layout:auto"}

#### Cloud Servers &amp; Scaling

|     | Adobe | Merchant |
| --- | --- | --- |
| Beschikbaarheid van CPU-bronnen, datacenter, schijfruimte | R |   |
| Beschikbaarheid en uitvoering van piekcapaciteit of opwaardering van noodsituaties | R |   |
| Vulcapaciteit aanvragen |     | R |
| Het vCPU-gebruik op de limieten controleren | R |   |

{style="table-layout:auto"}

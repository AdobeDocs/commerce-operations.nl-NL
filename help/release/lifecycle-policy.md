---
title: Levenscyclusbeleid voor software
description: Leer meer over de belangrijkste datums voor het einde van de softwareondersteuning voor Adobe Commerce-releases.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 2e81a28502d369bc8903e6b9e9154e693260234d
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# Adobe Commerce-levenscyclusbeleid

Voor Adobe Commerce 2.4.4 en latere versies:

- Om het levenscyclusbeleid van Adobe Commerce te stroomlijnen en de opdracht-kritieke behoeften van klanten te steunen, breidde Adobe het steunvenster tot drie jaar uit van de Algemene datum van de Beschikbaarheid (GA) voor Adobe Commerce 2.4.4 en later. Adobe biedt kwaliteitscorrecties voor 2.4.4 en latere releases voor een periode van drie jaar. De klanten kunnen tot kwaliteitsmoeilijke situaties toegang hebben door [ Steun van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) te contacteren of door zelf-dient [[!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) als hun versie nog voor kwaliteitssteun verkiest. In de volgende tabel wordt het einde van de softwaresupportdatums voor de Adobe Commerce-releaselijnen beschreven.

- Adobe biedt beveiligingsoplossingen via een beveiligingspatchrelease voor de ondersteuningsperiode van drie jaar.

- Voor kritieke veiligheidskwesties, zoals nul-dag kwetsbaarheid, verstrekt Adobe [ hotfixes ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) voor alle klanten op een gesteunde versie, zelfs als zij niet op het recentste flard of de versie van het veiligheidspatch zijn. Een hotfix is niet uitgebreid en biedt geen oplossing voor alle beveiligingsproblemen die worden opgelost door een upgrade naar de nieuwste versie uit te voeren.

- Adobe biedt geen beveiligings- en kwaliteitsoplossingen voor services en softwareafhankelijkheden van derden (zoals PHP en MySQL) die het einde van de levensduur kunnen bereiken terwijl klanten de ondersteuningsperiode van drie jaar voor Adobe Commerce hebben. Zie de [ systeemvereisten ](../installation/system-requirements.md) voor een volledige lijst van geteste en gesteunde derdetechnologieën.

- Voor Adobe Commerce op Cloud-klanten die versie 2.4.4 en 2.4.5 gebruiken, past Adobe automatisch PHP 8.1 levenslange beveiligingsoplossingen toe op de infrastructuur, zodat deze klanten niet worden beïnvloed door PHP 8.1 end-of-support. Klanten op locatie die Adobe Commerce 2.4.4 en 2.4.5 gebruiken, moeten contact opnemen met de ondersteuning van Adobe om zo nodig beveiligingspatches voor de PHP 8.1-levensduur aan te vragen.

- Adobe biedt compatibiliteit met services en softwareafhankelijkheden van derden, terwijl klanten de ondersteuningsperiode van drie jaar voor Adobe Commerce gebruiken in het bereik van patchreleases die alleen betrekking hebben op beveiliging, maar alleen wanneer dit mogelijk is zonder dat dit wijzigingen met terugwerkende kracht tot gevolg heeft.

## Uitgebreide ondersteuning

Adobe moedigt klanten aan om zo snel mogelijk een upgrade uit te voeren. Om echter meer flexibiliteit te bieden om af te stemmen op upgradeplannen en bedrijfsbehoeften, biedt Adobe een ondersteuningsverlenging van één jaar zonder extra kosten voor Adobe Commerce-klanten op versies 2.4.4 en 2.4.5. De ondersteuningsextensie omvat kwaliteits- en beveiligingspatches voor de kerntoepassing gedurende maximaal één jaar.

>[!NOTE]
>
>Uitgebreide ondersteuning is alleen beschikbaar voor Adobe Commerce-klanten. Deze is niet beschikbaar voor de Magento Open Source-codebasis.

## Einde van softwareondersteuning

| Geen | Algemene beschikbaarheid | Eind van regelmatige steun <sup> 1 </sup> | Einde van uitgebreide ondersteuning | Afhankelijke PHP-versie | Afhankelijke MariaDB-versie |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | 8 april 2025 | 11 april 2028 | NVT | 8.3 en 8.4 | 11,4 |
| Adobe Commerce 2.4.7 | 9 april 2024 | 9 april 2027 | NVT | 8.2 en 8.3 | 10.11 <sup> 3 </sup> |
| Adobe Commerce 2.4.6 | 14 maart 2023 | 11 augustus, 2026 <sup> 2 </sup> | NVT | 8.1 en 8.2 | 10.11 <sup> 4 </sup> |
| Adobe Commerce 2.4.5 | 9 augustus 2022 | 12 augustus 2025 | 11 augustus 2026 | 8,1 | 10.6 <sup> 5 </sup> |
| Adobe Commerce 2.4.4 | 12 april 2022 | 12 april 2025 | 14 april 2026 | 8,1 | 10.6 <sup> 6 </sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup> 1 </sup> Eind van softwaresteun omvat zowel eind van kwaliteitsmoeilijke situaties als eind van veiligheidsmoeilijke situaties.
>- <sup> 2 </sup> Bijgewerkt om zich op het eind van uitgebreide steun voor 2.4.5 te richten.
>- <sup> 3 </sup> Beginnend met het 2.4.7-p6 veiligheidspatch.
>- <sup> 4 </sup> Beginnend met 2.4.6-p11 veiligheidspatch.
>- <sup> 5 </sup> Beginnend met 2.4.5-p11 veiligheidspatch.
>- <sup> 6 </sup> Beginnend met 2.4.4-p12 veiligheidspatch.
>- Zie [ Beleid van de Levenscyclus van de Software ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
    <td>V1</td>
    <td>V2</td>
    <td>V3</td>
    <td>V4</td>
  </tr>
  <tr>
    <td>2.4.4.</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7.</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8.</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Sleutel**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Regelmatige ondersteuning</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Uitgebreide ondersteuning</td>
  </tr>
 </tbody>
</table>

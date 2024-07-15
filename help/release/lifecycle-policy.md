---
title: Levenscyclusbeleid voor software
description: Leer meer over de belangrijkste datums voor het einde van de softwareondersteuning voor Adobe Commerce-releases.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce-levenscyclusbeleid

Voor Adobe Commerce 2.4.4 en latere versies:

- Om het levenscyclusbeleid van Adobe Commerce te stroomlijnen en de opdracht-kritieke behoeften van klanten te steunen, breidde de Adobe het steunvenster tot drie jaar uit van de Algemene datum van de Beschikbaarheid (GA) voor Adobe Commerce 2.4.4 en later. Adobe biedt kwaliteitscorrecties voor 2.4.4 en latere releases voor een periode van drie jaar. De klanten kunnen tot kwaliteitsmoeilijke situaties toegang hebben door [ Steun van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) te contacteren of door zelf-dient [[!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) als hun versie nog voor kwaliteitssteun verkiest. Raadpleeg de onderstaande tabel voor de einddata van de softwareondersteuning voor Adobe Commerce-releaselijnen.

- Adobe biedt beveiligingsoplossingen via een beveiligingspatchrelease voor de ondersteuningsperiode van drie jaar.

- Voor kritieke veiligheidskwesties, zoals nul-dag kwetsbaarheid, verstrekt de Adobe [ hotfixes ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) voor alle klanten op een gesteunde versie, zelfs als zij niet op het recentste flard of de versie van het veiligheidspatch zijn. Het is belangrijk om op te merken dat een hotfix geen vangst-allen is en niet alle veiligheidskwesties behandelt die door verbetering aan de recentste versie zouden worden opgelost.

- Adobe biedt geen beveiligings- en kwaliteitsoplossingen voor services en softwareafhankelijkheden van derden (zoals PHP en MySQL) die het einde van de levensduur kunnen bereiken terwijl klanten de ondersteuningsperiode van drie jaar voor Adobe Commerce hebben. Zie de [ systeemvereisten ](../installation/system-requirements.md) voor een volledige lijst van geteste en gesteunde derdetechnologieën.

- Adobe biedt compatibiliteit met services en softwareafhankelijkheden van derden, terwijl klanten de ondersteuningsperiode van drie jaar voor Adobe Commerce hebben in het bereik van patchreleases die alleen betrekking hebben op beveiliging, maar alleen wanneer dit mogelijk is zonder de wijzigingen die achteraf incompatibel zijn, in te voeren.

## Einde van softwareondersteuning

| Geen | Algemene beschikbaarheid | Eind van softwaresteun <sup> 1 </sup> | Afhankelijke PHP-versie | Afhankelijke MariaDB-versie |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 april 2024 | 9 april 2027 | 8.2 en 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 maart 2023 | 14 maart 2026 | 8.1 en 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 augustus 2022 | 9 augustus 2025 | 8,1 | 10.5 <sup> 2 </sup> |
| Adobe Commerce 2.4.4 | 12 april 2022 | 24 april 2025 | 8,1 | 10.5 <sup> 3 </sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup> 1 </sup> Eind van softwaresteun omvat zowel eind van kwaliteitsmoeilijke situaties als eind van veiligheidsmoeilijke situaties.
>- <sup> 2 </sup> Beginnend met 2.4.5-p8 veiligheidspatch.
>- <sup> 3 </sup> Beginnend met 2.4.4-p9 veiligheidspatch.
>- Zie [ Beleid van de Levenscyclus van de Software ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
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
  </tr>
  <tr>
    <td>2.4.4.</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7.</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Sleutel**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Ondersteund</td>
   <td>Beveiliging en kwaliteitspatches voor Adobe Commerce</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>

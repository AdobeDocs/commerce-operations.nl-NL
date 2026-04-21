---
title: Levenscyclusbeleid voor software
description: Leer meer over de belangrijkste datums voor het einde van de softwareondersteuning voor Adobe Commerce-releases.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce-levenscyclusbeleid

Om het Adobe Commerce-levenscyclusbeleid te stroomlijnen en de bedrijfskritieke behoeften van klanten te ondersteunen, biedt Adobe een ondersteuningsvenster van drie jaar vanaf de datum van de algemene beschikbaarheid (GA) voor elke versie en biedt het tijdens deze periode kwaliteitsoplossingen. Voor data en details op het eind van softwaresteun voor elke versie, zie het [&#x200B; Eind van softwaresteun &#x200B;](#end-of-software-support) lijst.

Tijdens het drie jaar durende supportvenster hebben klanten toegang tot:

- **de moeilijke situaties van de Kwaliteit** - Klanten kunnen tot kwaliteitsmoeilijke situaties toegang hebben door [&#x200B; Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) of door zelf-dient [[!DNL Quality Patches Tool] te contacteren &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). In de volgende tabel wordt het einde van de softwaresupportdatums voor de Adobe Commerce-releaselijnen beschreven.

- **de moeilijke situaties van de Veiligheid** - Adobe verstrekt veiligheidsmoeilijke situaties door cumulatieve veiligheidspatches en niet-cumulatieve [&#x200B; geïsoleerde dossiers van het veiligheidspatch &#x200B;](versioning-policy.md#isolated-security-fixes) voor de periode van de drie jaar steun.

- **Hotfixes** - voor kritieke veiligheidskwesties, zoals nul-dag kwetsbaarheid, verstrekt Adobe [&#x200B; hotfixes &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) voor alle klanten op een gesteunde versie, zelfs als zij niet op de recentste flardversie of veiligheidsflardversie zijn. Een hotfix is niet uitgebreid en biedt geen oplossing voor alle beveiligingsproblemen die worden opgelost door een upgrade naar de nieuwste versie uit te voeren.

Adobe biedt geen beveiligings- en kwaliteitsoplossingen voor services en softwareafhankelijkheden van derden (zoals PHP en MySQL) die het einde van de levensduur kunnen bereiken terwijl klanten in de drie jaar durende of verlengde ondersteuningsperiode voor Adobe Commerce zitten. Zie de [&#x200B; systeemvereisten &#x200B;](../installation/system-requirements.md) voor een volledige lijst van geteste en gesteunde derdetechnologieën.

## Uitgebreide ondersteuning

Adobe moedigt klanten aan om zo snel mogelijk een upgrade uit te voeren. Om echter meer flexibiliteit te bieden om af te stemmen op upgradeplannen en bedrijfsbehoeften, biedt Adobe een ondersteuningsverlenging van één jaar zonder extra kosten voor Adobe Commerce-klanten op versie 2.4.6. De ondersteuningsextensie omvat kwaliteits- en beveiligingspatches voor de kerntoepassing gedurende maximaal één jaar. De uitgebreide ondersteuning voor Adobe Commerce 2.4.4- en 2.4.5-versies loopt af in april en augustus 2026, zoals gepland.

>[!NOTE]
>
>Uitgebreide ondersteuning is alleen beschikbaar voor Adobe Commerce-klanten. Deze is niet beschikbaar voor de Magento Open Source-codebasis.

## Einde van softwareondersteuning

| Geen | Algemene beschikbaarheid | Eind van regelmatige steun <sup> 1 </sup> | Einde van uitgebreide ondersteuning |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 8 april 2025 | 31 mei 2028 | TBD |
| Adobe Commerce 2.4.7 | 9 april 2024 | 31 mei 2027 | TBD |
| Adobe Commerce 2.4.6 | 14 maart 2023 | 11 augustus 2026 | 30 augustus 2027 |
| Adobe Commerce 2.4.5 | 9 augustus 2022 | 12 augustus 2025 | 11 augustus 2026 |
| Adobe Commerce 2.4.4 | 12 april 2022 | 12 april 2025 | 14 april 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup> 1 </sup> als u een klant van Adobe Commerce bent, kunt u veiligheid en kwaliteitsmoeilijke situaties voor een extra jaar door de uitgebreide steunperiode blijven ontvangen.
>- Zie [&#x200B; Beleid van de Levenscyclus van de Software &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Extra beveiligingsoplossingen voor Adobe Commerce 2.4.4 en 2.4.5

Bij wijze van eenmalige uitzondering biedt Adobe een uitgebreide beveiligingstijd voor Adobe Commerce-versies 2.4.4 en 2.4.5 om klanten extra tijd te geven om naar Adobe Commerce as a Cloud Service te migreren of een upgrade naar een ondersteunde releaselijn uit te voeren.

Houd rekening met het volgende tijdens deze beveiligingsperiode voor inrichtingsopdrachten:

- **Geïsoleerd dossier van het veiligheidspatch slechts** - een geïsoleerd dossier van het veiligheidspatch zal voor deze versies volgens het versieschema worden vrijgegeven. Tijdens deze periode worden geen beveiligingspatchreleases (geen nieuwe -p-versies) geleverd.

  Om een geïsoleerd dossier van het veiligheidspatch toe te passen, moeten de klanten op de recentste veiligheid-enige flardversie (de recentste - p versie) voor hun gesteunde versielijn zijn, aangezien de geïsoleerde veiligheidsmoeilijke situaties exclusief tegen die versie worden getest.

- **geen kwaliteitsmoeilijke situaties of ingenieursbijstand** - geen insectenmoeilijke situaties, kwaliteitsupdates ([&#x200B; Hulpmiddel van de Patches van de Kwaliteit &#x200B;](../tools/quality-patches-tool/usage.md)), of technische bijstand ([&#x200B; de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) zal voor versies 2.4.4 of 2.4.5 tijdens deze periode worden verstrekt.

- **naleving PCI wordt niet gewaarborgd:** - Omdat 2.4.4 en 2.4.5 PHP versies gebruiken die eind van het leven hebben bereikt, kan de naleving PCI niet voor verkopers op die versies worden gewaarborgd. Als u deze versies blijft uitvoeren, kan de PCI-compatibiliteit in gevaar komen.

Om volledige veiligheidsdekking te handhaven en naleving PCI te verzekeren, moeten de klanten aan een momenteel gesteunde versie van Adobe Commerce zo spoedig mogelijk bevorderen of aan [&#x200B; Adobe Commerce as a Cloud Service &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview) migreren.

| Geen | Algemene beschikbaarheid | Einde van uitgebreide ondersteuning | Oplossingen voor einde van beveiliging |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 9 augustus 2022 | 11 augustus 2026 | Mei 2027 |
| Adobe Commerce 2.4.4 | 12 april 2022 | 14 april 2026 | Mei 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Aanvullende beveiligingsoplossingen zijn alleen beschikbaar voor Adobe Commerce-klanten en zijn niet beschikbaar voor de Magento Open Source-codebasis.


## Tijdlijn voor ondersteuning

De steunchronologie kaarten steunen periodes kwartaal door kwartaal voor elke de versielijn van Adobe Commerce. Gebruik de lijsten die vroeger in dit onderwerp voor nauwkeurige einddata worden verstrekt.

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
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
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
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Uitgebreide beveiligingsoplossingen</td>
  </tr>
 </tbody>
</table>

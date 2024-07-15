---
title: Releaseplanning
description: Ontdek wanneer Adobe de release van nieuwe functies voor Adobe Commerce gaat aankondigen.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# Releaseplanning

De Adobe streeft voortdurend naar het juiste evenwicht tussen het maken van productverbeteringen eenvoudig en voorspelbaar terwijl het leveren van verbeteringen en nieuwe eigenschappen aan vroege adopters sneller (zie [ versioning beleid ](versioning-policy.md)). Het doel van dit schema is de data te bepalen waarop de Adobe van plan is de introductie van belangrijke nieuwe functies aan te kondigen. Deze kenmerken kunnen het hele jaar door variëren. Adobe geeft echter regelmatig en voortdurend verbeteringen door voor uitbreidbaarheidsinstrumenten, -infrastructuur en SaaS-producten (services) tussen de data die op deze pagina zijn vermeld.

De Adobe geeft [ flarden ](versioning-policy.md#patch-release) voor elke gesteunde versielijn van de kernAdobe Commerce PHP toepassing vrij. De versies van de flard zijn kansen om de kern codebase te bevorderen om uw platform veilig, betrouwbaar, en prestatieshoog te houden. De eigenschappen zijn onafhankelijk van de kerncodebase en zijn beschikbaar door [ externe module, uitbreiding, hulpmiddel, of de Webdienst ](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>Vanaf 2024 biedt Adobe geen &quot;pre-release&quot;-toegang meer tot patches. In plaats daarvan, voor 2.4.7 en later, kunnen de klanten van Adobe Commerce [ bètaversies ](beta.md) gebruiken om tot pre-algemene beschikbaarheidscode voor het testen en ontwikkelingsdoeleinden toegang te hebben.

De volgende tabel bevat de datums voor geplande releases (de datums kunnen worden gewijzigd):

<table>
<thead>
  <tr>
    <th>Algemene beschikbaarheid</th>
    <th>Functies</th>
    <th>PHP Core</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong> Legend </strong>
         <ul>
           <li><strong><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> B2B </strong> - Nieuwe eigenschappen, verhogingen, en insectenmoeilijke situaties voor de uitbreiding B2B voor Adobe Commerce. Voor details over versies van de B2B uitbreiding, zie de <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html"> B2B Nota's van de Versie </a>.</li>
            <li><strong><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> Uitbreidbaarheid </strong> - Nieuwe ontwikkelaarshulpmiddelen en de diensten voor uit-van-procesrekbaarheid die onafhankelijk van flardversies worden geleverd. Bijvoorbeeld Admin UI SDK, Adobe I/O Events for Commerce en API Mesh.</li>
            <li><strong><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> Infrastructuur </strong> - Nieuwe eigenschappen en verbeteringen aan Adobe Commerce op cloudinfrastructuur en de Cloud Tools Suite voor Commerce-pakketten, die zijn ontworpen om Adobe Commerce-installaties en -upgrades op het Cloud-platform te implementeren en te beheren.</li>
            <li><strong><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> Patches </strong> - Updates aan de kernAdobe Commerce PHP toepassing die veiligheid, naleving, prestaties, en high-priority kwaliteitsmoeilijke situaties omvatten.</li>
            <li><strong><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> de diensten </strong> - Nieuwe eigenschappen SaaS die onafhankelijk van flardversies worden geleverd. Bijvoorbeeld Catalog Service, Live Search en Product Recommendations.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 februari 2024</td>
    <td><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> </a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> Infrastructuur </a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> de Diensten van de Uitbreidbaarheid <a [#$sd1_sf1_tu19]> </a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> de flarden van de Veiligheid </a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>12 maart 2024</td>
    <td>—</td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"> het flard van Beta </a>: 2.4.7-bèta3</td>
  </tr>
  <tr>
    <td>9 april 2024</td>
    <td><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> </a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> Infrastructuur </a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> de Diensten van de Uitbreidbaarheid <a [#$sd1_sf1_tu33]> </a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong> Adobe Commerce 2.4.7 </a></strong>:<ul><li>Prestatieverbeteringen</li><li>Kwaliteitsverbeteringen</li><li>Verbeterde beveiliging</li><li>Afhankelijkheidsupdates van derden</li></ul><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> de flarden van de Veiligheid </a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 juni 2024</td>
    <td><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> </a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> Infrastructuur </a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> de Diensten van de Uitbreidbaarheid <a [#$sd1_sf1_tu49]> </a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> de flarden van de Veiligheid </a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 augustus 2024</td>
    <td><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> </a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> Infrastructuur </a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> de Diensten van de Uitbreidbaarheid <a [#$sd1_sf1_tu59]> </a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> de flarden van de Veiligheid </a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 oktober 2024</td>
    <td><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> </a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> Infrastructuur </a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> de Diensten van de Uitbreidbaarheid <a [#$sd1_sf1_tu69]> </a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"> het flard van Beta </a>: 2.4.8-beta1 <br><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> flarden van de Veiligheid </a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>

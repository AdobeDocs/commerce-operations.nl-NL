---
title: Releaseplanning
description: Ontdek wanneer Adobe de release van belangrijke nieuwe functies voor Adobe Commerce gaat aankondigen.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 7edf6d5a8dfe58a86f27e97816e4d850bc21babc
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# Releaseplanning

Adobe streeft voortdurend naar het juiste evenwicht tussen het eenvoudig en voorspelbaar maken van productupgrades en het sneller aanbieden van verbeteringen en nieuwe functies voor vroege gebruikers (zie [versiebeleid](versioning-policy.md)). Het doel van dit schema is de data te bepalen waarop de Adobe van plan is de introductie van belangrijke nieuwe functies aan te kondigen. Deze kenmerken kunnen het hele jaar door variëren. Adobe geeft echter regelmatig en voortdurend verbeteringen door voor uitbreidbaarheidsinstrumenten, -infrastructuur en SaaS-producten (services) tussen de data die op deze pagina zijn vermeld.

Adobe [patches](versioning-policy.md#patch-release) voor elke ondersteunde releaselijn van de kern-Adobe Commerce PHP-toepassing. De versies van de flard zijn kansen om de kern codebase te bevorderen om uw platform veilig, betrouwbaar, en prestatieshoog te houden. Functies zijn onafhankelijk van de kerncodebase en zijn beschikbaar via [externe module, extensie, gereedschap of webservice](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>Vanaf 2024 biedt Adobe geen &quot;pre-release&quot;-toegang meer tot patches. In plaats daarvan kunnen Adobe Commerce-klanten voor 2.4.7 en hoger [bèta-releases](beta.md) toegang tot de algemene beschikbaarheidscode voor test- en ontwikkelingsdoeleinden.

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
      <td colspan="3"><strong>Legenda</strong>:
         <ul>
            <li><strong><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> B2B</strong>—Nieuwe functies, verbeteringen en foutoplossingen voor de B2B-extensie voor Adobe Commerce.</li>
            <li><strong><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> Uitbreidbaarheid</strong>—Nieuwe ontwikkelaarshulpmiddelen en de diensten voor uit-van-procesrekbaarheid die onafhankelijk van flardversies worden geleverd. Bijvoorbeeld Admin UI SDK, Adobe I/O Events for Commerce, en API Mesh.</li>
            <li><strong><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> Infrastructuur</strong>—Nieuwe functies en verbeteringen voor Adobe Commerce op cloudinfrastructuur en de Cloud Tools Suite voor handel, die zijn ontworpen om Adobe Commerce-installaties en -upgrades te implementeren en beheren op het Cloud-platform.</li>
            <li><strong><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> Patches</strong>—Updates voor de belangrijkste Adobe Commerce PHP-toepassing die oplossingen voor beveiliging, compatibiliteit, prestaties en hoge prioriteit bevatten.</li>
            <li><strong><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> Services</strong>—Nieuwe SaaS-functies die onafhankelijk van patchreleases worden geleverd. Bijvoorbeeld Catalog Service, Live Search en Product Recommendations.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 februari 2024</td>
    <td><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Uitbreidbaarheid</a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastructuur</a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Services</a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Beveiligingspatches</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>19 maart 2024</td>
    <td>—</td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta-patch</a>: 2.4.7-bèta3</td>
  </tr>
  <tr>
    <td>9 april 2024</td>
    <td><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Uitbreidbaarheid</a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastructuur</a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Services</a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>Prestatieverbeteringen</li><li>Kwaliteitsverbeteringen</li><li>Verbeterde beveiliging</li><li>Afhankelijkheidsupdates van derden</li></ul><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Beveiligingspatches</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 juni 2024</td>
    <td><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Uitbreidbaarheid</a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastructuur</a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Services</a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Beveiligingspatches</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 augustus 2024</td>
    <td><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Uitbreidbaarheid</a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastructuur</a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Services</a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Beveiligingspatches</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 oktober 2024</td>
    <td><img alt="B2B-functiepictogram" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Pictogram voor uitbreidbaarheidsfunctie" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Uitbreidbaarheid</a><br><img alt="Pictogram Infrastructuurfunctie" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastructuur</a><br><img alt="Pictogram voor de functie Services" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Services</a></td>
    <td><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta-patch</a>: 2.4.8-bèta1<br><img alt="Patchvrijgavepictogram" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Beveiligingspatches</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>

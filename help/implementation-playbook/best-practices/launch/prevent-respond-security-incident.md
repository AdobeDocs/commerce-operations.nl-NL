---
title: Voorkomen en reageren op een beveiligingsincident
description: Leer over beste praktijken om veiligheidsincidenten in uw Adobe Commerce op het project van de wolkeninfrastructuur te vermijden en te antwoorden.
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Tips en trucs om een beveiligingsincident te helpen voorkomen en erop te reageren

Adobe Commerce security werkt onder een [Gedeelde verantwoordelijkheid](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) model. Het is van essentieel belang om te begrijpen waarvoor Adobe en uw technische teams verantwoordelijk zijn. Hieronder geven we een overzicht [Aanbevolen werkwijzen voor beveiliging](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) om ervoor te zorgen dat uw project de beste beveiligingscontroles heeft en hoe u het beste kunt reageren op een beveiligingsincident.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur

## Reageren op een incident

Er zijn vele overwegingen aangezien u op een veiligheidsincident antwoordt. Als u vermoedt dat u een recent beveiligingsincident voor uw Adobe Commerce hebt ondervonden in het kader van een cloudinfrastructuurproject, is het belangrijk dat u de toegang tot alle beheerdersgebruikersaccounts controleert, geavanceerde multifactorverificatie-besturingselementen (MFA) inschakelt, kritieke logbestanden behoudt en beveiligingsupdates voor uw versie van Adobe Commerce controleert.

Hieronder vindt u meer aanbevelingen. Zij kunnen helpen onbevoegde toegang verhinderen en het proces voor verdere invallingsanalyse beginnen.

## Hoe te om veiligheidsincidenten te verhinderen

Volg deze best practices op het gebied van beveiliging om beveiligingsincidenten die gevolgen hebben voor uw Adobe Commerce-sites en winkels proactief te voorkomen:

- [2FA inschakelen voor beheertoegang](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
Verificatie met twee factoren wordt veel gebruikt en het is gebruikelijk om toegangscodes te genereren voor verschillende websites op dezelfde app. Dit zorgt ervoor dat alleen u zich kunt aanmelden bij uw gebruikersaccount. Als je je wachtwoord verliest of als een bot het vermoedt, voegt tweeledige verificatie een extra beveiligingslaag toe.
- [MFA inschakelen voor SSH-toegang](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Wanneer MFA op een project wordt toegelaten, moet alle Adobe Commerce op de rekeningen van de wolkeninfrastructuur met de toegang van SSH een authentificatiewerkschema volgen dat of een twee-factor authentificatie (2FA) code, of een API teken en een certificaat van SSH vereist om tot het milieu toegang te hebben.
- Voer een upgrade uit naar de nieuwste versie van Adobe Commerce.
Adobe geeft beveiligings- en functionele patches uit voor elke ondersteunde release Adobe Commerce.
- Een [niet-standaard admin-URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe raadt u aan een unieke, aangepaste Admin-URL te gebruiken in plaats van de standaard `admin` of een gemeenschappelijke term zoals *achterste*. Hoewel deze configuratieverandering niet direct uw plaats tegen een bepaalde slechte actor beschermt, kan het blootstelling aan manuscripten verminderen die proberen om onbevoegde toegang te krijgen.
- Voorkomen dat configuratiewaarden worden bewerkt of bijgewerkt in de beheerfunctie  [`bin/magento config:set` CLI-opdracht met de `lock env` configuratieoptie](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Met deze optie vergrendelt u de configuratiewaarde zodat deze niet kan worden bewerkt in de beheerfunctie, of voorkomt u wijzigingen in een instelling die al is vergrendeld. Als u deze optie gebruikt, worden configuratiewijzigingen naar de `<Commerce base dir>/app/etc/env.php` bestand.
- Stel de [Adobe Commerce Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html).
Met de verbeterde beveiligingsscan kunt u elk van uw Adobe Commerce-sites, inclusief PWA, controleren op bekende beveiligingsrisico&#39;s en malware en patchupdates en beveiligingsmeldingen ontvangen.
- [Toegang van Admin-gebruikers controleren en bijwerken](https://docs.magento.com/user-guide/system/permissions-users-all.html) en [beveiligingsinstellingen](https://docs.magento.com/user-guide/stores/security-admin.html).
   - We raden u aan oude, ongebruikte of verdachte accounts te verwijderen en wachtwoorden voor alle Admin-gebruikers te roteren.
   - Bekijk en werk de Geavanceerde beveiligingsinstellingen&lt; voor uw project bij. Met de beveiligingsconfiguratie Admin kunt u een geheime sleutel aan URL&#39;s toevoegen, opgeven dat wachtwoorden hoofdlettergevoelig moeten zijn en kunt u de duur van beheersessies beperken, inclusief de levensduur van wachtwoorden, en het aantal aanmeldingspogingen dat kan worden uitgevoerd voordat de beheergebruikersaccount is vergrendeld. Voor verhoogde veiligheid, kunt u de lengte van toetsenbordinactiviteit vormen alvorens de huidige zitting verloopt, en vereisen de gebruikersbenaming en het wachtwoord om case-sensitive te zijn.
- Adobe Commerce controleren op [wolkenprojectgebruikers](https://devdocs.magento.com/cloud/project/user-admin.html).
We raden u aan oude, ongebruikte of verdachte accounts te verwijderen en gebruikers te vragen hun wachtwoorden te wijzigen.
- Audit [SSH-toetsen](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) voor Adobe Commerce over cloudinfrastructuur.
We raden u aan SSH-toetsen te bekijken, te verwijderen en te roteren.
- Voer de Lijst van het Toegangsbeheer (ACL) voor Admin uit.
U kunt een Snelle ACL van de Rand in combinatie met een douane gebruiken [VCL-codefragment](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) om inkomende verzoeken te filtreren en toegang door IP adres aan Admin toe te staan.

## Een incident analyseren

De eerste stap van de analyse van incidenten is om zoveel mogelijk feiten te verzamelen, zo snel als u kunt. Het verzamelen van informatie over het incident kan u helpen de potentiële oorzaak van het incident te bepalen. Adobe Commerce biedt de onderstaande tools voor hulp bij uw analyse van incidenten.

- [Handelingenlogboeken voor Beheer controleren](https://docs.magento.com/user-guide/system/action-log-report.html).
In het rapport Handelingenlogs wordt een gedetailleerd overzicht weergegeven van alle beheeracties die zijn ingeschakeld voor loggen. Elke record heeft een tijdstempel en registreert het IP-adres en de naam van de gebruiker. Het logboekgegeven omvat admin gebruikersgegevens en verwante veranderingen die tijdens de actie werden aangebracht.
- Gebeurtenissen analyseren met de [Waarneming voor Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Met het gereedschap Waarnemen voor Adobe Commerce kunt u complexe problemen analyseren om de onderliggende oorzaken te achterhalen. In plaats van het bijhouden van ongelijke gegevens kunt u tijd besteden aan het correleren van gebeurtenissen en fouten om dieper inzicht te krijgen in de oorzaken van knelpunten in de prestaties.
Het hulpmiddel is bedoeld om een duidelijk beeld van enkele potentiële plaatkwesties te geven om u te helpen de worteloorzaak identificeren en plaatsen te houden optimaal presteert. Klik op de koppeling naar de bovenstaande documentatie voor het gereedschap Waarneming voor Adobe Commerce voor toegang tot de documentatie van het gereedschap. Er is een sectie in de documentatie waarin alle informatie wordt beschreven die op de **Beveiliging** tab.
- Logbestanden analyseren met [New Relic Logs](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Tot de Adobe Commerce on cloud Infrastructure Pro-projecten behoren [New Relic Logs](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) service. De dienst wordt pre-gevormd om alle logboekgegevens van uw het Opvoeren en milieu&#39;s van de Productie samen te voegen om het in een gecentraliseerd logboekbeheersdashboard te tonen.
U kunt de New Relic Logs-service gebruiken om de volgende taken uit te voeren:
   - Gebruiken [New Relic-query&#39;s](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) om geaggregeerde loggegevens te zoeken.
   - Loggegevens visualiseren via de toepassing New Relic Logs.

## Aanvullende informatie

- [Framework voor analyse van hoofdoorzaken](https://sansec.io/kb/incident-response/magento-root-cause-analysis).

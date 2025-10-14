---
source-git-commit: 4dd926ca7014c9e007a8c2c847e076064eb8d170
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 1%

---
# Bijdragen

Bedankt dat u hebt gekozen om bij te dragen!

Hieronder volgt een reeks richtlijnen die moeten worden gevolgd wanneer u een bijdrage levert aan dit project.

## Gedragscode

Dit project voldoet aan de Adobe-[gedragscode](code-of-conduct.md). Door deelname,
u wordt verwacht deze code te handhaven. Geef een onacceptabel gedrag aan
[&#x200B; Grp-opensourceoffice@adobe.com &#x200B;](mailto:Grp-opensourceoffice@adobe.com).

## Documentatie voor de bijdragegids

Zie de [&#x200B; Gids van de Medewerker &#x200B;](https://experienceleague.adobe.com/nl/docs/contributor/contributor-guide/introduction).

## Heb je een vraag?

Begin met het indienen van een probleem. De bestaande commissies voor dit project werken eraan om
consensus over de richting van projecten en het uitwerken van oplossingen binnen de verschillende thema&#39;s
(indien van toepassing).

## Licentieovereenkomst voor contribuant

Alle bijdragen van derden aan dit project moeten vergezeld gaan van een ondertekende contribuant
licentieovereenkomst. Dit geeft Adobe toestemming om uw bijdragen opnieuw te verdelen
als onderdeel van het project. [&#x200B; Onderteken onze CLA &#x200B;](https://opensource.adobe.com/cla.html). U
slechts één keer een Adobe CLA hoeven in te dienen, dus als u eerder een CLA hebt ingediend,
je bent klaar om te gaan !

## Codebeoordelingen

Alle opmerkingen moeten in de vorm van een &quot;pull&quot;-verzoek worden ingediend en moeten worden herzien
door projectbevrachters. Lees {de documentatie van het trekvraag van 0} GitHub [&#128279;](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
voor meer informatie over het verzenden van trekkingsverzoeken.

<!--
Lastly, please follow the [pull request template](PULL_REQUEST_TEMPLATE.md) when
submitting a pull request!
-->

## Van contribuant aan vastleggingen

We houden van bijdragen van onze gemeenschap! Als u een stap verder wilt gaan dan contribuant
en wordt een commissie met volledige schrijftoegang en een inspraak in het project, moet u
worden uitgenodigd voor het project. De bestaande comités hanteren een interne voordracht
proces dat een luie consensus moet bereiken (stilte is goedkeuring) vóór uitnodigingen
worden afgegeven. Als u zich gekwalificeerd voelt en meer betrokken wilt worden,
het is vrij om contact op te nemen met bestaande toezeggingen om hierover te praten .

## Beveiligingsproblemen

Beveiligingsproblemen moeten niet worden gerapporteerd in deze Issue Tracker. In plaats daarvan, [&#x200B; dossier een kwestie aan onze veiligheidsdeskundigen &#x200B;](https://helpx.adobe.com/nl/security/alertus.html).

## Nieuwe hooglichten

Als uw veranderingen nieuwe onderwerpen, significante updates, of correcties introduceren die moeten worden benadrukt, kunt u een korte beschrijving aan [&#x200B; toevoegen wat Nieuwe sectie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/operational-guides/home#whats-new) recht van het lichaam van uw trekkrachtverzoek is.

Een nieuwe markering toevoegen:

1. Neem de tag `whatsnew` met de juiste beschrijving op in de hoofdtekst van de aanroepaanvraag aan het einde. De beschrijving zou context over de verandering en een verbinding aan het doelonderwerp of de onderwerpen moeten verstrekken. Gebruik de volgende indeling (codeblokken zijn alleen bedoeld voor weergave, neem ze niet op in de hoofdtekst van de aanroepingsaanvraag):

   ```text
   whatsnew
   Short description of the change in the [target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html).
   ```

   of, als er meerdere onderwerpen zijn:

   ```text
   whatsnew
   Short description of the changes in the [first target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html), [second target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-target-topic.html), and [third target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/third-target-topic.html).
   ```

   u kunt ook lijsten gebruiken voor meerdere hooglichten:

   ```text
   whatsnew
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

   ```text
   whatsnew
   The following changes were made to the documentation:
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

1. Voeg ondersteunde labels toe die het type wijziging aangeven. Ondersteunde labels bevatten labels voor elk type wijziging, zoals:

   - `new-topic` - voor nieuwe onderwerpen
   - `major-update` - voor belangrijke updates die belangrijke wijzigingen in inhoud, structuur of functionaliteit kunnen bevatten
   - `technical` - voor technische wijzigingen die niet als belangrijke updates worden beschouwd, maar die wel aandacht behoeven

   en eventueel etiketten voor het toepassingsgebied van de wijziging, zoals:

   - `qpt` - voor wijzigingen die betrekking hebben op het gereedschap Kwaliteitspatch

**Belangrijk:**

1. Het `whatsnew` -onderdeel moet beginnen met de tag `whatsnew` en zich helemaal aan het einde van de hoofdtekst van de trekkingsaanvraag bevinden.
1. In de beschrijvingen van de wijzigingen moeten ook werkkoppelingen staan. Controleer of de koppelingen correct zijn en leiden naar de gewenste onderwerpen. Als het onderwerp nieuw is, verifieer dat de verbindingen na het samenvoegen van het trekkingsverzoek werken en het publiceren van het nieuwe onderwerp. U kunt de koppelingen herstellen nadat de pull-aanvraag is samengevoegd.

Voor voorbeelden, onderzoek in gesloten trekkingsverzoeken in de bewaarplaats om te zien hoe de bestaande hoogtepunten worden geformatteerd, en hen te vergelijken met [&#x200B; wat Nieuwe sectie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/operational-guides/home#whats-new) is om te zien hoe zij in de documentatie verschijnen.

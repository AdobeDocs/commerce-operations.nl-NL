---
title: Aanbevolen werkwijzen voor codebeheer
description: Meer informatie over best practices voor codebeheer voor de ontwikkelingsfase van Adobe Commerce-projecten.
feature: Best Practices
role: Developer
source-git-commit: 0902997fb0bf862b37a5e29026f462bf8c86c96b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Beste werkwijzen voor codebeheer voor Adobe Commerce

Dit onderwerp wordt ontworpen om u te helpen beslissen of om Git of Composer te gebruiken om douanecode, met aandacht voor versiebeheer, codeingewikkeldheid, en gebiedsdeelbeheer te verspreiden.

>[!NOTE]
>
>Deze beste praktijken zijn het meest geschikt voor migraties en implementaties; minder zo voor de enig-moduleontwikkeling.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

Het betreft beide [algemene referentiearchitectuur (GRA)](../../architecture/global-reference/overview.md) en installaties voor één instantie.

## Definities

{{$include /help/_includes/gra-definitions.md}}

## Wanneer gebruikt u Git of Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Code die hoofdzakelijk door Git wordt beheerd</th>
    <th>Code die hoofdzakelijk door Composer wordt beheerd</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Wanneer gebruiken voor een single-instance opstelling</td>
    <td>
      <ul>
        <li><strong>Standaardbenadering voor het beheren van code voor een Single Instance Setup</strong></li>
        <li>Wanneer de basis van de code in de toekomst geen deel zal uitmaken van een meermerkige GRA</li>
        <li>Wanneer alle merken op één instantie als websites worden uitgevoerd</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Wanneer de codebasis in de toekomst deel kan of zal worden van een multi-instantie opstelling</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Wanneer gebruiken voor een installatie van meerdere instanties</td>
    <td>
      <ul>
        <li>Wanneer bijna alle modules onderling zijn gekoppeld (niet aanbevolen)</li>
        <li>Wanneer de code door een team wordt gehandhaafd dat niet vertrouwd met Composer is</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Standaardbenadering voor het beheren van code voor een meervoudige instantie-instelling</strong></li>
        <li>Wanneer de Adobe de codebasis handhaaft of het handhaven team vertrouwd met Composer is</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Eigenschappenmatrix

| Functie | Git | Composer |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Hoofdgegevensopslagplaats voor code | Alle code bevindt zich in één of enkele Git-opslagplaatsen | Alle code bevindt zich in de pakketten in een Composer-opslagplaats<br>Elk Composer-pakket wordt vertegenwoordigd door een Git-opslagplaats |
| Codelocatie | Ontwikkeling vindt plaats in de `app/` directory | Ontwikkeling vindt plaats in de `vendor/` directory |
| Core Upgrade-beheer | Adobe Commerce core wordt geïnstalleerd en geüpgraded met Composer, het resultaat wordt vastgelegd in Git | Adobe Commerce core wordt geïnstalleerd en geüpgraded met Composer; het resultaat wordt vastgelegd in Git |
| Modulebeheer van derden | Modules van derden worden geïnstalleerd in `vendor/` als ze via de markt zijn geïnstalleerd of packagist.org. Anders worden ze geïnstalleerd in `app/` | Alle modules van derden worden geïnstalleerd in de `vendor/` directory |
| Uitstoot | De vrijgave wordt gekenmerkt door `git merge` en `git pull` of `git checkout` opdrachten | De vrijgave wordt gekenmerkt door `composer update` en `git pull` of `git checkout` opdrachten |
| Aantal Git-opslagruimten | Weinig | Veel |
| Ontwikkelingscomplexiteit | eenvoudig | Complex |
| Complexiteit verzoek volledig uitvoeren | eenvoudig | Complex |
| Complexiteit van coderevisie | eenvoudig | eenvoudig |
| Complexiteit van updates in Dev/QA/UAT-omgeving | eenvoudig | Complex |
| GRA-ondersteuning | ![Pictogram Ja](../../../assets/yes.svg) | ![Pictogram Ja](../../../assets/yes.svg) |
| Modules kunnen automatisch externe bibliotheken installeren | ![Geen pictogram](../../../assets/no.svg) | ![Pictogram Ja](../../../assets/yes.svg) |
| Flexibiliteit in GRA-samenstelling | ![Geen pictogram](../../../assets/no.svg) | ![Pictogram Ja](../../../assets/yes.svg) |
| Beheer van moduleafhankelijkheid | ![Pictogram Ja](../../../assets/yes.svg) Alleen via `module.xml`, beperkte functionaliteit | ![Pictogram Ja](../../../assets/yes.svg) Volledig afhankelijkheidsbeheer via `composer.json` |
| Moduleversie | ![Pictogram Ja](../../../assets/yes.svg) U kunt een versie definiëren, maar u kunt geen specifieke versie installeren | ![Pictogram Ja](../../../assets/yes.svg) Ondersteuning voor volledige versies |
| Betaalde services vereist | Git-opslagplaats | Git-opslagplaats, Private Packagist (± 600 euro per jaar) |
| Integratie van bitemand met Jira mogelijk | ![Pictogram Ja](../../../assets/yes.svg) | ![Pictogram Ja](../../../assets/yes.svg) |
| Wijzigingen in code die direct beschikbaar is voor installatie | ![Pictogram Ja](../../../assets/yes.svg) | ![Pictogram Ja](../../../assets/yes.svg) |

## Oplossingen om te vermijden

1. **Composer combineren en `app/code` voor uw modules**

   Resultaat in het hebben van alle nadelen van beide die stijlen van het codebeheer in uw project worden gecombineerd. Het voegt onnodige complexiteit, instabiliteit en gebrek aan flexibiliteit toe.

   Bijvoorbeeld:
   - Verklaar zowel de werkschema&#39;s van de Git als van de Composer (in plaats van slechts één) aan het ontwikkelingsteam.
   - Incompatibele modules installeren in `app/code` aangezien er niets is om dat tegen te houden .
   - Een module verplaatsen vanuit `app/code` naar Composer (of omgekeerd) is omslachtig, vooral bij de lopende ontwikkeling.

1. **Satis Package Manager**

   Private Packagist kost ± 600 euro per jaar. Deze kosten zijn voor de hele GRA samen, niet per merk. Probeer deze kosten niet te vermijden door de vrije oplossing Satis te gebruiken. Uw pakketten worden niet automatisch bijgewerkt wanneer u op Vastleggen drukt. Satis heeft ook geen ingebouwde vergunning. U moet een webserver onderhouden om Satis uit te voeren. Je geeft uiteindelijk een veelvoud van de abonnementskosten voor Private Packagist door om Satis te behouden.

1. **Begin met Git en ga vervolgens naar Composer**

   Maak de keus voor een benadering van het codebeheer bij het begin van uw project. Het schakelen van Git naar Composer of omgekeerd, met aan de gang zijnde ontwikkeling is omslachtig en kan tot codeverlies en of het verlies van de revisiegeschiedenis leiden.

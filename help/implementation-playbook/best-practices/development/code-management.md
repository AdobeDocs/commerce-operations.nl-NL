---
title: Aanbevolen werkwijzen voor codebeheer
description: Meer informatie over best practices voor codebeheer voor de ontwikkelingsfase van Adobe Commerce-projecten.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Beste werkwijzen voor codebeheer voor Adobe Commerce

Dit onderwerp wordt ontworpen om u te helpen beslissen of om Git of Composer te gebruiken om douanecode, met aandacht voor versiebeheer, codeingewikkeldheid, en gebiedsdeelbeheer te verspreiden.

>[!NOTE]
>
>Deze beste praktijken zijn het meest geschikt voor migraties en implementaties; minder zo voor de enig-moduleontwikkeling.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

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
        <li>Wanneer Adobe de codebasis onderhoudt of het onderhoudsteam vertrouwd is met Composer</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Eigenschappenmatrix

| Functie | Git | Composer |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Hoofdgegevensopslagplaats voor code | Alle code bevindt zich in één of enkele Git-opslagplaatsen | Alle code verblijft in de pakketten in een bewaarplaats Composer <br> Elk enig pakket Composer wordt vertegenwoordigd door een bewaarplaats van het Git |
| Codelocatie | De ontwikkeling vindt plaats in de map `app/` | De ontwikkeling vindt plaats in de map `vendor/` |
| Core Upgrade-beheer | Adobe Commerce core wordt geïnstalleerd en geüpgraded met Composer, het resultaat wordt vastgelegd in Git | Adobe Commerce core wordt geïnstalleerd en geüpgraded met Composer; het resultaat wordt vastgelegd in Git |
| Modulebeheer van derden | Modules van derden worden geïnstalleerd in `vendor/` als ze via de markt of packagist.org worden geïnstalleerd. Anders worden ze geïnstalleerd in `app/` | Alle modules van derden worden geïnstalleerd in de map `vendor/` |
| Uitstoot | De release wordt gekenmerkt door `git merge` - en `git pull` - of `git checkout` -opdrachten | De release wordt gekenmerkt door `composer update` - en `git pull` - of `git checkout` -opdrachten |
| Aantal Git-opslagruimten | Weinig | Veel |
| Ontwikkelingscomplexiteit | eenvoudig | Complex |
| Complexiteit verzoek volledig uitvoeren | eenvoudig | Complex |
| Complexiteit van coderevisie | eenvoudig | eenvoudig |
| Complexiteit van updates in Dev/QA/UAT-omgeving | eenvoudig | Complex |
| GRA-ondersteuning | ![ ja pictogram ](../../../assets/yes.svg) | ![ ja pictogram ](../../../assets/yes.svg) |
| Modules kunnen automatisch externe bibliotheken installeren | ![ Geen pictogram ](../../../assets/no.svg) | ![ ja pictogram ](../../../assets/yes.svg) |
| Flexibiliteit in GRA-samenstelling | ![ Geen pictogram ](../../../assets/no.svg) | ![ ja pictogram ](../../../assets/yes.svg) |
| Beheer van moduleafhankelijkheid | ![ ja pictogram ](../../../assets/yes.svg) slechts door `module.xml`, beperkte functionaliteit | ![ ja pictogram ](../../../assets/yes.svg) Volledige gebiedsdeelbeheer door `composer.json` |
| Moduleversie | ![ ja pictogram ](../../../assets/yes.svg) U kunt een versie bepalen, maar u kunt geen specifieke versie installeren | ![ ja pictogram ](../../../assets/yes.svg) Volledige versiessteun |
| Betaalde services vereist | Git-opslagplaats | Git-opslagplaats, Private Packagist (± 600 euro per jaar) |
| Integratie van bitemand met Jira mogelijk | ![ ja pictogram ](../../../assets/yes.svg) | ![ ja pictogram ](../../../assets/yes.svg) |
| Wijzigingen in code die direct beschikbaar is voor installatie | ![ ja pictogram ](../../../assets/yes.svg) | ![ ja pictogram ](../../../assets/yes.svg) |

## Oplossingen om te vermijden

1. **Combinerend Composer en `app/code` voor uw modules**

   Resultaat in het hebben van alle nadelen van beide die stijlen van het codebeheer in uw project worden gecombineerd. Het voegt onnodige complexiteit, instabiliteit en gebrek aan flexibiliteit toe.

   Bijvoorbeeld:
   - Verklaar zowel de werkschema&#39;s van de Git als van de Composer (in plaats van slechts één) aan het ontwikkelingsteam.
   - Installeer incompatibele modules in `app/code` omdat er niets is om dat te voorkomen.
   - Het verplaatsen van een module van `app/code` naar Composer (of omgekeerd) is omslachtig, vooral bij de lopende ontwikkeling.

1. **Satis de Manager van het Pakket**

   Private Packagist kost ± 600 euro per jaar. Deze kosten zijn voor de hele GRA samen, niet per merk. Probeer deze kosten niet te vermijden door de vrije oplossing Satis te gebruiken. Uw pakketten worden niet automatisch bijgewerkt wanneer u op Vastleggen drukt. Satis heeft ook geen ingebouwde vergunning. U moet een webserver onderhouden om Satis uit te voeren. Je geeft uiteindelijk een veelvoud van de abonnementskosten voor Private Packagist door om Satis te behouden.

1. **Begin met Git, dan beweging aan Composer**

   Maak de keus voor een benadering van het codebeheer bij het begin van uw project. Het schakelen van Git naar Composer of omgekeerd, met aan de gang zijnde ontwikkeling is omslachtig en kan tot codeverlies en of het verlies van de revisiegeschiedenis leiden.

---
title: Voorbeeld met een gedeelde configuratie
description: Zie een voorbeeld van hoe te om montages in een ontwikkelingssysteem met een gedeeld configuratiedossier te veranderen.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Voorbeeld met een gedeelde configuratie

In dit voorbeeld wordt getoond hoe u de volgende instellingen in uw ontwikkelingssysteem kunt wijzigen, het gedeelde configuratiebestand `config.php` in uw constructiesysteem kunt bijwerken en dezelfde instellingen in uw productiesysteem kunt implementeren:

- Tijdzone
- Gewichtseenheid

Deze montages zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > Algemeen > **Algemeen**.

U kunt de zelfde procedure gebruiken om het even welke niet gevoelige, niet systeem-specifieke montages in de volgende verwijzingen te vormen:

- [Verwijzing naar andere configuratiepaden](../reference/config-reference-general.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Referentie voor configuratiepaden voor Commerce Enterprise B2B-extensies](../reference/config-reference-b2b.md)

## Voordat u begint

Alvorens u begint, de toestemmingen en de eigendom van het opstellingssysteem zoals besproken in [ Vereisten voor ontwikkeling, bouwt, en productiesystemen ](../deployment/prerequisites.md).

## Veronderstellingen

Dit onderwerp verstrekt een voorbeeld om de configuratie van het productiesysteem te wijzigen. U kunt desgewenst verschillende configuratieopties kiezen.

In dit voorbeeld gaan we uit van het volgende:

- U gebruikt Git-bronbesturingselement
- Het ontwikkelingssysteem is beschikbaar in een Git-opslagplaats op afstand met de naam `mconfig`
- Uw Git-werkvertakking krijgt de naam `m2.2_deploy`

## Stap 1: Plaats de configuratie in het ontwikkelingssysteem

U kunt als volgt de tijdzone- en gewichtseenheden in uw ontwikkelingssysteem instellen:

1. Meld u aan bij de beheerder.
1. Klik **Slaat** op > Montages > **Configuratie** > Algemeen > **Algemeen**.
1. In de juiste ruit, breid **Opties van de Landinstelling** uit.

   In de volgende afbeelding ziet u een voorbeeld.

   ![ plaats scèneopties in het ontwikkelingssysteem ](../../assets/configuration/split-deploy-set-locale.png)

1. Van de **lijst van de Tijdzone**, klik **GMT+00:00 (UTC)**.
1. Ontruim het **checkbox van de systeemwaarde van het Gebruik** naast het **3&rbrace; gebied van de Eenheid van de Gewicht.**
1. Van de **lijst van de Eenheid van 0&rbrace; Gewicht, klik** kgs **.**
1. Klik **sparen Config**.
1. Maak de cache leeg als daarom wordt gevraagd.

## Stap 2: Werk de gedeelde configuratie bij

Genereer het gedeelde configuratiedossier, `app/etc/config.php`, in uw ontwikkelingssysteem en breng het over gebruikend broncontrole aan uw bouwstijlsysteem zoals die in deze sectie wordt besproken.

{{$include /help/_includes/config-save-config.md}}

## Stap 3: Werk uw bouwstijlsysteem bij en produceer dossiers

Nu u uw veranderingen in de gedeelde configuratie aan broncontrole hebt geëngageerd, kunt u die veranderingen in uw bouwstijlsysteem trekken, code compileren, en statische dossiers produceren. De laatste stap is om die veranderingen in uw productiesysteem te trekken. Dientengevolge, zal de configuratie van uw productiesysteem uw ontwikkelingssysteem aanpassen.

{{$include /help/_includes/config-update-build-system.md}}

## Stap 4: Productiesysteem bijwerken

De laatste stap in het proces is uw productiesysteem van broncontrole bij te werken. Dit trekt alle veranderingen aan u op uw ontwikkeling en bouwsystemen aanbracht, wat uw productiesysteem volledig bijgewerkt betekent.

{{$include /help/_includes/config-update-prod-system.md}}

### Wijzigingen in Admin controleren

**om deze montages te verifiëren zijn niet editable in Admin**:

1. Meld u aan bij de beheerder.
1. Klik **Slaat** op > Montages > **Configuratie** > Algemeen > **Algemeen**.
1. In de juiste ruit, breid **Opties van de Landinstelling** uit.

   De opties die u zojuist hebt ingesteld, worden als volgt weergegeven:

   ![ de opties van de Configuratie niet editable in Admin ](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Als u een instelling wilt wijzigen die is vergrendeld in Beheer, gebruikt u de opdracht [`magento config:set --lock` ](../cli/set-configuration-values.md) .

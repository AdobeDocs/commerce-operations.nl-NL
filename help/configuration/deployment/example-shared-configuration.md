---
title: Voorbeeld met een gedeelde configuratie
description: Zie een voorbeeld van hoe te om montages in een ontwikkelingssysteem met een gedeeld configuratiedossier te veranderen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Voorbeeld met een gedeelde configuratie

In dit voorbeeld wordt getoond hoe u de volgende instellingen in uw ontwikkelingssysteem kunt wijzigen en het gedeelde configuratiebestand kunt bijwerken. `config.php`, in uw bouwstijlsysteem, en voer de zelfde montages in uw productiesysteem uit:

- Tijdzone
- Gewichtseenheid

Deze instellingen zijn beschikbaar in de beheerfunctie **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**.

U kunt de zelfde procedure gebruiken om het even welke niet gevoelige, niet systeem-specifieke montages in de volgende verwijzingen te vormen:

- [Verwijzing naar andere configuratiepaden](../reference/config-reference-general.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Bron voor configuratiepaden van de extensie Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Voordat u begint

Voordat u begint, stelt u de machtigingen en het eigendom van het bestandssysteem in zoals beschreven in [Vereisten voor ontwikkeling, bouw, en productiesystemen](../deployment/prerequisites.md).

## Aannames

Dit onderwerp verstrekt een voorbeeld om de configuratie van het productiesysteem te wijzigen. U kunt desgewenst verschillende configuratieopties kiezen.

In dit voorbeeld gaan we ervan uit dat:

- U gebruikt Git-bronbesturingselement
- Het ontwikkelingssysteem is beschikbaar in een Git-opslagplaats op afstand met de naam `mconfig`
- Uw Git-werkvertakking krijgt de naam `m2.2_deploy`

## Stap 1: De configuratie instellen in het ontwikkelingssysteem

U kunt als volgt de tijdzone- en gewichtseenheden in uw ontwikkelingssysteem instellen:

1. Meld u aan bij de beheerder.
1. Klikken **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**.
1. Vouw in het rechterdeelvenster uit **Landinstellingen**.

   In de volgende afbeelding ziet u een voorbeeld.

   ![Opties voor landinstellingen instellen in het ontwikkelingssysteem](../../assets/configuration/split-deploy-set-locale.png)

1. Van de **Tijdzone** lijst, klikt u op **GMT+00:00 (UTC)**.
1. Wis de **Systeemwaarde gebruiken** selectievakje naast **Gewichtseenheid** veld.
1. Van de **Gewichtseenheid** lijst, klikt u op **kgs**.
1. Klikken **Config opslaan**.
1. Maak desgevraagd de cache leeg.

## Stap 2: De gedeelde configuratie bijwerken

Genereer het gedeelde configuratiebestand, `app/etc/config.php`, in uw ontwikkelingssysteem en breng het over gebruikend broncontrole aan uw bouwstijlsysteem zoals die in deze sectie wordt besproken.

{{$include /help/_includes/config-save-config.md}}

## Stap 3: Uw constructiesysteem bijwerken en bestanden genereren

Nu u uw veranderingen in de gedeelde configuratie aan broncontrole hebt geëngageerd, kunt u die veranderingen in uw bouwstijlsysteem trekken, code compileren, en statische dossiers produceren. De laatste stap is om die veranderingen in uw productiesysteem te trekken. Dientengevolge, zal de configuratie van uw productiesysteem uw ontwikkelingssysteem aanpassen.

{{$include /help/_includes/config-update-build-system.md}}

## Stap 4: Productiesysteem bijwerken

De laatste stap in het proces is uw productiesysteem van broncontrole bij te werken. Dit trekt alle veranderingen aan u op uw ontwikkeling en bouwsystemen aanbracht, wat uw productiesysteem volledig bijgewerkt betekent.

{{$include /help/_includes/config-update-prod-system.md}}

### Wijzigingen in Admin controleren

**Om te controleren of deze instellingen niet kunnen worden bewerkt in de beheerdersfunctie**:

1. Meld u aan bij de beheerder.
1. Klikken **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**.
1. Vouw in het rechterdeelvenster uit **Landinstellingen**.

   De opties die u zojuist hebt ingesteld, worden als volgt weergegeven:

   ![Configuration options not editable in the Admin](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Als u een instelling wilt wijzigen die is vergrendeld in de beheerfunctie, gebruikt u de opdracht [`magento config:set --lock` command](../cli/set-configuration-values.md).
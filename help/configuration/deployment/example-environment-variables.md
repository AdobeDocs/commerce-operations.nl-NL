---
title: Voorbeeld met omgevingsvariabelen
description: Zie een voorbeeld van hoe te om gedeelde, systeem-specifieke, en gevoelige waarden in uw ontwikkelingssysteem te plaatsen gebruikend omgevingsvariabelen.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---

# Voorbeeld met omgevingsvariabelen

In dit voorbeeld wordt getoond hoe u gedeelde, systeemspecifieke en gevoelige waarden in uw ontwikkelingssysteem instelt en vervolgens alle waarden in uw productiesysteem instelt met een combinatie van de gedeelde configuratie. `config.php`en PHP omgevingsvariabelen.

Deze configuratie-instellingen kunnen worden gedeeld tussen de ontwikkelings- en productiesystemen:

BTW-nummer en winkelnaam van **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**

Deze configuratie-instellingen zijn systeemspecifiek of gevoelig, zoals aangegeven:

- E-mails verzenden naar (gevoelig) van **Winkels** > Instellingen > **Configuratie** > Algemeen > **Contactpersonen**
- Standaard e-maildomein (systeemspecifiek) van **Winkels** > Instellingen > **Configuratie** > Klanten > **Klantconfiguratie** > **Nieuwe accountopties maken**

U kunt de zelfde procedure gebruiken om het even welke montages in de volgende verwijzingen te vormen:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar algemene configuratiepaden](../reference/config-reference-general.md)
- [Bron voor configuratiepaden van de extensie Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Voordat u begint

Voordat u begint, stelt u de machtigingen en het eigendom van het bestandssysteem in zoals beschreven in [Vereiste voor ontwikkeling, bouw, en productiesystemen](../deployment/prerequisites.md).

## Aannames

Dit onderwerp verstrekt een voorbeeld om de configuratie van het productiesysteem te wijzigen. U kunt desgewenst verschillende configuratieopties kiezen.

In dit voorbeeld gaan we ervan uit dat:

- U gebruikt Git-bronbesturingselement
- Het ontwikkelingssysteem is beschikbaar in een Git-opslagplaats op afstand met de naam `mconfig`
- Uw Git-werkvertakking krijgt de naam `m2.2_deploy`

## Stap 1: De configuratie instellen in het ontwikkelingssysteem

U kunt als volgt de standaardwaarden voor landinstelling en gewicht in uw ontwikkelingssysteem instellen:

1. Meld u aan bij de beheerder.
1. Klikken **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**.
1. Als u meer dan één website beschikbaar hebt, gebruikt u **Winkelweergave** in de linkerbovenhoek om naar een andere website te schakelen zoals in de volgende afbeelding wordt getoond.

   ![Andere websites](../../assets/configuration/split-deploy-switch-website.png)

1. Vouw in het rechterdeelvenster uit **Opslaggegevens**.
1. Indien nodig de **Standaardinstellingen gebruiken** selectievakje naast **BTW-nummer** veld.
1. Voer een getal in het veld in (bijvoorbeeld `12345`).
1. In de **Winkelnaam** veld, geef een waarde op (zoals `My Store`).
1. Klikken **Config opslaan**.
1. Gebruik de **Winkelweergave** te selecteren **Standaardconfiguratie** zoals het volgende cijfer toont.

   ![Overschakelen naar de standaardconfiguratie](../../assets/configuration/split-deploy-default-config.png)

1. Klik in de linkernavigatie onder Algemeen op **Contactpersonen**.
1. Wis de **Standaardinstellingen gebruiken** selectievakje naast **E-mails verzenden naar** veld.
1. Voer een e-mailadres in het veld in.
1. Klikken **Config opslaan**.
1. Klik in het linkerdeelvenster op Klanten > **Klantconfiguratie**.
1. Vouw in het rechterdeelvenster uit **Nieuwe accountopties maken**.
1. Wis de **Systeemwaarde gebruiken** selectievakje naast **Standaard-e-maildomein** veld.
1. Voer een domeinnaam in het veld in.
1. Klikken **Config opslaan**.
1. Maak desgevraagd de cache leeg.

## Stap 2: De configuratie bijwerken

Nu u de configuratie in Admin hebt veranderd, schrijf de gedeelde configuratie aan een dossier zoals die in deze sectie wordt besproken.

{{$include /help/_includes/config-save-config.md}}

Houd er rekening mee dat `app/etc/env.php` (de systeem-specifieke configuratie) werd bijgewerkt, controleer het niet aan broncontrole. U zult de zelfde configuratiemontages op uw productiesysteem later in deze procedure tot stand brengen.

## Stap 3: Uw constructiesysteem bijwerken en bestanden genereren

Nu u uw veranderingen in de gedeelde configuratie aan broncontrole hebt geëngageerd, kunt u die veranderingen in uw bouwstijlsysteem trekken, code compileren, en statische dossiers produceren. De laatste stap is om die veranderingen in uw productiesysteem te trekken.

{{$include /help/_includes/config-update-build-system.md}}

## Stap 4: Productiesysteem bijwerken

De laatste stap in het proces is het bijwerken van uw productiesysteem. U moet het in twee delen doen:

- De gevoelige en systeemspecifieke instellingen bijwerken
- De gedeelde instellingen bijwerken

### De gevoelige en systeemspecifieke instellingen bijwerken

Als u de gevoelige en systeemspecifieke instellingen wilt instellen met omgevingsvariabelen, moet u het volgende weten:

- Bereik voor elke instelling

   Als u de instructies in Stap 1 volgde, is het werkingsgebied voor het verzenden van e-mails naar globaal (namelijk het werkingsgebied Standaard Config) en het werkingsgebied voor Standaard e-maildomein is website.

   U moet de code van de website kennen om de configuratiewaarde van het StandaardE-maildomein te plaatsen. Zie [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](../reference/override-config-settings.md#environment-variables) voor meer informatie over het vinden ervan .

- Configuratiepad voor elke instelling

   De configuratiepaden die in dit voorbeeld worden gebruikt, zijn als volgt:

   | Naam instellen | Configuratiepad |
   |--------------|--------------|
   | E-mails verzenden naar | `contact/email/recipient_email` |
   | Standaard-e-maildomein | `customer/create_account/email_domain` |

   U kunt alle gevoelige en systeemspecifieke configuratiewegen in vinden [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md).

#### Configuratiepaden omzetten in variabelenamen

Zoals besproken in [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](../reference/override-config-settings.md#environment-variables)De indeling van de variabelen is:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

De waarde van `<SCOPE>` is `CONFIG__DEFAULT__` voor een mondiaal bereik of `CONFIG__WEBSITES__<WEBSITE CODE>` voor websitebereik.

De waarde van `<SYSTEM__VARIABLE__NAME>`, vervangt elke `/` in het configuratiepad met twee onderstrepingstekens.

De variabelenamen zijn als volgt:

| Naam | Config-pad | Naam variabele |
|--------------|--------------|--------------|
| E-mails verzenden naar | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Standaard-e-maildomein | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>De voorgaande tabel bevat een voorbeeldcode voor de website. `BASE`, voor de configuratie-instelling Standaard-e-maildomein. Vervangen `BASE` met de juiste websitecode voor uw winkel.

#### Variabelen instellen met omgevingsvariabelen

U kunt de variabelewaarden instellen in het dialoogvenster `index.php` in de volgende notatie:

```php
$_ENV['VARIABLE'] = 'value';
```

**Variabelewaarden instellen**:

1. Meld u aan bij uw productiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Openen `<Commerce root dir>/pub/index.php` in een teksteditor.
1. Overal in `index.php`stelt u waarden in voor de volgende variabelen:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Sla uw wijzigingen op in `pub/index.php` en sluit de teksteditor af.
1. Ga verder met de volgende sectie.

### De gedeelde instellingen bijwerken

In deze sectie wordt besproken hoe u alle wijzigingen die u hebt aangebracht in uw ontwikkelings- en buildsystemen kunt doorvoeren. Hiermee worden de gedeelde configuratie-instellingen (Winkelnaam en BTW-nummer) bijgewerkt.

{{$include /help/_includes/config-update-prod-system.md}}

### Configuratie-instellingen controleren in de beheerder

Deze sectie bespreekt hoe u de configuratiemontages in uw Admin van het productiesysteem kunt verifiëren.

**Om de configuratiemontages te verifiëren**:

1. Meld u aan bij de beheerder van het productiesysteem.
1. Klikken **Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen**.
1. Gebruik de **Winkelweergave** in de linkerbovenhoek om naar een andere website te schakelen.

   De gedeelde configuratieopties die u in het ontwikkelingssysteem instelt, worden als volgt weergegeven.

   ![Instellingen controleren in het productiesysteem](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >De **Winkelnaam** Het veld kan worden bewerkt in het bereik van de website, maar als u overschakelt naar het bereik Standaard configuratie, kan het niet worden bewerkt. Dit is het resultaat van hoe u de opties in het ontwikkelingssysteem plaatst. De waarde van **BTW-nummer** kan niet worden bewerkt in het bereik van de website.

1. Als u dit nog niet hebt gedaan, schakelaar aan het werkingsgebied Standaard Config.
1. Klik in de linkernavigatie onder Algemeen op **Contactpersonen**.

   De **E-mails verzenden naar** kan niet worden bewerkt, zoals in de volgende afbeelding wordt getoond. Dit is een gevoelige instelling.

   ![Instellingen controleren in het productiesysteem](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klik in het linkerdeelvenster op Klanten > **Klantconfiguratie**.
1. Vouw in het rechterdeelvenster uit **Nieuwe accountopties maken**.

   De waarde van de **Standaard-e-maildomein** wordt als volgt weergegeven. Dit is een systeemspecifieke instelling.

   ![Instellingen controleren in het productiesysteem](../../assets/configuration/split-default-domain.png)

---
title: Voorbeeld met omgevingsvariabelen
description: Zie een voorbeeld van hoe te om gedeelde, systeem-specifieke, en gevoelige waarden in uw ontwikkelingssysteem te plaatsen gebruikend omgevingsvariabelen.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Voorbeeld met omgevingsvariabelen

In dit voorbeeld wordt getoond hoe u gedeelde, systeemspecifieke en gevoelige waarden in uw ontwikkelingssysteem instelt en vervolgens alle waarden in uw productiesysteem instelt met behulp van een combinatie van de gedeelde configuratie, `config.php` en PHP-omgevingsvariabelen.

Deze configuratie-instellingen kunnen worden gedeeld tussen de ontwikkelings- en productiesystemen:

Het Aantal van BTW en de Naam van de Opslag van **Slaat** > Montages > **Configuratie** > Algemeen > **Algemeen**

Deze configuratie-instellingen zijn systeemspecifiek of gevoelig, zoals aangegeven:

- Verzend E-mail naar (gevoelig) van **Sporen** > Montages > **Configuratie** > Algemeen > **Contacten**
- Het standaard E-maildomein (systeem-specifiek) van **Slaat** > Montages > **Configuratie** > Klanten > **Configuratie van de Klant** > **creeer Nieuwe Opties van de Rekening**

U kunt de zelfde procedure gebruiken om het even welke montages in de volgende verwijzingen te vormen:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar algemene configuratiepaden](../reference/config-reference-general.md)
- [Referentie voor configuratiepaden voor Commerce Enterprise B2B-extensies](../reference/config-reference-b2b.md)

## Voordat u begint

Alvorens u begint, de toestemmingen en de eigendom van het opstellingssysteem zoals besproken in [ Vereiste voor ontwikkeling, bouwt, en productiesystemen ](../deployment/prerequisites.md).

## Veronderstellingen

Dit onderwerp verstrekt een voorbeeld om de configuratie van het productiesysteem te wijzigen. U kunt desgewenst verschillende configuratieopties kiezen.

In dit voorbeeld gaan we uit van het volgende:

- U gebruikt Git-bronbesturingselement
- Het ontwikkelingssysteem is beschikbaar in een Git-opslagplaats op afstand met de naam `mconfig`
- Uw Git-werkvertakking krijgt de naam `m2.2_deploy`

## Stap 1: Plaats de configuratie in het ontwikkelingssysteem

U kunt als volgt de standaardwaarden voor landinstelling en gewicht in uw ontwikkelingssysteem instellen:

1. Meld u aan bij de beheerder.
1. Klik **Slaat** op > Montages > **Configuratie** > Algemeen > **Algemeen**.
1. Als u meer dan één beschikbare website hebt, gebruik de **lijst van de Mening van de Opslag** in de hogere linkerhoek om naar een verschillende website te schakelen aangezien het volgende cijfer toont.

   ![ de websites van de Schakelaar ](../../assets/configuration/split-deploy-switch-website.png)

1. In de juiste ruit, breid **Informatie van de Opslag** uit.
1. Indien nodig, ontruim het **Gebrek van het Gebruik** checkbox naast het **&#x200B;**&#x200B;gebied van het Aantal van BTW.
1. Voer een getal in het veld in (bijvoorbeeld `12345` ).
1. Op het **gebied van de Naam van de Opslag**, ga een waarde (als `My Store`) in.
1. Klik **sparen Config**.
1. Gebruik de **lijst van de Mening van de Opslag** om **StandaardConfig** te selecteren aangezien het volgende cijfer toont.

   ![ Schakelaar aan het gebrek config ](../../assets/configuration/split-deploy-default-config.png)

1. In de linkernavigatie, onder Algemeen, klik **Contacten**.
1. Ontruim het **Standaardvakje van het Gebruik** naast **verzendt E-mail naar** gebied.
1. Voer een e-mailadres in het veld in.
1. Klik **sparen Config**.
1. In de linkerruit, klik Klanten > **Configuratie van de Klant**.
1. In de juiste ruit, breid **uit tot Nieuwe Opties van de Rekening**.
1. Wis het **checkbox van de systeemwaarde van het Gebruik** naast het **Standaard e-mailgebied** gebied.
1. Voer een domeinnaam in het veld in.
1. Klik **sparen Config**.
1. Maak de cache leeg als daarom wordt gevraagd.

## Stap 2: Werk de configuratie bij

Nu u de configuratie in Admin hebt veranderd, schrijf de gedeelde configuratie aan een dossier zoals die in deze sectie wordt besproken.

{{$include /help/_includes/config-save-config.md}}

Merk op dat alhoewel `app/etc/env.php` (de systeem-specifieke configuratie) werd bijgewerkt, het niet aan broncontrole controleert. U zult de zelfde configuratiemontages op uw productiesysteem later in deze procedure tot stand brengen.

## Stap 3: Werk uw bouwstijlsysteem bij en produceer dossiers

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

  U moet de code van de website kennen om de configuratiewaarde van het StandaardE-maildomein te plaatsen. Zie [ het omgevingsvariabelen van het Gebruik om configuratiemontages ](../reference/override-config-settings.md#environment-variables) voor meer informatie met voeten te treden bij het vinden van het.

- Configuratiepad voor elke instelling

  De configuratiepaden in dit voorbeeld zijn als volgt:

  | Naam instellen | Configuratiepad |
  |--------------|--------------|
  | E-mails verzenden naar | `contact/email/recipient_email` |
  | Standaard-e-maildomein | `customer/create_account/email_domain` |

  U kunt alle gevoelige en systeem-specifieke configuratiewegen in [ Gevoelige en systeem-specifieke verwijzing van configuratiepaden ](../reference/config-reference-sens.md) vinden.

#### Configuratiepaden omzetten in variabelenamen

Zoals besproken in [ het omgevingsvariabelen van het Gebruik om configuratiemontages ](../reference/override-config-settings.md#environment-variables) met voeten te treden, is het formaat van variabelen:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

De waarde van `<SCOPE>` is `CONFIG__DEFAULT__` voor algemeen bereik of `CONFIG__WEBSITES__<WEBSITE CODE>` voor websitebereik.

Als u de waarde van `<SYSTEM__VARIABLE__NAME>` wilt zoeken, vervangt u elk `/` -teken in het configuratiepad door twee onderstrepingstekens.

De variabelenamen zijn als volgt:

| Naam | Config-pad | Naam variabele |
|--------------|--------------|--------------|
| E-mails verzenden naar | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Standaard-e-maildomein | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>De voorgaande tabel heeft een voorbeeldwebsitecode, `BASE` , voor de configuratie-instelling Standaard-e-maildomein. Vervang `BASE` door de juiste websitecode voor uw winkel.

#### Variabelen instellen met omgevingsvariabelen

U kunt de waarden van de variabelen in de `index.php` als volgt instellen:

```php
$_ENV['VARIABLE'] = 'value';
```

**om veranderlijke waarden** te plaatsen:

1. Meld u aan bij uw productiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Open `<Commerce root dir>/pub/index.php` in een teksteditor.
1. Stel overal in `index.php` waarden in voor de variabelen die op het volgende lijken:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Sla de wijzigingen in `pub/index.php` op en sluit de teksteditor af.
1. Ga verder met de volgende sectie.

### De gedeelde instellingen bijwerken

In deze sectie wordt besproken hoe u alle wijzigingen die u hebt aangebracht in uw ontwikkelings- en buildsystemen kunt doorvoeren. Hiermee worden de gedeelde configuratie-instellingen (Winkelnaam en BTW-nummer) bijgewerkt.

{{$include /help/_includes/config-update-prod-system.md}}

### Configuratie-instellingen controleren in de beheerder

Deze sectie bespreekt hoe u de configuratiemontages in uw Admin van het productiesysteem kunt verifiëren.

**om de configuratiemontages** te verifiëren:

1. Meld u aan bij de beheerder van het productiesysteem.
1. Klik **Slaat** op > Montages > **Configuratie** > Algemeen > **Algemeen**.
1. Gebruik de **lijst van de Mening van de Opslag** in de hogere linkerhoek om aan een verschillende website over te schakelen.

   De gedeelde configuratieopties die u in het ontwikkelingssysteem instelt, worden als volgt weergegeven.

   ![ de montages van de Controle in het productiesysteem ](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Het **gebied van de Naam van de Opslag** is editable in het websitewerkingsgebied maar als u op het Gebrek Config schakelt, is het niet editable. Dit is het resultaat van hoe u de opties in het ontwikkelingssysteem plaatst. De waarde van **het Aantal van BTW** is niet editable in websitewerkingsgebied.

1. Als u dit nog niet hebt gedaan, schakelaar aan het werkingsgebied Standaard Config.
1. In de linkernavigatie, onder Algemeen, klik **Contacten**.

   **verzendt E-mail naar** gebied is niet editable, aangezien het volgende cijfer toont. Dit is een gevoelige instelling.

   ![ de montages van de Controle in het productiesysteem ](../../assets/configuration/split-deploy-verify-contacts.png)

1. In de linkerruit, klik Klanten > **Configuratie van de Klant**.
1. In de juiste ruit, breid **uit tot Nieuwe Opties van de Rekening**.

   De waarde van het **StandaardE-mailDomein** gebied wordt getoond als volgt. Dit is een systeemspecifieke instelling.

   ![ de montages van de Controle in het productiesysteem ](../../assets/configuration/split-default-domain.png)

<!-- Last updated from includes: 2024-07-18 15:50:54 -->

---
title: Voorbeeld met CLI-opdrachten
description: Zie een voorbeeld van hoe te om gedeelde, systeem-specifieke, en gevoelige waarden in uw ontwikkelingssysteem te plaatsen gebruikend de bevellijn.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Voorbeeld met CLI-opdrachten

Dit voorbeeld toont hoe te om gedeelde, systeem-specifieke, en gevoelige waarden in uw ontwikkelingssysteem te plaatsen, dan die waarden in uw productiesysteem op te stellen.
Dit wordt gedaan door een combinatie gedeelde configuraties, het `config.php` dossier, en het bevel van Commerce CLI te gebruiken.

In dit voorbeeld worden de volgende configuratie-instellingen gebruikt:

- **Vat Aantal** en **Naam van de Opslag** voor de gedeelde configuratiemontages.

  Deze worden gevonden onder **Slaat** > Montages > **Configuratie** > Algemeen > **Algemeen**.

- **verzendt E-mail naar** voor de gevoelige configuratiewaarde.

  Dit wordt gevonden onder **Slaat** > Montages > **Configuratie** > Algemeen > **Contacten**.

- **Standaard E-mailDomein** voor de systeem-specifieke configuratiewaarde.

  Dit wordt gevonden onder **Opslag** > Montages > **Configuratie** > Klanten > **de Configuratie van de Klant** > **creeer Nieuwe Opties van de Rekening**.

U kunt de zelfde procedure gebruiken in dit voorbeeld wordt getoond om het even welke montages in de volgende verwijzingen te vormen die:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar andere configuratiepaden](../reference/config-reference-general.md)
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
1. Indien nodig, ontruim het **Standaardvakje van het Gebruik** naast het **BTW Aantal** en **de gebieden van de Naam van de Opslag**.
1. Voer een getal in het veld in (bijvoorbeeld `12345` ).
1. Op het **gebied van de Naam van de Opslag**, ga een waarde (als `My Store`) in.
1. Klik **sparen Config**.
1. In de linkernavigatie, onder Algemeen, klik **Contacten**.
1. In de juiste ruit, breid **E-mailOpties** uit.
1. Indien nodig, ontruim het **Gebruik Standaard** checkbox naast **verzendt E-mail naar** gebied.
1. Voer een e-mailadres in het veld in.
1. Klik **sparen Config**.
1. Gebruik de **lijst van de Mening van de Opslag** om **StandaardConfig** te selecteren aangezien het volgende cijfer toont.

   ![ Schakelaar aan het gebrek config ](../../assets/configuration/split-deploy-default-config.png)

1. In de linkerruit, klik Klanten > **Configuratie van de Klant**.
1. In de juiste ruit, breid **uit tot Nieuwe Opties van de Rekening**.
1. Indien noodzakelijk, ontruim het **checkbox van de systeemwaarde van het 0&rbrace; Gebruik naast het** Standaard e-mailgebied **gebied.**
1. Voer een domeinnaam in het veld in.
1. Klik **sparen Config**.
1. Maak de cache leeg als daarom wordt gevraagd.

## Stap 2: Werk de configuratie bij

Nu u de configuratie in Admin hebt veranderd, schrijf de gedeelde configuratie aan een dossier zoals gebruikend de volgende stappen:

{{$include /help/_includes/config-save-config.md}}

Hoewel `app/etc/env.php` (de systeem-specifieke configuratie) werd bijgewerkt, controleer het niet aan broncontrole.
U zult de zelfde configuratiemontages op uw productiesysteem later in deze procedure tot stand brengen.

## Stap 3: Werk uw bouwstijlsysteem bij en produceer dossiers

Nu u uw veranderingen in de gedeelde configuratie aan broncontrole hebt geëngageerd, kunt u die veranderingen in uw bouwstijlsysteem trekken, de code compileren, en statische dossiers produceren.

{{$include /help/_includes/config-update-build-system.md}}

## Stap 4: Productiesysteem bijwerken

De laatste stap in het proces is het bijwerken van uw productiesysteem. U moet het in twee delen doen:

- De gevoelige en systeemspecifieke instellingen bijwerken
- De gedeelde instellingen bijwerken

### De gevoelige en systeemspecifieke instellingen bijwerken

Als u de gevoelige en systeemspecifieke instellingen wilt instellen met omgevingsvariabelen, moet u het volgende weten:

- Bereik voor elke instelling

  Als u de instructies in Stap 1 volgde, verzendt het werkingsgebied voor **E-mail naar** website en het werkingsgebied voor **Standaard E-maildomein** is globaal (namelijk het werkingsgebied Standaard Config).

  U hebt de websitecode nodig om **te plaatsen verzendt E-mail naar** configuratiewaarde.

  Voor meer informatie bij het vinden van deze waarde, zie: [ de milieuvariabelen van het Gebruik om configuratiemontages ](../reference/override-config-settings.md#environment-variables) met voeten te treden.

- Configuratiepaden voor de instellingen die in dit voorbeeld worden gebruikt:

  | Naam instellen | Configuratiepad |
  | -------------------- | -------------------------------------- |
  | E-mails verzenden naar | `contact/email/recipient_email` |
  | Standaard-e-maildomein | `customer/create_account/email_domain` |

  Voor alle gevoelige en systeem-specifieke configuratiewegen, zie: [ Gevoelige en systeem-specifieke verwijzing van configuratiepaden ](../reference/config-reference-sens.md).

### De variabelen instellen met CLI-opdrachten

Gebruik de volgende CLI bevelen om systeem-specifieke en gevoelige configuratiemontages te plaatsen:

- `magento config:set` voor systeemspecifieke instellingen
- `magento config:sensitive:set` voor gevoelige instellingen

Om het systeem-specifieke plaatsen **Standaard E-mailDomein** te plaatsen, dat in het standaardwerkingsgebied is, gebruik het volgende bevel:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

U hoeft het bereik niet in de opdracht te gebruiken omdat dit het standaardbereik is.

Om waarden voor **te plaatsen verzendt E-mail naar**, echter, moet u het werkingsgebiedtype (`website`) en de werkingsgebiedcode kennen, die waarschijnlijk verschillend op elke plaats is.

Voorbeeld:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### De gedeelde instellingen bijwerken

Deze sectie bespreekt hoe te om alle veranderingen te trekken u op uw ontwikkeling aanbracht en systemen aan een productiemilieu bouwt, dat de gedeelde configuratiemontages (de Naam van de Opslag en het Aantal van de BTW) bijwerkt.

{{$include /help/_includes/config-update-prod-system.md}}

### Configuratie-instellingen controleren in de beheerder

Om de configuratiemontages te verifiëren:

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

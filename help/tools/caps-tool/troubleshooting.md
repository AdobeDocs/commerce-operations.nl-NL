---
title: '[!DNL Cloud Automation Patching Service (CAPS)] Handleiding voor probleemoplossing'
description: Los gemeenschappelijke kwesties en foutenmeldingen in  [!DNL Cloud Automation Patching Service (CAPS)] problemen op
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)] gids voor probleemoplossing

Wanneer u [!DNL CAPS] gebruikt voor patchbewerkingen, kunt u foutmeldingen en problemen tegenkomen die een geslaagde patchtoepassing of -herversie kunnen voorkomen. Deze gids verstrekt oplossingen voor de gemeenschappelijkste problemen.

## Snelle stappen voor probleemoplossing

### Als de patchbewerking mislukt

* Controleer de status van de bewerking om te zien welk werkgebied is mislukt
* Foutberichten voor specifieke oorzaken van een fout controleren
* Foutenlogboeken controleren op technische details
* Volg de oplossingen in deze handleiding

### Duur patchbewerkingen

Voor de meeste omgevingen wordt in de volgende tijdlijn beschreven hoe lang het duurt voordat de patchbewerkingen zijn uitgevoerd, maar dit kan langer duren, afhankelijk van de grootte en complexiteit van de omgeving:

* **Voorverwerking:** 2-5 minuten
* **het Patching:** 5-15 minuten
* **na-verwerking:** 10-40 minuten
* **Totaal:** 15-60 minuten

### Een patch annuleren die wordt uitgevoerd

>[!WARNING]
>
>Zodra een flardverrichting begint, zou het moeten worden toegestaan om te voltooien. Het systeem omvat schoonmaakprocedures die in werking stellen zelfs als de verrichtingen ontbreken. Als u het proces onderbreekt, kan de omgeving inconsequent blijven.

## Algemene succesberichten

* **&quot;Baan met succes voltooide&quot;** - het flard werd met succes toegepast/met andere problemen teruggekomen.

* **&quot;Reparatie is toegepast&quot;** - u probeert om een flard toe te passen die reeds is toegepast. Het systeem heeft gedetecteerd dat de patch al aanwezig is in uw omgeving. Er is geen actie nodig.

* **&quot;Reparatie is teruggekeerd&quot;** - u probeert om een flard terug te keren die reeds is teruggekeerd. Het systeem heeft gedetecteerd dat de patch momenteel niet wordt toegepast. Er is geen actie nodig.

## Algemene foutmeldingen en oplossingen

### Fouten in patchtoepassing

#### &quot;De patch kan niet worden toegepast omdat [!DNL CAPS] deze problemen heeft gedetecteerd met uw codebase of het patchbestand.&quot;

**wanneer het voorkomt:** tijdens inleidende controle

**Oorzaak:** de flardconflicten met uw huidige codebase OF er is een kwestie met het flard zelf

**Oplossingen:**

* Bekijk de gedetailleerde foutenlogboeken die worden verstrekt om te identificeren of het een codebase of flardkwestie is
* Controleren op conflicterende aanpassingen in uw code
* Controleren of de patch compatibel is met uw Adobe Commerce-versie
* Overweeg conflicten handmatig op te lossen of neem contact op met de ondersteuningsafdeling

#### &quot;Deze patch is niet beheerd door [!DNL CAPS]. Kan niet terugkeren&quot;

**wanneer het voorkomt:** tijdens keert verrichtingen terug

**Oorzaak:** u probeert om een flard terug te keren die niet door [!DNL CAPS] werd toegepast

**Oplossing:** gebruik de zelfde methode die werd gebruikt om het flard oorspronkelijk toe te passen, of contactsteun voor handbijstand

### Omgeving en validatiefouten

#### &quot;De omgeving is niet synchroon met het bovenliggende element&quot;

**wanneer het voorkomt:** tijdens bevestiging

**Oorzaak:** Uw integratiemilieu verschilt van het oudermilieu

**Oplossingen:**

* De omgeving synchroniseren met de bovenliggende vertakking
* De patchbewerking opnieuw uitvoeren
* Neem contact op met de ondersteuningsafdeling als synchronisatiekwesties aanhouden

#### &quot;Niet-naleving van de productiemilieu&quot;

**wanneer het voorkomt:** Tijdens inleidende controle voor productiemilieu&#39;s

**Oorzaak:** het productiemilieu voldoet niet aan de vereiste veiligheidsvoorwaarden

**Oplossingen:**

* Onderhoudsmodus inschakelen voor uw productiearchief
* Snijtaken in uw productieomgeving uitschakelen
* Verifieer beide voorwaarden alvorens opnieuw te proberen

>[!IMPORTANT]
>
> In [!DNL CAPS] wordt de onderhoudsmodus niet automatisch ingeschakeld en worden de taken voor uitsnijden niet uitgeschakeld. Dit moet u extern doen

#### &quot;Reparatie is toegepast, maar de health check is mislukt. Overweeg om terug te keren&quot;

**wanneer het voorkomt:** na flardtoepassing tijdens bevestiging

**Oorzaak:** het flard werd toegepast met succes, maar de ontbroken gezondheidscontroles

**Oplossingen:**

* Toepassingslogboeken controleren op specifieke fouten
* Kritieke functionaliteit handmatig testen
* Overweeg de pleister om te keren als de problemen aanhouden
* Neem contact op met de ondersteuningsafdeling als u hulp nodig hebt

### Verificatie- en toegangsfouten

#### &quot;Verificatie mislukt voor Adobe Commerce-opslagplaats&quot;

**wanneer het voorkomt:** tijdens om het even welk stadium

**Oorzaak:** Ongeldige of verlopen de geloofsbrieven van de bewaarplaats van Adobe Commerce

**Oplossingen:**

Er zijn twee aanbevolen opties voor het oplossen van dit probleem:

**Optie 1: Repareer `env:COMPOSER_AUTH` (Geadviseerde) variabele van het milieuniveau**

* Controleer of u de juiste referenties voor `env:COMPOSER_AUTH` hebt ingesteld.
* De toegang globale configuratie door op het tandwielpictogram bij de hoogste linkerzijde van uw wolkenproject UI te klikken, dan selecteren de **Variabelen** tabel.
* Zorg ervoor u _Beschikbaar tijdens buildtime_ selecteert en _Beschikbaar tijdens runtime_ schrapt.

Als Optie 1 uw probleem niet oplost, ga met Optie 2 te werk.

**Optie 2: Creeer en stel `auth.json` dossier manueel** op

* SSH in uw server.
* De inhoud van de huidige `env:COMPOSER_AUTH` variabele ophalen met:\
  `echo $COMPOSER_AUTH`
* Kopieer alle inhoud uit bovenstaande stap (in JSON-indeling).
* Maak een nieuw bestand met de naam `auth.json` met deze inhoud.
* Leg dit nieuwe `auth.json` -bestand vast in de hoofdmap van uw opslagplaats.
* Trigger een nieuwe plaatsing.

#### &quot;Onvoldoende rechten voor toegang tot omgeving&quot;

**wanneer het voorkomt:** tijdens omgevingsverwezenlijking of toegang

**Oorzaak:** Uw gebruikersrekening mist noodzakelijke toestemmingen

**Oplossingen:**

* Gebruikersrol en machtigingen controleren
* Neem contact op met de systeembeheerder
* Controleren of u beschikt over machtigingen voor omgevingsbeheer
* Ervoor zorgen dat u beschikt over implementatiemachtigingen

### Bron- en quotafouten

#### &quot;Milieuquotum overschreden&quot;

**wanneer het voorkomt:** tijdens milieu verwezenlijking

**Oorzaak:** u hebt uw milieugrens bereikt

**Oplossingen:**

* Ongebruikte omgevingen deactiveren
* Oude vertakkingen en implementaties opschonen
* Contact opnemen met ondersteuning om quotaverhoging aan te vragen
* Overweeg een upgrade van uw abonnement uit te voeren

#### &quot;Onvoldoende bedrijfsmiddelen&quot;

**wanneer het voorkomt:** tijdens om het even welk stadium

**Oorzaak:** Uw milieu mist voldoende CPU, geheugen, of opslag

**Oplossingen:**

* Gebruik van omgevingsbronnen controleren
* Bronnen vrijmaken door bestanden op te schonen
* Wacht tot bronnen beschikbaar zijn
* Contact opnemen met de ondersteuning als de bronproblemen zich blijven voordoen

## Hulp krijgen

**wanneer om steun te contacteren:**

Neem contact op met de ondersteuning van Adobe Commerce Cloud als:

* Foutberichten zijn onduidelijk of onvoldoende gedetailleerd
* Patchbewerkingen mislukken
* U hebt hulp nodig bij het handmatig oplossen van conflicten
* Gezondheidscontroles mislukken, maar de oorzaak is niet duidelijk
* U hebt hulp nodig bij problemen met omgevingssynchronisatie

**te verstrekken Informatie:**

Geef bij contact met de ondersteuningsafdeling het volgende op:

* **identiteitskaart van het Project** - Uw het projectherkenningsteken van de Wolk van de Handel van Adobe
* **identiteitskaart van het Milieu** - het specifieke milieu waar de kwestie voorkwam
* **identiteitskaart van de Verrichting** - het [!DNL CAPS] verrichtings herkenningsteken
* **de details van de Fout** - Volledige foutenmeldingen en logboeken
* **Stappen om** te reproduceren - wat u deed toen de fout voorkwam
* **Vorige pogingen** - wat u reeds hebt geprobeerd om de kwestie op te lossen

### Aanvullende bronnen

Voor meer gedetailleerde technische informatie:

* Controleer de volledige foutlogboeken die bij mislukte bewerkingen zijn geleverd
* Raadpleeg de Adobe Commerce-documentatie voor patchspecifieke richtlijnen
* Neem contact op met de ondersteuning van Adobe Commerce Cloud voor specifieke problemen op milieugebied

### Verwante onderwerpen

* [&#x200B; documentatie van de Wolk van de Handel van Adobe &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview.html)
* [&#x200B; de Gids van de Installatie van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview.html)
* [CAPS-introductie](intro.md)
* [Toegang krijgen](access.md)
* [Workflow](workflow.md)
* [Aanbevolen procedures](best-practices.md)

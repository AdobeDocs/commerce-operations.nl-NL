---
title: Security.txt
description: Leer hoe u informatie verstrekt om beveiligingsonderzoekers te helpen kwetsbaarheden te melden.
feature: Configuration, Security
badge: label="Medewerkers van Kalpesh Mehta van Corra" type="Informatief" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Beveiligingstxtbestand

Wanneer door onderzoekers beveiligingskwetsbaarheden worden ontdekt, ontbreekt het vaak aan goede rapporteringskanalen. Hierdoor worden enkele kwetsbaarheden niet gemeld. Het doel van de `security.txt` [bestandsindeling](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) het dossier moet veiligheidsonderzoekers de informatie verstrekken die zij kunnen gebruiken om hun bevindingen te melden.

Handelaren kunnen hun contactgegevens invoeren voor [rapportage van beveiligingsproblemen](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) van de Commerce _Beheer_. Voor ontwikkelaars geldt het `Magento_Securitytxt` biedt de volgende functionaliteit:

- Staat veiligheidsconfiguraties toe om van te bewaren _Beheer_.
- Bevat een router om toepassingsactieklasse voor verzoeken aan te passen `.well-known/security.txt` en `.well-known/security.txt.sig` bestanden.
- Dient de inhoud van `.well-known/security.txt` en `.well-known/security.txt.sig` bestanden.

Een geldige `security.txt` Het bestand kan er als volgt uitzien:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Als u de opdracht `security.txt` handtekening (`security.txt.sig`) bestand:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

De handtekening verifiëren:

```bash
gpg --verify security.txt.sig security.txt
```

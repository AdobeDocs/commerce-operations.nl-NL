---
title: Security.txt
description: Leer hoe u informatie verstrekt om beveiligingsonderzoekers te helpen kwetsbaarheden te melden.
feature: Configuration, Security
badge: label="Bijdrage van Kalpesh Mehta van Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Beveiligingstxtbestand

Wanneer door onderzoekers beveiligingskwetsbaarheden worden ontdekt, ontbreekt het vaak aan goede rapporteringskanalen. Hierdoor worden enkele kwetsbaarheden niet gemeld. Het doel van het `security.txt` [ dossier - formaat ](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) dossier moet veiligheidsonderzoekers de informatie verstrekken die zij kunnen gebruiken om hun bevindingen te melden.

De handelaren kunnen hun contactinformatie voor [ veiligheidskwestie ingaan die ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-issue-reporting) van Commerce _meldt Admin_. Voor ontwikkelaars biedt de module `Magento_Securitytxt` de volgende functionaliteit:

- Staat veiligheidsconfiguraties toe om van _worden bewaard Admin_.
- Bevat een router om toepassingsactieklasse voor verzoeken aan `.well-known/security.txt` en `.well-known/security.txt.sig` dossiers aan te passen.
- De inhoud van de bestanden `.well-known/security.txt` en `.well-known/security.txt.sig` .

Een geldig `security.txt` bestand kan er als volgt uitzien:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Het `security.txt` handtekeningbestand (`security.txt.sig` ) maken:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Om de handtekening te verifiëren:

```bash
gpg --verify security.txt.sig security.txt
```

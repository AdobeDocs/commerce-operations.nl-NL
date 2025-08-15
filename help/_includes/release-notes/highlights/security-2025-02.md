---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# februari 2025 hooglichten beveiligingspatch

Deze release bevat de volgende hooglichten:

* **het Leiden encryptiesleutels en re-encrypting gegevens** - opnieuw ontworpen het beheren van encryptiesleutels om bruikbaarheid te verbeteren en vorige beperkingen en insecten te elimineren.<!-- AC-12679 -->

  De nieuwe bevelen CLI zijn nu beschikbaar voor [ veranderende ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/encryption-key) sleutels en [ re-encrypting ](https://developer.adobe.com/commerce/php/development/security/data-encryption/) bepaalde systeemconfiguratie, betaling, en gegevens van het douanegebied. Het wijzigen van toetsen in de interface van Admin wordt niet meer ondersteund in deze release. U moet de bevelen CLI gebruiken.

* **Reparatie voor [ CVE-2025-24434 ](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** - lost een vergunningskwetsbaarheid op.

  Deze oplossing is ook beschikbaar als een geïsoleerde pleister. Zie het [ artikel van de Kennisbank ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) voor details.<!-- AC-12755 -->

* **de versiedaling van TinyMCE** - het gebiedsdeel TinyMCE is gedowngraded van versie 7 tot 6.8.5 om verlenen van vergunningen compatibiliteitskwesties te behandelen.

  Deze wijziging zorgt voor voortdurende naleving, terwijl Adobe een alternatieve open source WYSIWYG-editor evalueert.

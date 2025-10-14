---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Augustus 2024 de hoogtepunten van de veiligheidspatch

Deze release bevat de volgende hooglichten:

* **snelheidsbeperking voor[!DNL one-time passwords]** - De volgende nieuwe opties van de systeemconfiguratie zijn nu beschikbaar om tarief toe te laten beperkt op [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] bevestiging:

   * [!UICONTROL **probeert opnieuw pooggrens voor two-Factor Authentificatie**]
   * [!UICONTROL **two-FactorAuthentificatie lockout tijd (seconden)**]

  Adobe raadt u aan een drempelwaarde voor 2FA OTP-validatie in te stellen om het aantal pogingen tot het beperken van aanvallen met brute krachten te beperken. Zie [&#x200B; Veiligheid > 2FA &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/security/2fa) in de _Gids van de Verwijzing van de Configuratie_ voor meer informatie. <!-- AC-12095 -->

* **de zeer belangrijke omwenteling van de Encryptie** - een nieuw CLI bevel is nu beschikbaar voor het veranderen van uw encryptiesleutel. Zie de [&#x200B; Zeer belangrijke Omwenteling van de Encryptie van het Oplossen van problemen: CVE-2024-34102 &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) artikel van de Kennisbank voor details.

* **Repareren voor [&#x200B; CVE-2020-27511 &#x200B;](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** - lost a [!DNL Prototype.js] veiligheidskwetsbaarheid op.<!-- AC-11936 -->

* **Repareren voor [&#x200B; CVE-2024-39397 &#x200B;](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** - lost een kwetsbaarheid van de de veiligheidsveiligheid van de verre codeuitvoering op. Deze kwetsbaarheid is van invloed op verkopers die de Apache-webserver gebruiken voor onbedrijfsmatige of zelfgehoste implementaties. Deze oplossing is ook beschikbaar als een geïsoleerde pleister. Zie de [&#x200B; update van de Veiligheid beschikbaar voor Adobe Commerce - APSB24-61 &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) artikel van de Kennisbank voor details.<!-- ACSD-60551 -->

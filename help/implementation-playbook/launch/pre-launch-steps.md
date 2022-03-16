---
title: Stappen die vooraf worden gestart
description: Gebruik onze controlelijsten vóór de introductie om een probleemloze implementatie van de Adobe Commerce-site te garanderen.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Stappen vóór de introductie

When you have completed deployment and testing in the staging environments, you can begin site-launch preparation. Staging is een omgeving in de buurt van de productie die wordt uitgevoerd op vergelijkbare hardware, configuraties, architectuur en services. Het kan uw onderbreking verminderen en uw uitbreiding, de dienst, douaneconfiguraties, en bedrijfsmatige gebruikersaanvaarding testende vitale componenten maken om uw plaatsen en opslag vrij te geven.

De checklist vóór de lancering is vereist om voorafgaand aan lanceringsstaat te verifiëren, die de volgende belangrijkste controles omvat:

- Code vastzetten voor implementatie
- Ensure that the downtime was communicated in advance by at least one day for maintenance release and one week for the first launch
- Implementatiescripts worden volledig ingesteld/geconfigureerd voor productie-/staging-/integratieomgevingen
- Databases zijn allemaal opgezet en zijn identiek tussen Staging- en Productieomgevingen
- SSL (TLS) certificates are validated for Staging/Production environments
- Mail services are well-configured and functioning for transactional emails
- CDN is geconfigureerd voor productieomgevingen voor staging/productie
- Beveiligingsscan instellen voor Staging-/Productieomgevingen
   - Adobe Commerce-beveiligingsscan
- Perform performance assessment by
   - JMeter
   - Siege
   - Webpagina testen
   - Google-paginasnelheid
- Alle integratie van derden valideren die in de toepassing zal functioneren (OMS, CRM)
- Gereedschap voor prestatiebewaking inschakelen (nieuwe relais)
- Activiteiten op het gebied van gegevensmigratie tijdens een repetitie (indien van toepassing)

![Diagram van fase 1 van het startproces](../../assets/playbooks/launch-steps-1.svg)

De belangrijkste verschillen tussen Adobe Commerce-implementaties op locatie en in de cloud zijn de implementatiescripts en -gereedschappen en de installatie voor SSL, Mail-service en CDN. However, the process is still the same.

Voor het SSL-certificaat (TLS) biedt Adobe Commerce op de cloudinfrastructuur een snel jokertekencertificaat. Als u het wilt gaan gebruiken, moet u de validatie doorgeven: Voeg de Fastly TXT-record toe aan een ex-domeinnaam binnen uw DNS-instellingen. De Fastly TXT-record kan worden gevonden in de spreadsheet aan boord, anders moet u een ticket indienen om het te verkrijgen. Vervang deze tekst door uw vragen/opmerkingen hier. Als u uw eigen SSL(TLS)-certificaat gebruikt in plaats van een snelvervangingscertificaat, verzendt u een ondersteuningsticket met het certificaat dat u aan de installatie hebt gekoppeld.

Adobe Commerce on cloud Infrastructure biedt de functionaliteit SendGrid Mail voor uw transactie-e-mails. Voor Pro plannen, moet u verslagen SendGrid aan uw DNS montages toevoegen. De verslagen SendGrid kunnen in het aan boord gaan spreadsheet worden gevonden, anders zou SI of de handelaar steunkaartjes moeten voorleggen om hen te verkrijgen. To start, you don&#39;t need to make any changes to your DNS; SendGrid is pre-configured for you.

## Complete pre-launch checklist

De volledige checklist vóór de lancering toont alle belangrijke activiteiten waarvan volledigheid noodzakelijk is om zich aan de lanceringsstaat te bewegen.

- Bijkomende risicobeperkende plannen bijgewerkt
- Correct domain names provided
- Outgoing emails have been tested
- SSL-certificaat is ingericht en geconfigureerd
- All-important configuration of Adobe Commerce application is updated correctly
- Basis-URL&#39;s en Basis-Admin-URL worden op de juiste wijze ingesteld op de uiteindelijke hostnaam
- Beheerderswachtwoorden worden gewijzigd
- All users with access to application that no longer require access are removed
- Payment configuration for production environment (for some, payment is using sandbox mode for testing)
- Test data (customer, wishlist, reviews, orders, and related data) from Production database is cleared

![Diagram van fase 2 van het startproces](../../assets/playbooks/launch-steps-2.svg)

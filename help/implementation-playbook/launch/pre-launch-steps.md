---
title: Stappen die vooraf worden gestart
description: Gebruik onze controlelijsten vóór de introductie om een probleemloze implementatie van de Adobe Commerce-site te garanderen.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Stappen vóór de introductie

Wanneer u de implementatie en het testen in de testomgevingen hebt voltooid, kunt u beginnen met de voorbereiding van de site. Staging is een omgeving in de buurt van de productie die wordt uitgevoerd op vergelijkbare hardware, configuraties, architectuur en services. Het kan uw onderbreking verminderen en uw uitbreiding, de dienst, douaneconfiguraties, en bedrijfsmatige gebruikersaanvaarding testende vitale componenten maken om uw plaatsen en opslag vrij te geven.

De checklist vóór de lancering is vereist om voorafgaand aan lanceringsstaat te verifiëren, die de volgende belangrijkste controles omvat:

- Code vastzetten voor implementatie
- Zorg ervoor dat de uitvaltijd van tevoren werd meegedeeld vóór ten minste één dag voor onderhoudsrelease en één week voor de eerste keer dat de toepassing werd gestart
- Implementatiescripts worden volledig ingesteld/geconfigureerd voor productie-/staging-/integratieomgevingen
- Databases zijn allemaal opgezet en zijn identiek tussen Staging- en Productieomgevingen
- SSL-certificaten (TLS) worden gevalideerd voor testomgevingen/productieomgevingen
- E-mailservices zijn goed geconfigureerd en werken goed voor transactie-e-mails
- CDN is geconfigureerd voor productieomgevingen voor staging/productie
- Beveiligingsscan instellen voor Staging-/Productieomgevingen
   - Adobe Commerce-beveiligingsscan
- Prestatiebeoordeling uitvoeren met
   - JMeter
   - Siege
   - Webpagina testen
   - Google-paginasnelheid
- Alle integratie van derden valideren die in de toepassing zal functioneren (OMS, CRM)
- Gereedschap voor prestatiebewaking inschakelen (nieuwe relais)
- Activiteiten op het gebied van gegevensmigratie tijdens een repetitie (indien van toepassing)

![Diagram van fase 1 van het startproces](../../assets/playbooks/launch-steps-1.svg)

De belangrijkste verschillen tussen Adobe Commerce-implementaties op locatie en in de cloud zijn de implementatiescripts en -gereedschappen en de installatie voor SSL, Mail-service en CDN. Het proces is echter nog steeds hetzelfde.

Voor het SSL-certificaat (TLS) biedt Adobe Commerce op de cloudinfrastructuur een snel jokertekencertificaat. Als u het wilt gaan gebruiken, moet u de validatie doorgeven: Voeg de Fastly TXT-record toe aan een ex-domeinnaam binnen uw DNS-instellingen. De Fastly TXT-record kan worden gevonden in de spreadsheet aan boord, anders moet u een ticket indienen om het te verkrijgen. Vervang deze tekst door uw vragen/opmerkingen hier. Als u uw eigen SSL(TLS)-certificaat gebruikt in plaats van een snelvervangingscertificaat, verzendt u een ondersteuningsticket met het certificaat dat u aan de installatie hebt gekoppeld.

Adobe Commerce on cloud Infrastructure biedt de functionaliteit SendGrid Mail voor uw transactie-e-mails. Voor Pro plannen, moet u verslagen SendGrid aan uw DNS montages toevoegen. De verslagen SendGrid kunnen in het aan boord gaan spreadsheet worden gevonden, anders zou SI of de handelaar steunkaartjes moeten voorleggen om hen te verkrijgen. Om te beginnen, te hoeven u om het even welke veranderingen in uw DNS niet aan te brengen; SendGrid is vooraf geconfigureerd voor u.

## Volledige checklist voor het starten

De volledige checklist vóór de lancering toont alle belangrijke activiteiten waarvan volledigheid noodzakelijk is om zich aan de lanceringsstaat te bewegen.

- Bijkomende risicobeperkende plannen bijgewerkt
- Opgegeven domeinnamen corrigeren
- Uitgaande e-mailberichten zijn getest
- SSL-certificaat is ingericht en geconfigureerd
- De zeer belangrijke configuratie van de toepassing van Adobe Commerce wordt correct bijgewerkt
- Basis-URL&#39;s en Basis-Admin-URL worden op de juiste wijze ingesteld op de uiteindelijke hostnaam
- Beheerderswachtwoorden worden gewijzigd
- Alle gebruikers met toegang tot een toepassing die geen toegang meer nodig heeft, worden verwijderd
- Betalingsconfiguratie voor productieomgeving (voor sommige gebruikers wordt de sandboxmodus gebruikt voor het testen)
- Testgegevens (klant, wenslijst, revisies, orders en verwante gegevens) uit de productiedatabase worden gewist

![Diagram van fase 2 van het startproces](../../assets/playbooks/launch-steps-2.svg)

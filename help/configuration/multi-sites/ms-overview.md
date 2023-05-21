---
title: Meerdere websites of winkels
description: Leer hoe u meerdere websites kunt starten of winkelweergaven kunt implementeren met verschillende opties, domeinen en inhoud.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Meerdere websites of winkels

Met één exemplaar van de Adobe Commerce-software kunt u meerdere websites starten of weergaven opslaan die verschillende kenmerken en inhoud gebruiken, zoals:

- Standaardtalen
- Domeinnamen
- Categorieën
- Producten
- Valuta

Deze flexibele oplossing laat één Koophandel codebase en Admin toe om verschillende opslag te beheren en te tonen. U configureert de websites, winkels en opslagweergaven in de beheerfunctie. Gebruik bepaalde variabelen in virtuele gastheren om de toepassing van de Handel te beginnen gebruikend deze websites of opslagmeningen.

Doorgaans worden winkels met verschillende opties in verschillende domeinen ingesteld. U kunt bijvoorbeeld een set categorieën en producten op een bepaald domein plaatsen en een andere set categorieën en producten op een afzonderlijk domein in een andere taal.

U vormt de websites, de opslag, en de opslagmeningen in Admin van de Handel. Gebruik de `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` variabelen in virtuele gastheren om de toepassing van de Handel te beginnen gebruikend deze websites of opslagmeningen.

Overweeg de volgende termen:

- **Website**—is de container op hoofdniveau voor sites, leveringsmethoden, betalingsmethoden en meer. Als u volledig aparte sites wilt maken die geen winkelwagentje, bezorgmethoden of andere sites delen, moet u afzonderlijke websites maken.

   De de klantenrekeningen van de website kunnen tussen veelvoudige websites binnen één enkele instantie van de Handel worden gedeeld. Een website bevat minstens één winkel. Catalogusprijzen moeten op het niveau van de website worden beheerd.

- **Winkel**—is opgenomen door een website. Een winkel bevat op zijn beurt ten minste één *winkelweergave*.

   Meerdere winkels kunnen winkelwagentjes, gebruikerssessies, betaalgateways en nog veel meer delen, maar ze hebben aparte catalogusstructuren en catalogusprijs.

   De catalogushoeveelheid (voorraad) kan niet op archiefniveau worden beheerd. De inventarisatie wordt alleen op website- of wereldwijd niveau beheerd.

   De mening van de opslag verandert de manier pagina&#39;s worden voorgesteld, en typisch gebruikt om een opslag met verschillende lay-outs of talen te tonen. U kunt verschillende valuta&#39;s per winkelweergave beheren.

   Elke website en elke winkelweergave moet een unieke id hebben. Deze id is vereist voor het gebruik van de `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` variabelen, als hieronder:

- `MAGE_RUN_TYPE` kan `store` of `website`

   - Gebruiken `website` om een website in uw winkel te laden.
   - Gebruiken `store` om een winkelweergave in uw winkel te laden.

- `MAGE_RUN_CODE` is de unieke website- of opslagweergavecode die overeenkomt met `MAGE_RUN_TYPE`

Hieronder volgt een overzicht van de taken die u moet uitvoeren:

1. [Stel websites in, sla weergaven op en sla deze op in de beheerfunctie.](ms-admin.md)
1. Maak een virtuele host om een groot aantal websites of één virtuele host per website van Commerce te laden of stel de weergave van de winkel in om specifieke instructies voor elke winkel toe te staan.
1. Geef de waarden van `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` naar de webserver.

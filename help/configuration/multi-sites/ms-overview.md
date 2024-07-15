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

Met deze flexibele oplossing kunnen één Commerce-codebase en -beheerder verschillende winkels beheren en weergeven. U configureert de websites, winkels en opslagweergaven in de beheerfunctie. Gebruik bepaalde variabelen in virtuele hosts om de Commerce-toepassing te starten met deze websites of om weergaven op te slaan.

Doorgaans worden winkels met verschillende opties in verschillende domeinen ingesteld. U kunt bijvoorbeeld een set categorieën en producten op een bepaald domein plaatsen en een andere set categorieën en producten op een afzonderlijk domein in een andere taal.

U configureert de websites, winkels en opslagweergaven in Commerce Admin. Gebruik de variabelen `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` in virtuele hosts om de Commerce-toepassing te starten met deze websites of om weergaven op te slaan.

Overweeg de volgende termen:

- **Website** - is de top-level container voor plaatsen, leveringsmethodes, betalingsmethodes, en meer. Als u volledig aparte sites wilt maken die geen winkelwagentje, bezorgmethoden of andere sites delen, moet u afzonderlijke websites maken.

  Klantenaccounts van websites kunnen worden gedeeld tussen meerdere websites in één Commerce-exemplaar. Een website bevat minstens één winkel. Catalogusprijzen moeten op het niveau van de website worden beheerd.

- **opslag** - is bevat door een website. beurtelings, bevat een opslag minstens één *opslagmening*.

  Meerdere winkels kunnen winkelwagentjes, gebruikerssessies, betaalgateways en nog veel meer delen, maar ze hebben aparte catalogusstructuren en catalogusprijs.

  De catalogushoeveelheid (voorraad) kan niet op archiefniveau worden beheerd. De inventarisatie wordt alleen op website- of wereldwijd niveau beheerd.

  De mening van de opslag verandert de manier pagina&#39;s worden voorgesteld, en typisch gebruikt om een opslag met verschillende lay-outs of talen te tonen. U kunt verschillende valuta&#39;s per winkelweergave beheren.

  Elke website en elke winkelweergave moet een unieke id hebben. Deze id is vereist om de variabelen `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` als volgt te kunnen gebruiken:

- `MAGE_RUN_TYPE` kan `store` of `website` zijn

   - Gebruik `website` om een website in uw winkel te laden.
   - Gebruik `store` om een winkelweergave in uw winkelvoorkeuren te laden.

- `MAGE_RUN_CODE` is de unieke code van de website- of opslagweergave die overeenkomt met `MAGE_RUN_TYPE`

Hieronder volgt een overzicht van de taken die u moet uitvoeren:

1. [Stel websites in, sla weergaven op en sla deze op in de beheerfunctie.](ms-admin.md)
1. Maak een virtuele host om veel websites of één virtuele host per Commerce-website te laden of stel de weergave van de winkel in om specifieke instructies voor elke winkel toe te staan.
1. Geef de waarden van `MAGE_RUN_TYPE` en `MAGE_RUN_CODE` door aan de webserver.

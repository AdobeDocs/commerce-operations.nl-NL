---
title: MySQL triggergebruik
description: Leer hoe u MySQL-triggers effectief kunt gebruiken met Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Aanbevolen procedures voor gebruik van MySQL-triggers

In dit artikel wordt uitgelegd hoe u prestatieproblemen kunt voorkomen bij het gebruik van MySQL-triggers. De trekkers worden gebruikt om veranderingen in controletabellen te registreren.

## Betrokken producten en versies

- Adobe Commerce ter plaatse
- Adobe Commerce over cloudinfrastructuur

>[!WARNING]
>
>Voor Adobe Commerce op wolkenprojecten, test altijd configuratieveranderingen in het Staging milieu alvorens de configuratie voor het milieu van de Productie te veranderen.

## Prestatieeffecten begrijpen

Triggers worden geïnterpreteerd als code die betekent dat MySQL ze niet vooraf compileert.

Het houden van in de de transactieruimte van de vraag, de trekkers voegen overheadkosten aan een parser en een interpreter voor elke vraag toe die met de lijst wordt uitgevoerd. De trekkers delen de zelfde transactieruimte zoals de originele vragen, en terwijl die vragen voor sloten op de lijst concurreren, concurreren de trekkers onafhankelijk voor sloten op een andere lijst.

Deze extra overhead kan de siteprestaties op de site negatief beïnvloeden als er veel triggers worden gebruikt.

>[!WARNING]
>
>Adobe Commerce ondersteunt geen aangepaste triggers in de Adobe Commerce-database omdat aangepaste triggers incompatibiliteiten met toekomstige Adobe Commerce-versies kunnen introduceren. Voor beste praktijken, zie [Algemene MySQL-richtlijnen](../../../installation/prerequisites/database/mysql.md) in de documentatie van Adobe Commerce.

## Efficiënt triggers gebruiken

Volg deze richtlijnen om prestatieproblemen te voorkomen bij het gebruik van triggers:

- Als u douanetriggers hebt die sommige gegevens schrijven wanneer de trekker wordt uitgevoerd, beweeg deze logica om rechtstreeks aan de controletabellen in plaats daarvan te schrijven. Bijvoorbeeld, door een extra vraag in de toepassingscode toe te voegen, na de vraag u was bedoeld om de trekker voor tot stand te brengen.
- Bekijk bestaande aangepaste triggers en overweeg deze te verwijderen en rechtstreeks vanuit de toepassingszijde naar de tabellen te schrijven. Controleren op bestaande triggers in uw database met de opdracht [`SHOW TRIGGERS` SQL-instructie](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Voor extra hulp, vragen, of zorgen, [een Adobe Commerce-ondersteuningsticket verzenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Aanvullende informatie

- [MySQL-voorwaarden](../../../installation/prerequisites/database/mysql.md)
- [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](database-on-cloud.md)

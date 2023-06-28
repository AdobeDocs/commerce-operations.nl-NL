---
title: Aanbevolen werkwijzen voor productkaarten
description: Leer hoe u de Adobe Commerce-prestaties kunt optimaliseren door het aantal producten in een winkelwagentje te beperken.
role: User
feature: Best Practices, Shopping Cart
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor productcartbeheer

Voor de beste prestaties gebruikt u de volgende richtlijnen voor het beheer van de kartellimieten voor Adobe Commerce en Magento Open Source:

- Voor versies 2.3.x - 2.4.2, sta een maximum van 100 producten in een kar toe.
- Voor versies 2.4.3 en later, verhoogde de verbetering aan verkoopregelmogelijkheden het kartmaximum tot 750.


Voor versies 2.3.x - 2.4.2, zijn de verwachte prestaties gebaseerd op de grenzen van het winkelwagentje de volgende:

- Tot maximaal **100** producten in een kar-het product werkt, die prestatiesdoelstellingen voor reactietijd bereiken.
- Tot maximaal **300** producten in een winkelwagentje - het product werkt, maar de reactietijd neemt toe boven de doelen.
- Boven **500** producten in een winkelwagentje - de winkelwagentjes en de kassa werken niet altijd

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Aantal winkelwagentjes verkleinen

Gebruik de volgende strategieën om het aantal winkelwagentjes te beheren

- Hiermee splitst u ordes in verschillende kleinere bestellingen met een kleiner aantal rijen met behulp van de optie [!UICONTROL Add Item by SKU] gebruiken.
- Voeg alleen de aangepaste logica en aanpassing van het winkelwagentje toe die zijn vereist om een lijst met items te laden.

## Mogelijke gevolgen voor de prestaties

Als u meer dan het aanbevolen maximumaantal producten in de kar hebt, kan dit de prestaties van de site op de volgende manieren beïnvloeden:

- Verhoogde responstijd voor het opvragen van gegevens, validatie van winkelwagentjes, controles voor het toepassen van prijsregels, en belasting en totale berekeningen.
- Verhoogde responstijd voor minicart-rendering, inclusief rendering van cartweergaven, uitcheckflow en uitvoering.
- Verhoogde laadtijd voor alle sitepagina&#39;s waarin het minicart aanwezig is.

## Aanvullende informatie

- [Productopties configureren](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Een winkelwagentje beheren](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)

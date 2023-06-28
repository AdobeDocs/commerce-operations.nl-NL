---
title: Aanbevolen procedures voor het configureren van promoties
description: Leer beste praktijken voor het vormen van verkoopregels en couponcodes om de prestaties van de winkel van de Handel te optimaliseren.
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Aanbevolen procedures voor het configureren van promoties

Voor de beste prestaties, volg deze beste praktijken om verkoop en promoties voor punten in een winkelwagentje te vormen:

- **Verkoopregels (regels betreffende de kartprijs)**-Configureer niet meer dan 1000 regels voor winkelwagenprijzen voor alle websites
   - Ongebruikte regels beheren en verwijderen.
   - Voeg strikte regelvoorwaarden (zoals kenmerk- of categoriefilter) toe voor de meest efficiënte overeenkomst.
- **Coupons**—
   - Controleer of het totale aantal coupons in de database kleiner is dan 250.000.
   - Ongebruikte en verlopen coupons verwijderen.
   - Alleen het aantal coupons genereren dat nodig is om te voldoen aan de vereisten voor campagnes.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Mogelijke gevolgen voor de prestaties

Als u meer dan het aanbevolen maximumaantal regels of coupons voor de kartonprijs hebt, kan dit de prestaties van de site op de volgende manieren beïnvloeden:

- Hogere responstijd wanneer producten aan het winkelwagentje worden toegevoegd.
- Meer tijd om de miniaturen te laden en weer te geven.
- Meer tijd om de winkelwagenpagina weer te geven.
- Meer tijd om de **Totalen** op de pagina Afhandeling.
- Het toepassen van coupons kan meer dan 2 seconden duren.

## Aanvullende informatie

- [Informatie over marketingcampagnes en promoties](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Lijnen met winkelprijzen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Zelfstudie: Een regel voor een winkelwagenprijs maken](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Couponcodes](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce op cloudinfrastructuur: Beste praktijken voor archiefconfiguratie](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)

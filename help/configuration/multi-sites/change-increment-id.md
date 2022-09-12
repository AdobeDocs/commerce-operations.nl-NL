---
title: Toename-id wijzigen
description: Wijzig de increment ID voor een commercieel databaseentiteit.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Toename-id wijzigen

In dit artikel wordt besproken hoe u de increment-id voor een entiteit in een handelsdatabase (DB) (order, factuur, creditmemo, enzovoort) kunt wijzigen in een bepaalde winkel met behulp van de `ALTER TABLE` SQL-instructie.

## Betrokken versies

- Adobe Commerce (ter plaatse): 2.x.x
- Adobe Commerce op cloudinfrastructuur: 2.x.x
- MySQL: [elke ondersteunde versie](../../installation/prerequisites/database/mysql.md)

## Wanneer moet u de increment-id wijzigen

In de volgende gevallen moet u mogelijk de increment-id wijzigen voor nieuwe DB-entiteiten:

- Na een harde back-up herstellen op een live site
- Sommige transactiebestanden zijn verloren gegaan, maar hun id&#39;s worden al gebruikt door betalingsgateways (zoals PayPal) voor uw huidige Merchant-account. In dat geval verwerken de betaalgateways geen nieuwe orders die dezelfde id&#39;s hebben, en wordt de fout &#39;&#39;Dubbele factuur-id&#39;&#39; geretourneerd

>[!INFO]
>
>U kunt het probleem met de betaalgateway voor PayPal ook verhelpen door meerdere betalingen per factuur-ID toe te staan in de voorkeuren voor betalingsontvangst van PayPal. Zie [PayPal-gateway afgewezen aanvraag - dubbele factuurkwestie] in de _Kennisbank_.

## Vereiste stappen

1. Zoek opslagruimten en entiteiten waarvoor de nieuwe verhogings-id moet worden gewijzigd.
1. Maak verbinding met uw MySQL-database.
Voor Adobe Commerce op cloudinfrastructuur moet u eerst verbinding maken met de omgeving door middel van SSH.
1. Huidige controleren `auto_increment` waarde voor de lijst van de entiteitopeenvolging gebruikend de volgende vraag:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Als u een automatische verhoging voor een orde op de opslag met ID=1 controleert, zou de lijstnaam &quot;sequence_order_1&quot;zijn.

Als de waarde van de `auto_increment` kolom is &quot;1234&quot;, de volgende orde die bij de opslag wordt geplaatst met `ID=1` zal de ID &#39;#100001234&#39; hebben.

## Entiteit bijwerken om increment-id te wijzigen

Werk de entiteit bij met behulp van de volgende query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Belangrijk: De nieuwe toenamewaarde moet groter zijn dan de huidige waarde.

Na het uitvoeren van de volgende query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

De volgende volgorde die bij de winkel wordt geplaatst `ID=1` zal de ID &#39;#100002000&#39; hebben.

## Aanvullende aanbevolen stappen voor cloudproductieomgevingen

Voordat u het dialoogvenster `ALTER TABLE` We raden u ten zeerste aan om de volgende stappen uit te voeren in een productieomgeving van Adobe Commerce op cloudinfrastructuur:

- Test de volledige procedure om verhogingsidentiteitskaart op uw het opvoeren milieu te veranderen
- [Een DB-back-up maken] om de productiedatabase te herstellen in geval van een fout

<!-- Link Definitions -->

[PayPal-gateway afgewezen aanvraag - dubbele factuurkwestie]: https://support.magento.com/hc/en-us/articles/115002457473
[Een DB-back-up maken]: https://support.magento.com/hc/en-us/articles/360003254334
[elke ondersteunde versie]

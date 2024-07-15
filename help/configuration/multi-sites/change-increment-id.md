---
title: Toename-id wijzigen
description: Wijzig de increment-id voor een Commerce-database-entiteit.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Toename-id wijzigen

In dit artikel wordt besproken hoe u de verhogings-id voor een Commerce-database-entiteit (volgorde, factuur, creditnota, enzovoort) op een bepaalde Commerce-winkel kunt wijzigen met de SQL-instructie `ALTER TABLE` .

## Betrokken versies

- Adobe Commerce (op locatie): 2.x.x
- Adobe Commerce op cloud-infrastructuur: 2.x.x
- MySQL: [ om het even welke gesteunde versie ](../../installation/prerequisites/database/mysql.md)

## Wanneer moet u de increment-id wijzigen?

In de volgende gevallen moet u mogelijk de increment-id wijzigen voor nieuwe DB-entiteiten:

- Na een harde back-up herstellen op een live site
- Sommige transactiebestanden zijn verloren gegaan, maar hun id&#39;s worden al gebruikt door betalingsgateways (zoals PayPal) voor uw huidige Merchant-account. In dat geval verwerken de betaalgateways geen nieuwe orders die dezelfde id&#39;s hebben, en wordt de fout &quot;Dubbele factuur-id&quot; geretourneerd

>[!INFO]
>
>U kunt het probleem met de betaalgateway voor PayPal ook verhelpen door meerdere betalingen per factuur-ID toe te staan in de voorkeuren voor betalingsontvangst van PayPal. Zie {de gateway van 0} PayPal verworpen verzoek - dubbele factuurkwestie ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) in de _Kennisbank_.[

## Vereiste stappen

1. Zoek opslagruimten en entiteiten waarvoor de nieuwe verhogings-id moet worden gewijzigd.
1. Maak verbinding met uw MySQL-database.
Voor Adobe Commerce op cloudinfrastructuur moet u eerst verbinding maken met de omgeving door middel van SSH.
1. Controleer de huidige `auto_increment` waarde voor de lijst van de entiteitopeenvolging gebruikend de volgende vraag:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Als u een automatische verhoging voor een orde op de opslag met ID=1 controleert, zou de lijstnaam &quot;sequence_order_1&quot;zijn.

Als de waarde van de kolom `auto_increment` &#39;1234&#39; is, heeft de volgende volgorde die bij `ID=1` in de winkel wordt geplaatst, de ID &#39;#100001234&#39;.

## Entiteit bijwerken om increment-id te wijzigen

Werk de entiteit bij met behulp van de volgende query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Belangrijk: de nieuwe toenamewaarde moet groter zijn dan de huidige.

Na het uitvoeren van de volgende query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

De volgende volgorde die met `ID=1` bij de winkel wordt geplaatst, heeft de id &#39;#100002000&#39;.

## Aanvullende aanbevolen stappen voor cloudproductieomgevingen

Voordat we de query voor `ALTER TABLE` uitvoeren op een productieomgeving van Adobe Commerce op een cloudinfrastructuur, raden we u ten zeerste aan deze stappen uit te voeren:

- Test de volledige procedure om verhogingsidentiteitskaart op uw het opvoeren milieu te veranderen
- [ creeer een steun van DB ] om uw Productie-OB in het geval van mislukking te herstellen

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[Een DB-back-up maken]: https://support.magento.com/hc/en-us/articles/360003254334
[ om het even welke gesteunde versie ]

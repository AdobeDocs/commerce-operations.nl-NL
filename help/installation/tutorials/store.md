---
title: De winkel configureren
description: Voer de volgende stappen uit om uw Adobe Commerce- of Magento Open Source-winkel te configureren.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# De winkel configureren

Voordat u deze opdracht uitvoert, moet u het volgende doen: *of* u moet [de toepassing installeren](../advanced.md):

* [Implementatieconfiguratie maken of bijwerken](deployment.md)
* [Het databaseschema maken](database.md)

## Beveiligde installatie

{{$include /help/_includes/secure-install.md}}

## De winkel configureren

Opdrachtgebruik:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

In de volgende tabel worden parameters en waarden gedefinieerd:

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--base-url` | Baseer URL om tot uw Admin en opslag in om het even welke volgende formaten toegang te hebben:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Opmerking:** De regeling (`http://` of `https://`) en een schuine streep aan het einde zijn vereist. `<your install dir>` is het documentafhankelijke relatieve pad waarin de toepassing wordt geïnstalleerd. Afhankelijk van hoe u opstelling uw Webserver en virtuele gastheren, de weg magento2 zou kunnen zijn of het zou leeg kunnen zijn.<br><br>Als u de toepassing wilt openen op de localhost, kunt u `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` die een basis-URL vertegenwoordigt die wordt gedefinieerd door een virtuele host-instelling of door een virtualisatieomgeving zoals Docker. Als u bijvoorbeeld een virtuele host instelt met de hostnaam commerce.example.com, kunt u de toepassing installeren met `--base-url={{base_url}}` en heb toegang tot Admin met een URL als `http://commerce.example.com/admin`. | Nee |
| `--language` | Taalcode die moet worden gebruikt in Admin en storefront.<br><br>(Als u dit nog niet hebt gedaan, kunt u de lijst met taalcodes weergeven door `magento info:language:list` van de `bin` directory.) | Nee |
| `--currency` | Standaardvaluta voor gebruik in de winkel. <br><br>(Als u dit nog niet hebt gedaan, kunt u de lijst met valuta&#39;s weergeven door `magento info:currency:list` van de `bin` directory.) | Nee |
| `--timezone` | Standaardtijdzone die moet worden gebruikt in Admin en storefront. (Als u dit nog niet hebt gedaan, kunt u de lijst met tijdzones weergeven door `magento info:timezone:list` van de `bin` directory.) | Nee |
| `--use-rewrites` | `1` betekent dat u herschrijvingen van webservers gebruikt voor gegenereerde koppelingen in de winkel en in Admin.<br><br>`0` Hiermee schakelt u het gebruik van herschrijvingen van webservers uit. Dit is de standaardinstelling. | Nee |
| `--use-secure` | `1` laat het gebruik van de Veilige Laag van Contactdozen (SSL) in opslag URLs toe. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` schakelt het gebruik van SSL uit. In dit geval wordt aangenomen dat alle andere veilige URL-opties ook 0 zijn. Dit is de standaardinstelling. | Nee |
| `--base-url-secure` | Beveilig basis-URL voor toegang tot uw Admin en winkel in de volgende indeling: `http[s]://<host or ip>/<your install dir>/` | Nee |
| `--use-secure-admin` | `1` betekent dat u SSL gebruikt om toegang te krijgen tot Admin. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` betekent dat u geen SSL gebruikt met de Admin. Dit is de standaardinstelling. | Nee |
| `--admin-use-security-key` | `1` Hiermee gebruikt de toepassing een willekeurig gegenereerde sleutelwaarde voor toegang tot pagina&#39;s in de beheerfunctie en in formulieren. Deze zeer belangrijke waarden helpen dwars-plaats manuscriptvervalsingsaanvallen verhinderen. Dit is de standaardinstelling.<br/><br/>`0` Hiermee schakelt u het gebruik van de toets uit. | Nee |
| `--magento-init-params` | Toevoegen aan elke opdracht om de initialisatieparameters van de toepassing aan te passen<br/><br/>Bijvoorbeeld: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nee |

---
title: De winkel configureren
description: Voer de volgende stappen uit om uw Adobe Commerce-winkel te configureren.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# De winkel configureren

Alvorens u dit bevel in werking stelt, moet u het volgende *doen of* u moet [ de toepassing ](../advanced.md) installeren:

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
| `--base-url` | Baseer URL aan gebruik om tot uw Admin en opslag in om het even welke volgende formaten toegang te hebben:<br><br> - `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** de regeling (`http://` of `https://`) en een het slepen schuine streep worden allebei vereist. `<your install dir>` is het documentafhankelijke relatieve pad waarin de toepassing wordt geïnstalleerd. Afhankelijk van hoe u opstelling uw Webserver en virtuele gastheren, de weg magento2 zou kunnen zijn of het zou leeg kunnen zijn.<br><br> om tot de toepassing op localhost toegang te hebben, kunt u `http://127.0.0.1/<your install dir>/` gebruiken.<br><br> - `{{base_url}}` die een basis-URL vertegenwoordigt die wordt gedefinieerd door een virtuele hostinstelling of door een virtualisatieomgeving zoals Docker. Als u bijvoorbeeld een virtuele host instelt met de hostnaam commerce.example.com, kunt u de toepassing installeren met `--base-url={{base_url}}` en toegang krijgen tot de beheerder met een URL zoals `http://commerce.example.com/admin` . | Nee |
| `--language` | Taalcode die moet worden gebruikt in Admin en storefront.<br><br> (Als u dit nog niet hebt gedaan, kunt u de lijst met taalcodes weergeven door `magento info:language:list` in te voeren vanuit de map `bin` .) | Nee |
| `--currency` | Standaardvaluta voor gebruik in de winkel. <br><br> (Als u dit nog niet hebt gedaan, kunt u de lijst met valuta&#39;s weergeven door `magento info:currency:list` in te voeren vanuit de map `bin` .) | Nee |
| `--timezone` | Standaardtijdzone die moet worden gebruikt in Admin en Storage. (Als u dit nog niet hebt gedaan, kunt u de lijst met tijdzones weergeven door `magento info:timezone:list` in te voeren in de map `bin` .) | Nee |
| `--use-rewrites` | `1` betekent dat u herschrijvingen van webservers gebruikt voor gegenereerde koppelingen in de winkel en in Admin.<br><br>`0` schakelt het gebruik van herschrijven van webservers uit. Dit is de standaardinstelling. | Nee |
| `--use-secure` | `1` maakt het gebruik van SSL (Secure Sockets Layer) in winkel-URL&#39;s mogelijk. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` schakelt het gebruik van SSL uit. In dit geval wordt aangenomen dat alle andere veilige URL-opties ook 0 zijn. Dit is de standaardinstelling. | Nee |
| `--base-url-secure` | Beveilig basis-URL voor toegang tot uw beheerder en winkel in de volgende indeling: `http[s]://<host or ip>/<your install dir>/` | Nee |
| `--use-secure-admin` | `1` betekent dat u SSL gebruikt om toegang te krijgen tot Admin. Zorg ervoor dat uw webserver SSL ondersteunt voordat u deze optie selecteert.<br><br>`0` betekent dat u geen SSL gebruikt met de Admin. Dit is de standaardinstelling. | Nee |
| `--admin-use-security-key` | `1` zorgt ervoor dat de toepassing een willekeurig gegenereerde sleutelwaarde gebruikt om pagina&#39;s in de beheerfunctie en in formulieren te openen. Deze zeer belangrijke waarden helpen dwars-plaats manuscriptvervalsingsaanvallen verhinderen. Dit is de standaardinstelling.<br/><br/>`0` schakelt het gebruik van de toets uit. | Nee |
| `--magento-init-params` | Voeg aan om het even welk bevel toe om toepassings initialisatieparameters aan te passen <br/><br/> bijvoorbeeld: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nee |

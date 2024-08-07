---
title: Een beheerdersaccount maken, bewerken of ontgrendelen
description: Voer de volgende stappen uit om het beheerdersaccount voor uw Adobe Commerce Admin-toepassing te beheren.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Een beheerdersaccount maken, bewerken of ontgrendelen

Voordat u deze opdracht kunt gebruiken, moet u het volgende doen:

- [De implementatieconfiguratie maken](deployment.md)
- [Laat minstens Magento_Authorization en Magento_User modules toe](manage-modules.md)
- Het databaseschema maken

>[!NOTE]
>
>De eenvoudigste manier om de database te maken is met de opdracht `magento setup:upgrade` .

## Beheerders maken of bewerken

Gebruik deze opdracht om een beheerder te maken of om een bestaande beheerder te bewerken.

>[!NOTE]
>
>Als u een beheerder bewerkt, kunnen alleen de instructies `first name` , `last name` en `password` worden bewerkt.

Opdrachtgebruik:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

In de volgende tabel worden parameters en waarden gedefinieerd:

| Naam | Waarde | Vereist? |
|--- |--- |--- |
| `--admin-firstname` | Voornaam van beheerder. | Ja |
| `--admin-lastname` | Achternaam van beheerder. | Ja |
| `--admin-email` | E-mailadres van de beheerder. | Ja |
| `--admin-user` | Gebruikersnaam beheerder. | Ja |
| `--admin-password` | Beheerderswachtwoord. Het wachtwoord moet ten minste 7 tekens lang zijn en ten minste één alfabetisch en numeriek teken bevatten. <br><br> wij adviseren een langer, complexer wachtwoord. Als de wachtwoordtekenreeks speciale tekens bevat die letterlijke interpretatie vereisen (zoals backslashes of spaties), plaatst u het wachtwoord tussen enkele aanhalingstekens. | Ja |
| `--magento-init-params` | Voeg aan om het even welk bevel toe om toepassings initialisatieparameters aan te passen <br/><br/> bijvoorbeeld: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nee |

Voorbeeld van het gebruik:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Als u om het even welke vereiste params specificeert, vraagt de toepassing over hen in CLI:

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

In het volgende voorbeeld worden `first name` , `last name` en `password` van `j.doe` admin user bijgewerkt:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Een beheerdersaccount ontgrendelen

Gebruik deze opdracht om de account te ontgrendelen van een beheerder die is vergrendeld, meestal vanwege meerdere onjuiste aanmeldingspogingen.

```bash
bin/magento admin:user:unlock {username}
```

U moet de gebruikersnaam van de beheerder opgeven. Voorbeeld:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Als de account niet ontgrendeld is of als er een probleem is, wordt het volgende bericht weergegeven:

```
The user account "admin" was not locked or could not be unlocked
```

Controleer of de gebruiker een beheerder is, of de gebruiker actief is en of de account vergrendeld is. Om de lijst van gesloten gebruikers in Admin te bekijken, login als beheerder en klik **Systeem** > **Toestemmingen** > **Vergrendelde Gebruikers**.

Als de account niet bestaat, wordt het volgende bericht weergegeven:

```
Couldn't find the user account "bob"
```

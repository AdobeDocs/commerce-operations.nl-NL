---
title: 'ACSD-67039: Klantrecords zijn niet opgeslagen vanwege de validatie van rp_token-systeemkenmerken'
description: Pas de ACSD-67039-patch toe om het Adobe Commerce-probleem op te lossen waarbij coderingsdiakritische tekens validatie-einden veroorzaken op rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: Klantrecords zijn niet opgeslagen vanwege `rp_token` systeemkenmerkvalidatie

De ACSD-67039-patch verhelpt het probleem dat klantgegevens niet zijn opgeslagen vanwege de validatie van het systeemkenmerk `rp_token` en dat de validatie van diakritische gegevens alleen is toegepast op de e-mail van de resulterende klant. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-67039. Dit probleem is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p9

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Coderingsdiakritische tekens veroorzaken validatiefouten bij `rp_token` , die van validatie is uitgesloten. Diakritische tekens zijn alleen toegestaan voor e-mailadressen, zoals bedoeld.

<u> Stappen om </u> te reproduceren:

1. Installeer de Adobe Commerce 2.4.4-versie.
1. Maak een klant.
1. Upgrade Adobe Commerce naar versie 2.4.6 van de eerdere versie van 2.4.4 waar de klant al was gemaakt.
1. Stel de coderingssleutel in op `env.php` =
   *d337b914e91ff703b1e94ba4156adf0*
1. Stel de onderstaande waarden in de database in voor elke klant onder de tabel `customer_entity` :
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20 :06: 14*
1. Ga in het deelvenster Beheer naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** .
1. Bewerk de klant waarvoor u zojuist de bovenstaande waarden hebt bijgewerkt.
1. Klik op **[!UICONTROL Save Customer]** of **[!UICONTROL Save and Continue Edit]** .

<u> Verwachte resultaten </u>:

De klantwaarden zijn opgeslagen.

<u> Ware resultaten </u>:

Het klantenverslag wordt niet bewaard, en de admin gebruiker ziet het foutenbericht, *iets ging verkeerd terwijl het bewaren van de klant.*
`system.log` bevat de volgende fout:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Patches toepassen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen

---
title: 'MDVA-39305-V3: Login kwestie met toegelaten  [!DNL Google reCAPTCHA]'
description: Pas mDVA-39305-V3 flard toe om de kwestie van Adobe Commerce te bevestigen waar de geregistreerde klanten niet aan login kunnen wanneer  [!DNL Google reCAPTCHA]  wordt toegelaten. Dit flard lost ook de kwestie op waar een vorm kan worden voorgelegd alvorens  [!DNL Google reCAPTCHA]  volledig laadt. Bovendien wordt de fout *Call naar een lidfunctie isDisabled() op null* gecorrigeerd wanneer blokken worden gebruikt op niet-standaardlocaties op een CMS-pagina.
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: Aanmeldingsprobleem met ingeschakeld [!DNL Google reCAPTCHA]

>[!NOTE]
>
>Dit flard is een update van [ mDVA-39305 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md) flard.

De MDVA-39305-V3 patch verhelpt het probleem dat geregistreerde klanten zich niet kunnen aanmelden wanneer [!DNL Google reCAPTCHA] is ingeschakeld. Deze patch verhelpt ook het probleem waarbij een formulier kan worden verzonden voordat [!DNL Google reCAPTCHA] volledig is geladen. Bovendien, bevestigt het de fout *Vraag aan een lidfunctie isDisabled () op ongeldig* wanneer de blokken in niet-standaardplaatsen op een pagina van CMS worden gebruikt.

Dit flard werd toegevoegd in het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 versie. Het is bijgewerkt in de QPT 1.1.58-release en bevat nu nieuwe Adobe Commerce-versies 2.4.7 - 2.4.7-p4. De patch-id is MDVA-39305-V3. Het probleem is opgelost in Adobe Commerce versie 2.4.4, 2.4.5-p2 en 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.5-p2, 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Problemen

### Zaak I

1. Geregistreerde klanten kunnen zich niet aanmelden met de ingeschakelde [!DNL Google reCAPTCHA] .
1. Een formulier kan worden verzonden voordat [!DNL Google reCAPTCHA] volledig is geladen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** en schakel *** [!DNL Google reCAPTCHA] *** in.
1. Ga naar de voorkant.
1. Open **[!UICONTROL Developer Tool Console]** in de browser.

<u> Verwachte resultaten </u>:

Geen CSP waarschuwingen in de console.

<u> Ware resultaten </u>:

CSP waarschuwingen in de console.

### Zaak II

Een fout die *roepen aan een lidfunctie isDisabled () op ongeldig* verklaart wordt geworpen wanneer de blokken in niet-standaardplaatsen op een pagina van CMS worden gebruikt.

<u> Stappen om </u> te reproduceren:

1. Maak een statisch blok met de onderstaande inhoud:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Voeg een statisch blok van **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]** toe aan een CMS-pagina.
1. Sla de pagina op.

<u> Verwachte resultaten </u>:

De pagina wordt zonder fouten geladen.

<u> Ware resultaten </u>:

Er treedt een fout van 500 op op de pagina in de winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

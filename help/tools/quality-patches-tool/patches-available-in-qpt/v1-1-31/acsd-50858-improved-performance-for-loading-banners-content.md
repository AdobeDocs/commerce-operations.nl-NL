---
title: 'ACSD-50858: Verbeterde prestaties voor het laden van banners-inhoud'
description: Pas de ACSD-50858-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de bannerprestaties worden beïnvloed op de winkelwagentje/afhandelingspagina als gevolg van buitensporige DB-query's en een langere laadtijd.
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# ACSD-50858: Verbeterde prestaties voor het laden van banners-inhoud

De ACSD-50858-patch verhelpt een probleem op het gebied van bannerprestaties op de pagina Kaart/Afhandeling: *bovenmatige vragen van DB en verhoogde tijd van het paginading*. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-50858. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van de banner worden beïnvloed in het karretje/de controlepagina toe te schrijven aan *buitensporige vragen van DB en verhoogde tijd van het paginading*.

Dit probleem is opgelost door de manier te wijzigen waarop de inhoud van banners wordt geladen. Hierdoor is het aantal DB-query&#39;s met 99,99% en de laadtijd van de pagina met ~99% verminderd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Admin en maak een eenvoudig product.
1. Maak een klant, hetzij via Admin of de frontend, en voeg er een verzendadres voor toe.
1. Verplaats banners.php naar de map `magento_root/pub/` .
1. Maak banners met de opdracht `php pub/banners.php` . Het zal 10.000 eenvoudige banners en 1.000 banners met verkoopregels produceren.
1. Meld u aan bij de klant die u eerder op de voorzijde hebt gemaakt.
1. Voeg het eerder gemaakte product toe aan het winkelwagentje.
1. Ga naar de afhandelingspagina (Afrekenen/Kar).
1. Controleer de laadtijd van de `banner/ajax/load` aanvraag:

   * Zonder `bin/magento dev:query-log:enable`
   * Met `bin/magento dev:query-log:enable`

     ```shell
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u> Verwachte resultaten </u>:

Verlaag het aantal DB-query&#39;s voor `magento_banner_content` en de laadtijd van de pagina met cart- en uitcheckpagina.

<u> Ware resultaten </u>:

Verhoog het aantal DB-query&#39;s voor `magento_banner_content` en de laadtijd van de pagina met cart/checkout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende informatie

<u> banners.php inhoud </u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.

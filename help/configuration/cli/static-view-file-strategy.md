---
title: Implementatiestrategieën voor statische weergavebestanden
description: Leer over plaatsingsstrategieën voor statische meningsdossiers in de toepassingen van Adobe Commerce. Ontdek optimale implementatiemethoden voor verschillende gebruiksgevallen.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Implementatiestrategieën voor statische weergavebestanden

Bij het implementeren van statische weergavebestanden kunt u een van de drie beschikbare strategieën kiezen. Elk van hen verstrekt optimale plaatsingsresultaten voor verschillende gebruiksgevallen:

- [&#x200B; Norm &#x200B;](#standard-strategy): het regelmatige plaatsingsproces.
- [&#x200B; Snel &#x200B;](#quick-strategy) (_gebrek_): minimaliseert de tijd die voor plaatsing wordt vereist wanneer de dossiers voor meer dan één scène worden opgesteld.
- [&#x200B; Compact &#x200B;](#compact-strategy): minimaliseert de ruimte die door de gepubliceerde meningsdossiers wordt genomen.

In de volgende secties worden de implementatiedetails en -kenmerken van elke strategie beschreven.

## Standaardstrategie

Wanneer de Standaardstrategie wordt gebruikt, worden alle statische meningsdossiers voor alle pakketten opgesteld, dat wil zeggen, verwerkt door [`\Magento\Framework\App\View\Asset\Publisher` &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Voor meer informatie, zie [&#x200B; statische meningsdossiers &#x200B;](../cli/static-view-file-deployment.md) opstellen.

## Snelle strategie

De snelle strategie voert de volgende acties uit:

1. Voor elk thema wordt één willekeurige landinstelling gekozen en worden alle bestanden voor deze landinstelling geïmplementeerd, zoals in de standaardstrategie.
1. Voor alle andere landinstellingen van het thema:

   1. De dossiers die de opgestelde scène met voeten treden worden bepaald en opgesteld.
   1. Alle andere bestanden worden beschouwd als vergelijkbaar voor alle landinstellingen en worden gekopieerd van de geïmplementeerde landinstelling.

>[!INFO]
>
>Door _gelijkaardige_, bedoelen wij dossiers die van de scène, het thema, of het gebied onafhankelijk zijn. Deze bestanden kunnen CSS, afbeeldingen en lettertypen bevatten.

Deze benadering minimaliseert de plaatsingstijd die voor veelvoudige scènes wordt vereist hoewel veel dossiers worden gedupliceerd.

## Compacte strategie

Met de compacte strategie vermijdt u bestandsduplicatie door vergelijkbare bestanden op te slaan in submappen van `base` .

Voor het geoptimaliseerde resultaat worden drie bereiken voor mogelijke gelijkenis toegewezen: gebied, thema en landinstelling. De submappen van `base` worden gemaakt voor alle combinaties van deze bereiken.

De bestanden worden op basis van de volgende patronen naar deze submappen geïmplementeerd.

| Patroon | Beschrijving |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Bestanden die specifiek zijn voor een bepaald gebied, thema en landinstelling |
| `<area>/<theme>/default` | Bestanden die vergelijkbaar zijn voor alle landinstellingen van een bepaald thema in een bepaald gebied. |
| `<area>/Magento/base/<locale>` | Bestanden die specifiek zijn voor een bepaald gebied en een bepaalde landinstelling, maar die vergelijkbaar zijn voor alle thema&#39;s. |
| `<area>/Magento/base/default` | Bestanden die specifiek zijn voor een bepaald gebied, maar vergelijkbaar voor alle thema&#39;s en landinstellingen. |
| `base/Magento/base/<locale>` | Bestanden die vergelijkbaar zijn voor alle gebieden en thema&#39;s, maar specifiek zijn voor een bepaalde landinstelling. |
| `base/Magento/base/default` | Vergelijkbaar voor alle gebieden, thema&#39;s en landinstellingen. |

### Geïmplementeerde bestanden toewijzen

De benadering van plaatsing die in de compacte strategie wordt gebruikt betekent dat de dossiers van basisthema&#39;s en scènes worden geërft. Deze overervingsrelaties worden opgeslagen in de kaartbestanden voor elke combinatie van gebied, thema en landinstelling. Er zijn afzonderlijke toewijzingsbestanden voor PHP en JS:

- `map.php`
- `requirejs-map.js`

Het `map.php` dossier wordt gebruikt door [`Magento\Framework\View\Asset\Repository` &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) om correcte URLs te bouwen.

De `requirejs-map.js` wordt gebruikt door de `baseUrlResolver` -insteekmodule voor RequireJS.

Voorbeeld van `map.php` :

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Voorbeeld van `requirejs-map.js` :

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Tips voor ontwikkelaars van extensies

Gebruik [`\Magento\Framework\View\Asset\Repository::createAsset()` &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244) om URLs aan statische meningsdossiers te bouwen.

Gebruik geen URL-aaneenschakelingen om problemen te voorkomen waarbij statische bestanden niet worden gevonden en niet worden weergegeven tijdens het weergeven van pagina&#39;s.

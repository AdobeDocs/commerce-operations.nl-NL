---
title: Aanbevolen werkwijzen voor configuratie van indexen
description: Prestaties van sites onderhouden en optimaliseren door de best practices voor indexeerconfiguratie te volgen.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Aanbevolen procedures voor indexeerconfiguratie

Als u de prestaties van de site wilt optimaliseren en behouden, bekijkt en werkt u de indexeerconfiguratie bij met behulp van de best practices voor prestaties die in dit artikel worden beschreven.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Indexeerders instellen om volgens een schema bij te werken

Adobe Commerce heeft twee soorten indexeermodi: [!UICONTROL Update on Save] (standaardinstelling) en [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** wordt de index direct bijgewerkt wanneer de catalogus of andere gegevens worden gewijzigd. Als een Admin-gebruiker bijvoorbeeld nieuwe producten aan een categorie toevoegt, wordt de index van de categorieproducten onmiddellijk opnieuw aangepast wanneer de update wordt opgeslagen.

- **[!UICONTROL Update on Schedule]** de wijze slaat informatie over gegevensupdates op, en het opnieuw indexeren verrichtingen en indexupdates worden beheerd door een hulpbaan die op de achtergrond met geplande intervallen loopt. De snijtaak voert niet altijd een herindex uit telkens als het loopt. De index wordt alleen opnieuw toegepast als er nieuwe items staan in de logboeken voor indexwijzigingen (er is bijvoorbeeld een achterstand bij de indexen).

Als u een grote winkel hebt met meerdere beheerders die op de achtergrond werken of als u veel import en export hebt, worden er regelmatig indexupdates uitgevoerd. Als de configuratie van uw site-index is ingesteld op [!UICONTROL Update on Save] in deze modus worden de databaseprestaties door veelvuldig opnieuw indexeren verminderd, waardoor de prestaties van de site worden vertraagd en het herindexeringsproces veel vertraging oploopt, vooral bij grote winkels.

Volg de volgende aanbevolen procedures voor indexering om de prestaties van de site te maximaliseren:

- Controleer de indexconfiguratie.
- Indexeerders instellen op _[!UICONTROL Update on Schedule]_voor grote plaatsen, en plaatsen met frequente updates en zwaar verkeer. Zie [Indexbeheer](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Volgen [best practices voor prestaties](../../../performance/configuration.md) voor het beheren van indexen.

>[!IMPORTANT]
>
>De [!DNL Customer Grid] kan alleen opnieuw worden gedexeerd met de opdracht [!UICONTROL Update on Save] -optie. Deze index ondersteunt het `Update by Schedule` -optie.

## Aanvullende informatie

- [Indexbeheer voor Admin-gebruikers](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexbeheer met behulp van de Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Overzicht van indexering voor ontwikkelaars](https://developer.adobe.com/commerce/php/development/components/indexing/)

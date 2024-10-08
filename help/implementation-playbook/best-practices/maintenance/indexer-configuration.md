---
title: Aanbevolen werkwijzen voor configuratie van indexen
description: Prestaties van sites onderhouden en optimaliseren door de best practices voor indexeerconfiguratie te volgen.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 153cf3bae74a78d7a41176e0216203d354d2513b
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Aanbevolen procedures voor indexeerconfiguratie

Als u de prestaties van de site wilt optimaliseren en behouden, bekijkt en werkt u de indexeerconfiguratie bij met behulp van de best practices voor prestaties die in dit artikel worden beschreven.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Indexeerders instellen om volgens een schema bij te werken

Adobe Commerce heeft twee typen indexeermodi: [!UICONTROL Update on Save] en [!DNL Update on Schedule] .

- In de modus **[!UICONTROL Update on Save]** worden de indexen direct bijgewerkt wanneer de catalogus of andere gegevens worden gewijzigd. Als een Admin-gebruiker bijvoorbeeld nieuwe producten aan een categorie toevoegt, wordt de index van de categorieproducten onmiddellijk opnieuw aangepast wanneer de update wordt opgeslagen.

- In de modus **[!UICONTROL Update on Schedule]** wordt informatie over gegevensupdates opgeslagen en worden herindexeringsbewerkingen en indexupdates beheerd door een snijtaak die op de achtergrond wordt uitgevoerd met geplande intervallen. De snijtaak voert niet altijd een herindex uit telkens als het loopt. De index wordt alleen opnieuw toegepast als er nieuwe items staan in de logboeken voor indexwijzigingen (er is bijvoorbeeld een achterstand bij de indexen).

Als u een grote winkel hebt met meerdere beheerders die op de achtergrond werken of als u veel import en export hebt, worden er regelmatig indexupdates uitgevoerd. Als de configuratie van de index van uw site is ingesteld op de modus [!UICONTROL Update on Save] , leidt het vaak opnieuw indexeren tot een verslechtering van de databaseprestaties, wat de prestaties van de site vertraagt en tot lange vertragingen in het herindexeringsproces, vooral bij grote winkels.

Volg de volgende aanbevolen procedures voor indexering om de prestaties van de site te maximaliseren:

- Controleer de indexconfiguratie.
- Stel de indexeerders in op _[!UICONTROL Update on Schedule]_voor grote sites en sites met veelvuldige updates en veel verkeer. Zie [ Beheer van de Index ](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Volg [ prestaties beste praktijken ](../../../performance/configuration.md) voor het beheren van indexen.

>[!IMPORTANT]
>
>De [!DNL Customer Grid] kan alleen opnieuw worden genummerd met de optie [!UICONTROL Update on Save] . Deze index ondersteunt de optie `Update by Schedule` niet.

## Aanvullende informatie

- [Indexbeheer voor Admin-gebruikers](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [ Beheer van de Index die het Magento CLI ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) gebruikt
- [ Indexerend overzicht voor ontwikkelaars ](https://developer.adobe.com/commerce/php/development/components/indexing/)

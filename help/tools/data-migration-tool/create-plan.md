---
title: Een plan voor gegevensmigratie maken
description: Voer de volgende stappen uit om een gegevensmigratieplan te maken voor een geslaagde upgrade van Magento 1 naar Magento 2.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Een plan voor gegevensmigratie maken

Om met succes te migreren en problemen te vermijden, moet u uw migratie grondig plannen en testen.

## Voordat u begint: Overweeg een upgrade

Migratie is een ideaal moment om serieuze wijzigingen aan te brengen en uw site klaar te maken voor het volgende groeicijfer. Overweeg of uw nieuwe plaats met meer hardware of een geavanceerdere topologie met betere caching lagen moet worden ontworpen.

## Stap 1: Extensies op uw huidige site controleren

* Welke extensies hebt u geïnstalleerd?

* Hebt u vastgesteld of u al deze extensies op uw nieuwe site nodig hebt? Er kunnen oude zijn die u veilig kunt verwijderen.

* Hebt u vastgesteld of er Magento 2-versies van uw extensies bestaan? Bezoek [ Commerce Marketplace ] om de recentste versies te vinden of uw uitbreidingsleverancier te contacteren.

* Welke database-elementen van uw extensies wilt u migreren?

## Stap 2: uw winkel samenstellen en voorbereiden voor migratie

* Stel een Magento 2-hardwaresysteem in met behulp van topologie en ontwerp die ten minste overeenkomen met uw bestaande Magento 1-systeem

* Installeer Magento 2.x (met alle modules van deze versie) en [!DNL Data Migration Tool] op een systeem dat aan de [&#x200B; systeemvereisten &#x200B;](../../installation/system-requirements.md) voldoet

* Breng aangepaste aanpassingen aan de code van [!DNL Data Migration Tool] aan als u bepaalde gegevens niet hoeft te migreren (zoals CMS Pages, Verkoopregels) of als u uw Magento-aanpassingen tijdens de migratie wilt converteren. Lees de [!DNL Data Migration Tool] Technische Specificatie van 0&rbrace; [&#x200B; om beter te begrijpen hoe de migratie van binnen werkt](technical-specification.md)

## Stap 3: Droge run

Voordat u de migratie op de productieomgeving start, kunt u het beste alle migratiestappen in uw testomgeving doorlopen.

Voer bij dergelijke migratietests de volgende stappen uit:

* Magento 1-winkel kopiëren naar een testserver

* De gerepliceerde Magento 1-winkel volledig migreren naar Magento 2

* Test uw nieuwe winkel grondig

## Stap 4: de migratie starten

1. Zorg ervoor dat de [!DNL Data Migration Tool] netwerktoegang heeft om verbinding te maken met Magento 1- en Magento 2-databases. Open de overeenkomstige havens in uw firewall.

1. Stop alle activiteiten in het Magento 1.x Admin Panel (behalve voor orderbeheer), zoals verzending, het maken van facturen en creditnota&#39;s. De lijst met toegestane activiteiten kan worden uitgebreid door de instellingen van de Deltamodus in de [!DNL Data Migration Tool] aan te passen.

   >[!NOTE]
   >
   >Je mag deze activiteiten pas hervatten als je Magento 2-winkel live gaat.

1. We raden u aan alle Magento 1.x-taken voor uitsnijden te stoppen.

   Als tijdens de migratie bepaalde taken moeten worden uitgevoerd, moet u er echter voor zorgen dat er geen nieuwe database-entiteiten worden gemaakt of dat de bestaande entiteiten zodanig worden gewijzigd dat dergelijke entiteiten niet door de Delta-modus kunnen worden verwerkt.

   Met de `enterprise_salesarchive_archive_orders` cron-taak worden bijvoorbeeld oude bestellingen naar archief verplaatst. Het uitvoeren van deze taak tijdens de migratie is veilig, omdat deze taak in de Delta-modus wordt herkend en de gearchiveerde bestellingen correct worden verwerkt.

1. Gebruik [!DNL Data Migration Tool] om instellingen en websites te migreren.

1. Kopieer uw Magento 1.x-mediabestanden naar Magento 2.x.

   U moet deze bestanden handmatig kopiëren van de map `magento1-root/media` naar `magento2-root/pub/media` .

1. Gebruik [!DNL Data Migration Tool] om gegevens in bulk te kopiëren van Magento 1-database naar Magento 2-database.

   Als bepaalde extensies gegevens bevatten die u wilt migreren, moet u deze extensies mogelijk installeren, aangepast voor Magento 2. Als de structuur van de extensies anders is in de Magento 2-database, gebruikt u de toewijzingsbestanden die bij de [!DNL Data Migration Tool] worden geleverd.

1. Alle Magento 2.x-indexen opnieuw indexeren. Voor details, zie [&#x200B; indexeerders &#x200B;](../../configuration/cli/manage-indexers.md) in de _gids van de Configuratie_ leiden.

## Stap 5: Breng wijzigingen aan in de gemigreerde gegevens (indien nodig)

Soms wilt u na de migratie een andere catalogusstructuur, verkoopregels en CMS-pagina&#39;s in uw Magento 2-winkel opnemen.

Het is belangrijk om voorzichtigheid te oefenen terwijl het werken door handveranderingen van gegevens. De fouten leiden tot fouten in de stijgende stap van de gegevensmigratie die volgt.

Een product dat bijvoorbeeld is verwijderd uit Magento 2: het product dat is gekocht in je live Magento 1-winkel en dat niet meer beschikbaar is in je Magento 2-winkel. Het overdragen van gegevens over een dergelijke aankoop kan een fout veroorzaken wanneer de [!DNL Data Migration Tool] in de Delta-modus wordt uitgevoerd.

## Stap 6: Incrementele gegevens bijwerken

Nadat u gegevens hebt gemigreerd, moet u stapsgewijs gegevensupdates vastleggen die zijn toegevoegd in de Magento 1-winkel (zoals nieuwe bestellingen, revisies en wijzigingen in klantprofielen) en deze updates overbrengen naar de Magento 2-winkel met behulp van de Delta-modus.

* Start de incrementele migratie; updates worden voortdurend uitgevoerd. U kunt updates op elk gewenst moment niet meer overbrengen door op `Ctrl+C` te drukken.

* Test uw Magento 2-site gedurende deze tijd om eventuele problemen zo snel mogelijk op te sporen. Als er problemen optreden, drukt u op `Ctrl+C` om de incrementele migratie te stoppen en opnieuw te starten nadat u de problemen hebt opgelost.

>[!NOTE]
>
>Er kunnen waarschuwingen voor volumecontrole worden weergegeven als u uw Magento 2-site test en tegelijkertijd het migratieproces uitvoert. Dit gebeurt omdat u in Magento 2 entiteiten maakt die niet bestaan in Magento 1-exemplaar.

## Stap 7: Ga live

Nu uw Magento 2-site up-to-date is met Magento 1 en naar behoren functioneert, kunt u het volgende doen om naar de nieuwe site te gaan:

1. Zet uw Magento 1-systeem in de onderhoudsmodus (DOWNTIME STARTS).

1. Druk op Ctrl+C in het opdrachtvenster van het gereedschap Migratie om incrementele updates te stoppen.

1. Start je Magento 2 cron-taken.

1. In uw Magento 2-systeem moet u de aandelenindex opnieuw indexeren. Voor meer informatie, zie de [ gids van de Configuratie ].

1. Met een hulpprogramma van uw keuze kunt u pagina&#39;s in uw Magento 2-systeem slaan om pagina&#39;s in cache te plaatsen voor klanten die uw winkel gebruiken.

1. Voer een laatste verificatie van je Magento 2-site uit.

1. Wijzig DNS, taakverdelingsmechanisme enzovoort om naar nieuwe productiehardware (DOWNTIME ENDS) te verwijzen.

1. Magento 2 Store is nu klaar voor gebruik. U en uw klanten kunnen alle activiteiten hervatten.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com

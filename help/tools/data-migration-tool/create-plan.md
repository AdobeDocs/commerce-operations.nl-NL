---
title: Een gegevensmigratieplan maken
description: Leer hoe u een plan voor gegevensmigratie maakt voor het upgraden van Magento 1 naar Magento 2. Plan en test uw migratie om problemen te voorkomen.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Een plan voor gegevensmigratie maken

Als u uw migratie wilt voltooien en problemen wilt voorkomen, moet u uw migratie grondig plannen en testen.

## Voordat u begint: Overweeg een upgrade

Migratie is een goed moment om serieuze wijzigingen aan te brengen en uw site klaar te maken voor het volgende groeicijfer. Overweeg of uw nieuwe plaats met extra hardware of een geavanceerdere topologie met betere caching lagen moet worden ontworpen.

## Stap 1: Extensies op uw huidige site controleren

* Welke extensies hebt u geïnstalleerd?

* Hebt u vastgesteld of u al deze extensies op uw nieuwe site nodig hebt? Er kunnen oude zijn die u veilig kunt verwijderen.

* Hebt u vastgesteld of er Magento 2-versies van uw extensies bestaan? Bezoek [ Commerce Marketplace ](https://commercemarketplace.adobe.com/) om de recentste versies te vinden of uw uitbreidingsleverancier te contacteren.

* Welke database-elementen van uw extensies wilt u migreren?

## Stap 2: uw winkel samenstellen en voorbereiden voor migratie

* Stel een Magento 2-hardwaresysteem in met een topologie en een ontwerp die ten minste overeenkomen met uw bestaande Magento 1-systeem

* Installeer Magento 2 (met alle modules van deze versie) en [!DNL Data Migration Tool] op een systeem dat aan de [ systeemvereisten ](../../installation/system-requirements.md) voldoet

* Pas de [!DNL Data Migration Tool] -code aan om bepaalde gegevens over te slaan (zoals CMS-pagina&#39;s, verkoopregels) of om aanpassingen tijdens de migratie om te zetten. Lees de [!DNL Data Migration Tool] Technische Specificatie van 0} [ om meer over te leren hoe de migratie werkt](technical-specification.md)

## Stap 3: Droge run

Voordat u de migratie in de productieomgeving start, doorloopt u alle migratiestappen in de testomgeving.

Voer bij dergelijke migratietests de volgende stappen uit:

* Magento 1-winkel kopiëren naar een testserver

* De gerepliceerde Magento 1-winkel volledig migreren naar Magento 2

* Test uw nieuwe winkel grondig

## Stap 4: de migratie starten

1. Zorg ervoor dat de [!DNL Data Migration Tool] netwerktoegang heeft om verbinding te maken met Magento 1- en Magento 2-databases. Open de overeenkomstige havens in uw firewall.

1. Stop alle activiteiten in het Magento 1 Admin Panel (behalve Order Management), zoals verzending, het maken van facturen en creditnota&#39;s. De lijst met toegestane activiteiten kan worden uitgebreid door de instellingen van de Deltamodus in de [!DNL Data Migration Tool] aan te passen.

   >[!NOTE]
   >
   >Hervat deze activiteiten pas als je Magento 2-winkel live gaat.

1. We raden u aan alle Magento 1 cron-taken te stoppen.

   Als bepaalde taken tijdens de migratie moeten worden uitgevoerd, moet u ervoor zorgen dat deze geen databaseentiteiten maken of wijzigen op een manier die niet in de Delta-modus kan worden verwerkt.

   Met de `enterprise_salesarchive_archive_orders` cron-taak worden bijvoorbeeld oude bestellingen naar archief verplaatst. Het uitvoeren van deze taak tijdens de migratie is veilig, omdat deze taak in de Delta-modus wordt herkend en de gearchiveerde bestellingen correct worden verwerkt.

1. Gebruik [!DNL Data Migration Tool] om instellingen en websites te migreren.

1. Kopieer uw Magento 1-mediabestanden naar Magento 2.

   Kopieer deze bestanden handmatig van de map `magento1-root/media` naar `magento2-root/pub/media` .

1. Gebruik [!DNL Data Migration Tool] om gegevens in bulk te kopiëren van de Magento 1-database naar de Magento 2-database.

   Als bepaalde extensies gegevens bevatten die u wilt migreren, moet u deze extensies mogelijk installeren, aangepast voor Magento 2. Als de structuur van de extensies anders is in de Magento 2-database, gebruikt u de toewijzingsbestanden die bij de [!DNL Data Migration Tool] worden geleverd.

1. Alle Magento 2-indexen opnieuw indexeren. Voor details, zie [ indexeerders ](../../configuration/cli/manage-indexers.md) in de _gids van de Configuratie_ leiden.

## Stap 5: Breng wijzigingen aan in de gemigreerde gegevens (indien nodig)

Soms wilt u na de migratie een andere catalogusstructuur, verkoopregels en CMS-pagina&#39;s in uw Magento 2-winkel opnemen.

Het is belangrijk om voorzichtigheid te oefenen terwijl het werken door handveranderingen van gegevens. De fouten leiden tot fouten in de stijgende stap van de gegevensmigratie die volgt.

Een product dat bijvoorbeeld is verwijderd uit Magento 2: het product dat is gekocht in je live Magento 1-winkel en dat niet meer beschikbaar is in je Magento 2-winkel. Het overdragen van gegevens over een dergelijke aankoop kan een fout veroorzaken wanneer de [!DNL Data Migration Tool] in de Delta-modus wordt uitgevoerd.

## Stap 6: Incrementele gegevens bijwerken

Nadat u gegevens hebt gemigreerd, gebruikt u de Delta-modus om incrementele updates van Magento 1 (zoals nieuwe bestellingen, revisies en wijzigingen in het klantprofiel) vast te leggen en over te brengen naar Magento 2.

* Start de incrementele migratie; updates worden voortdurend uitgevoerd. U kunt updates op elk gewenst moment niet meer overbrengen door op `Ctrl+C` te drukken.

* Test uw Magento 2-site gedurende deze tijd om eventuele problemen zo snel mogelijk op te sporen. Als er problemen optreden, drukt u op `Ctrl+C` om de incrementele migratie te stoppen en opnieuw te starten nadat u de problemen hebt opgelost.

>[!NOTE]
>
>Er kunnen waarschuwingen voor volumecontrole worden weergegeven als u uw Magento 2-site test en het migratieproces tegelijkertijd uitvoert. Dit gebeurt omdat u in Magento 2 entiteiten maakt die niet bestaan in Magento 1-exemplaar.

## Stap 7: Ga live

Zodra uw Magento 2-site volledig is gemigreerd en normaal functioneert, voltooit u de cutover:

1. Zet uw Magento 1-systeem in de onderhoudsmodus (DOWNTIME STARTS).

1. Druk op Ctrl+C in het opdrachtvenster van het gereedschap Migratie om incrementele updates te stoppen.

1. Start je Magento 2 cron-taken.

1. In uw Magento 2-systeem moet u de aandelenindex opnieuw indexeren. Voor meer informatie, zie [ indexeerders ](../../configuration/cli/manage-indexers.md) in de _gids van de Configuratie_ leiden.

1. Met een hulpprogramma van uw keuze kunt u pagina&#39;s in uw Magento 2-systeem slaan om pagina&#39;s in cache te plaatsen voor klanten die uw winkel gebruiken.

1. Voer een laatste verificatie van je Magento 2-site uit.

1. Wijzig DNS, taakverdelingsmechanisme enzovoort om naar nieuwe productiehardware (DOWNTIME ENDS) te verwijzen.

1. Magento 2 Store is nu klaar voor gebruik. U en uw klanten kunnen alle activiteiten hervatten.

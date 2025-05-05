---
title: Een plan voor gegevensmigratie maken
description: Voer de volgende stappen uit om een plan voor gegevensmigratie te maken om een geslaagde upgrade van Magento 1 naar Magento 2 te garanderen.
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

* Hebt u bepaald als Magento 2 versies van uw uitbreidingen bestaan? Bezoek [ Commerce Marketplace ] om de recentste versies te vinden of uw uitbreidingsleverancier te contacteren.

* Welke database-elementen van uw extensies wilt u migreren?

## Stap 2: uw winkel samenstellen en voorbereiden voor migratie

* Opstelling een Magento 2 hardwaresysteem gebruikend topologie en ontwerp dat minstens uw bestaand Magento 1 systeem aanpast

* Installeer Magento 2.x (met alle modules van deze versie) en [!DNL Data Migration Tool] op een systeem dat aan de [ systeemvereisten ](../../installation/system-requirements.md) voldoet

* Breng aangepaste aanpassingen aan de [!DNL Data Migration Tool] -code aan als u bepaalde gegevens niet hoeft te migreren (zoals CMS-pagina&#39;s, Verkoopregels) of als u tijdens de migratie uw Magento wilt aanpassen. Lees de [ Technische Specificatie van 0&rbrace; ](technical-specification.md) om beter te begrijpen hoe de migratie van binnen werkt[!DNL Data Migration Tool]

## Stap 3: Droge run

Voordat u de migratie op de productieomgeving start, kunt u het beste alle migratiestappen in uw testomgeving doorlopen.

Voer bij dergelijke migratietests de volgende stappen uit:

* Kopieer uw Magento 1-winkel naar een testserver

* De gerepliceerde Magento 1-winkel volledig migreren naar Magento 2

* Test uw nieuwe winkel grondig

## Stap 4: de migratie starten

1. Zorg ervoor dat [!DNL Data Migration Tool] een netwerktoegang heeft om met Magento 1 en Magento 2 gegevensbestanden te verbinden. Open de overeenkomstige havens in uw firewall.

1. Stop alle activiteiten in Magento 1.x Admin Panel (behalve voor orderbeheer), zoals het verschepen, het creëren van facturen en creditnota&#39;s. De lijst met toegestane activiteiten kan worden uitgebreid door de instellingen van de Deltamodus in de [!DNL Data Migration Tool] aan te passen.

   >[!NOTE]
   >
   >U mag deze activiteiten pas hervatten wanneer uw Magento 2-winkel live gaat.

1. We raden u aan om alle Magento 1.x-snijtaken te stoppen.

   Als tijdens de migratie bepaalde taken moeten worden uitgevoerd, moet u er echter voor zorgen dat er geen nieuwe database-entiteiten worden gemaakt of dat de bestaande entiteiten zodanig worden gewijzigd dat dergelijke entiteiten niet door de Delta-modus kunnen worden verwerkt.

   Met de `enterprise_salesarchive_archive_orders` cron-taak worden bijvoorbeeld oude bestellingen naar archief verplaatst. Het uitvoeren van deze taak tijdens de migratie is veilig, omdat deze taak in de Delta-modus wordt herkend en de gearchiveerde bestellingen correct worden verwerkt.

1. Gebruik [!DNL Data Migration Tool] om instellingen en websites te migreren.

1. Kopieer uw Magento 1.x-mediabestanden naar Magento 2.x.

   U moet deze bestanden handmatig kopiëren van de map `magento1-root/media` naar `magento2-root/pub/media` .

1. Gebruik [!DNL Data Migration Tool] om uw gegevens van Magento 1 gegevensbestand aan Magento 2 gegevensbestand in bulk te kopiëren.

   Als bepaalde extensies gegevens bevatten die u wilt migreren, moet u deze extensies mogelijk installeren, aangepast voor Magento 2. Als de extensies een andere structuur hebben in Magento 2-database, gebruikt u de toewijzingsbestanden die bij de [!DNL Data Migration Tool] worden geleverd.

1. Alle Magento 2.x-indexen opnieuw indexeren. Voor details, zie [ indexeerders ](../../configuration/cli/manage-indexers.md) in de _gids van de Configuratie_ leiden.

## Stap 5: Breng wijzigingen aan in de gemigreerde gegevens (indien nodig)

Soms wilt u na de migratie mogelijk een Magento 2-winkel hebben met een andere catalogusstructuur, andere verkoopregels en andere CMS-pagina&#39;s.

Het is belangrijk om voorzichtigheid te oefenen terwijl het werken door handveranderingen van gegevens. De fouten leiden tot fouten in de stijgende stap van de gegevensmigratie die volgt.

Bijvoorbeeld, een product schrapte uit Magento 2: die die op uw levende Magento 1 opslag is gekocht en die niet meer in uw Magento 2 opslag beschikbaar is. Het overdragen van gegevens over een dergelijke aankoop kan een fout veroorzaken wanneer de [!DNL Data Migration Tool] in de Delta-modus wordt uitgevoerd.

## Stap 6: Incrementele gegevens bijwerken

Na het migreren van gegevens, moet u gegevens stapsgewijs updates vangen die in Magento 1 opslag (zoals nieuwe orden, recensies, en veranderingen in klantenprofielen) zijn toegevoegd en deze updates overbrengen naar Magento 2 opslag gebruikend de wijze van Delta.

* Start de incrementele migratie; updates worden voortdurend uitgevoerd. U kunt updates op elk gewenst moment niet meer overbrengen door op `Ctrl+C` te drukken.

* Test uw Magento 2-site gedurende deze tijd om problemen zo snel mogelijk op te sporen. Als er problemen optreden, drukt u op `Ctrl+C` om de incrementele migratie te stoppen en opnieuw te starten nadat u de problemen hebt opgelost.

>[!NOTE]
>
>Er kunnen waarschuwingen voor volumecontrole worden weergegeven als u tegelijkertijd uw Magento 2-site test en het migratieproces uitvoert. Het gebeurt omdat u in Magento 2 entiteiten maakt die niet in Magento 1 bestaan.

## Stap 7: Ga live

Nu uw Magento 2-site up-to-date is met Magento 1 en naar behoren functioneert, kunt u het volgende doen om naar de nieuwe site te knippen:

1. Plaats uw Magento 1-systeem in de onderhoudsmodus (DOWNTIME STARTS).

1. Druk op Ctrl+C in het opdrachtvenster van het gereedschap Migratie om incrementele updates te stoppen.

1. Start uw Magento 2 cron-taken.

1. In uw Magento 2 systeem, herdex de voorraadindexeer. Voor meer informatie, zie de [ gids van de Configuratie ].

1. Als u een hulpprogramma van uw keuze gebruikt, slaat u pagina&#39;s in uw Magento 2-systeem aan om pagina&#39;s in het cachegeheugen op te slaan vóór klanten die uw winkel gebruiken.

1. Voer een definitieve verificatie van uw Magento 2-site uit.

1. Wijzig DNS, taakverdelingsmechanisme enzovoort om naar nieuwe productiehardware (DOWNTIME ENDS) te verwijzen.

1. Magento 2-winkel is nu gebruiksklaar. U en uw klanten kunnen alle activiteiten hervatten.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com

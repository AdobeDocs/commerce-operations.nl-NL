---
title: Zelfgehoste Adobe Commerce-noodherstel
description: Leer over zelf-ontvangende rampenterugwinning ideeën en concepten en beste praktijken om te overwegen.
landing-page-description: Leer enkele concepten en zaken voor noodherstel die u in overweging kunt nemen wanneer u Adobe Commerce op uw eigen computer host.
short-description: Leer strategieën en concepten voor noodherstel om zelf Adobe Commerce te hosten.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cd546571-0241-4619-8696-3c5ebead9939
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1779'
ht-degree: 0%

---

# Zelfgehoste Adobe Commerce Disaster Recovery-ideeën

De rampenterugwinning voor dit artikel omvat een ontbroken plaatsing. Hoewel het hele proces misschien niet hetzelfde is, zijn soortgelijke beginselen van toepassing. Een ramp kan toe te schrijven zijn aan een mislukte productieplaatsing, server die niet ontvankelijk wordt, ontdekking van een uitbuiten en vele andere scenario&#39;s. Wanneer het terugwinningsproces voor een ontbroken plaatsing slechts twee eenvoudige stappen vereist, kan een terugwinning van een uitvinding veel uitdagender zijn. Vanwege de complexiteit van omgevingen, het hosten van variaties en andere complexe onderdelen biedt dit artikel ideeën en concepten, maar u moet het onderzoek zelf voortzetten. Op deze manier kunt u ervoor zorgen dat u een strategie ontwerpt die aan uw bedrijfsbehoeften voldoet.

## Het terugwinningsproces van de praktijk vaak

Praktijk, Praktijk, Praktijk. Er is een reden waarom de praktijken eerst op de lijst van de rampenterugwinning verschijnen. Het is verre van gemakkelijk om een herstelplan op te zetten maar nooit het uit te voeren. Als u niet genoeg oefent, bent u vatbaar aan fouten, gemiste stappen, en waarschijnlijk maakt een daadwerkelijke terugwinning langer duurt. Het gemak voor uw praktijkterugwinning is aan u en uw bedrijfspartners. Het maken van het terugwinningsproces een jaarlijkse gebeurtenis zou goed genoeg kunnen zijn, maar een diep gesprek met die besluitvormers in uw bedrijf zou verscheidene zeer belangrijke onderwerpen moeten omvatten. Deze onderwerpen helpen hen begrijpen waarom het praktiseren belangrijk is en zou moeten worden verwacht. Hier zijn een paar onderwerpen die helpen het gesprek beginnen:

* Het praktiseren vermindert de daadwerkelijke onderbreking wanneer een gebeurtenis voor echt gebeurt. Als een droge run uw locatie één uur per jaar inneemt, kan de werkelijke downtime van een echte gebeurtenis met enkele uren worden verminderd. Het is niet ongebruikelijk dat een hergebruik van een locatie acht uur of langer in beslag neemt. Door deze gebeurtenis te gebruiken kunt u vaak de hoeveelheid tijd verminderen elke fase neemt, en u kunt sneller terugkrijgen.
* De geplande onderbreking voor deze praktijklooppas kan met serverflarden, inventarisaanpassingen of om het even wat samenvallen die op een regelmatig programma zouden moeten worden gedaan.
* Andere scenario&#39;s gebruiken in plaats van dezelfde. Neem af en toe de tijd om een volledige terugvordering uit te voeren vanaf een vorige datum. Dit omvat dingen zoals het vinden van en het gebruiken van een gearchiveerd exemplaar van het gegevensbestand, die de code terugrollen om de datum aan te passen. Een gemakkelijkere zou een terugwinning van ontbroken plaatsing kunnen zijn, waar u eenvoudig terug naar vorige moet rollen begaat.
* Verifieer dat het terugwinningsproces eigenlijk werkt, soms kunnen de gearchiveerde gegevensbestanden corrupt worden. Op die manier zorgt het ervoor dat alles kan worden teruggewonnen en functioneel is. Het vinden en het herstellen van een oude OB vergt tijd, zou het moeten weten hoe lang dit deel van het proces kan zijn.
* Controleer of alle wijzigingen in configuraties zijn gedocumenteerd. Dit zorgt ervoor dat om het even welk terugwinning van een ouder gegevensbestand om het even welke nieuwe configuratieveranderingen moet functioneel zijn. Stel dat uw API-sleutel de afgelopen dagen is veranderd in uw betalingsprocessor. Door een goed veranderingsbeheerproces te hebben, maken het vinden van deze belangrijkste updates het proces gaan zoals gepland.

## DB-back-ups

Databaseback-ups moeten regelmatig zijn. Het is niet ongebruikelijk om uur-, dag-, week- en maandmomentopnamen te hebben. De back-ups moeten uiteindelijk worden verplaatst naar langdurige opslag. Deze opslag op lange termijn kan plaatsvinden wanneer het bedrijfs- of technologieteam genoeg tijd heeft verstreken dat een snel herstel van hen waarschijnlijk niet meer nodig is. Een herstel van langdurige opslag zorgt voor meer tijd voor het herstelproces. Daarom moet u zorgvuldig beslissen wanneer dit moet gebeuren. De gegevensbestandsteunen zouden moeten worden geautomatiseerd en niet op menselijke interactie vertrouwen. Dit verzekert u genoeg van hen om een veilig en voorspelbaar terugwinningsproces te verstrekken. Dit helpt ook bij alle forensische activiteiten, als een dergelijke activiteit noodzakelijk is, is haalbaar en betrouwbaar. Mogelijk hebt u forensisch onderzoek nodig nadat een misbruik is gedetecteerd, of wanneer u probeert vast te stellen wanneer een creditcard-frauduleuze activiteit heeft plaatsgevonden of zelfs wanneer iemand zich bij uw website heeft aangesloten. Er is geen limiet aan hoe u deze back-ups gebruikt, maar het hebben van een goede back-up is uw schaarste wanneer u deze daadwerkelijk nodig hebt.

Hieronder ziet u een voorbeeld van een beleid voor het bewaren van gegevens:

* Elke acht uur. De back-ups moeten gemakkelijk toegankelijk zijn.
* Dagelijkse back-ups gedurende de laatste zeven dagen en moeten gemakkelijk toegankelijk zijn. Een kopie ervan kan een kandidaat zijn voor verplaatsing naar een andere locatie.
* Wekelijkse back-ups voor de afgelopen vier weken kunnen u overwegen om offline te gaan.
* maandelijkse back-ups voor de afgelopen drie maanden zijn offline verplaatst.
* Oudere back-ups worden verplaatst naar opslag op lange termijn offsite.

## Infrastructuur als code

Deze methodologie betekent dat u hulpmiddelen en code op zijn plaats hebt om delen of de volledige infrastructuur voor uw project te herbouwen. Dit kan nodig zijn wanneer een server problemen ondervindt en buiten gebruik moet worden gesteld. Als u snel een nieuwe server online kunt brengen, implementeert u de code, maakt u PHP-, Nginx- of Apache-configuraties en wat dan ook automatisch minder downtime. Zelfs goed-gedocumenteerde stappen in een loopboek zijn gemakkelijker aan opstelling, om de stappen uit te voeren duurt veel langer. Overweeg ook de menselijke fout die kan optreden als er onder spanning een site staat waarop niet gereageerd kan worden.

## Secundaire database

Het gebruiken van een secundair gegevensbestand kan om een paar redenen nuttig zijn, zijn hier een paar:

* Warm stand-by als er een storing in de primaire schijf optreedt
* Toestaan voor aanvragen die klaar zijn voor de toepassing
* Laat mysqldump optreden en zorg ervoor dat normale transacties kunnen plaatsvinden zonder de database te vergrendelen
* Staat voor toegang tot gegevens van een externe gegevensbron toe zonder de Websites capaciteit te verminderen om informatie voor klantenverzoek te handelen.

De secundaire database kan als een `warm standby` worden gebruikt. Dit kan in spel komen wanneer u overweegt om van een primaire gegevensbestandmislukking terug te krijgen. Het bevorderen van het secundaire gegevensbestand aan primair is minder complex dan het herbouwen van en het herstellen van een gegevensbestand aan een pas gecreëerde instantie Mysql. Dit vermindert de daadwerkelijke onderbreking tijdens een terugwinningsverrichting.

Er is de kans om sommige verzoeken aan het secundaire gegevensbestand af te leiden. Als deze methode wordt gebruikt, wordt het maken van het secundaire gegevensbestand read-only voorgesteld. Door de toepassing van Adobe Commerce toe te staan om dit secundaire gegevensbestand voor leesverrichtingen te gebruiken helpt door enkele gelezen verzoeken te nemen en het secundaire gegevensbestand toe te staan om te antwoorden. Deze wijziging vertegenwoordigt echter slechts 30 tot 50% van alle aanvragen, maar elke belasting die u van de primaire database kunt verwijderen, is een overwinning.

## Creeer een plaatsingsplan dat een terugdraaiing omvat

Elke plaatsing zou een terugdraaiingsplan moeten omvatten. Ja, elke implementatie. Als je er voor plant, ben je nooit verrast en bent je klaar voor de slechte gebeurtenis. Soms kunnen de eenvoudigste code-updates om welke reden dan ook catastrofaal mislukken.

Overweeg dit ware verhaal van een team dat een klein, eenvoudig trekkingsverzoek toewees om een schemaverandering in het gegevensbestand uit te voeren. Aangezien de plaatsing van 1 minuut, aan 5, toen 10 ging, en het team meer ongerust werd. Wat zij tot op heden niet hebben gecontroleerd en overwogen, was elke discrepantie van de productiedatabank ten opzichte van de testdatabase. Zij hadden een gemeenschappelijke praktijk om alle klantengegevens te verwijderen wanneer het verfrissen van het opvoeren milieu met een exemplaar van productie. Dit betekende dat al hun tests en QA voorafgaand aan dit de plaatsing slechts een paar minuten om zou moeten vergen te voltooien. In werkelijkheid hadden ze meer dan 20 miljoen klanten en deze kleine schemawijziging duurde uitzonderlijk lang om te voltooien. Omdat ze geen idee hadden hoe lang dit zou duren, werden ze gedwongen om het mysql-proces te beëindigen en de implementatie terug te draaien.

Het voorbereiden van een terugschroeven van prijzenproces voor een plaatsing vergt slechts een paar notulen omdat het algemene proces zal gelijkaardig zijn. U moet echter wel de tijd nemen om precies te documenteren wat u wilt vastleggen en de HEAD van de git-opslagplaats terugzetten naar. U zou precies moeten documenteren welke db momentopname aan gebruik of waar te om huidige te vinden als dat altijd op de zelfde plaats is. Heb bepaalde tijden wanneer de status van de plaatsing moet worden besproken en wanneer de dingen automatisch van kracht worden. Als een implementatie bijvoorbeeld langer duurt dan 15 minuten, vraag dan aan de projectbeheerder en andere belanghebbenden of het verder moet. Het terugdraaiproces wordt echter automatisch uitgevoerd en alle belanghebbenden worden op de hoogte gebracht als het proces 45 minuten in beslag neemt, ongeacht of de projectmanager en architect aarzelen voor het project.

Zorg ervoor dat meerdere personen betrokken zijn bij het gehele proces en elke fase. Als ontwikkelaars op middenniveau het implementatieproces, de terugdraaiprocedure en de locatie van bestanden evalueren, is dit een goede manier om ze erbij te betrekken. Uiteindelijk zullen ze de stappen uitvoeren, zodat ze begrijpen dat het hele proces essentieel is voor succes op lange termijn. Zorg ervoor dat iedereen de bevoegdheid heeft om een plaatsing af te roepen. Het geven van die zegen aan uw team is empowerment en belonen. Als een ondergeschikte ontwikkelaar echt vindt dat er iets ontbreekt, dan moeten ze zich gedwongen voelen om op te komen en hun voorzichtigheid te laten horen. Laat de architect en projectmanagers hun angst bevestigen of verlichten. Het is belangrijk om een sterk team te hebben dat op zoek is naar het project en hun staat van dienst bij het bijhouden van foutloze implementaties.

## Toegang tot domeinnaambeheer, DMS, SSL, WAF controleren

Omdat de domeinnamen verlopen, DNS de verslagen per ongeluk kunnen worden gewijzigd, kunnen SSL de certificaten verlopen, en nog veel meer; ervoor zorgen u de capaciteit hebt om binnen te registreren en te verifiëren dat de connectiviteit vaak zou moeten gebeuren. Door deze eenvoudige controle elk kwartaal uit te voeren, hebt u er alle vertrouwen in dat u precies weet waar de zaken zich bevinden, met name in een noodsituatie. Ga er niet van uit dat uw DNS in uw registrar wordt beheerd om te achterhalen of het in Amazon is beheerd. Deze records worden niet vaak gebruikt, dus vergeten waar ze zich bevinden is een grote kans. Vertrouw geen geschreven documentatie voor gebruikersnamen en wachtwoorden alleen. Meld u aan bij elke configuratie en controleer of de configuraties die u zoekt, daar daadwerkelijk worden beheerd. Te vaak veranderen dingen tijdens management-omzet of bedrijfsovername en slechts één persoon weet wat er gebeurd is, omdat zij de update hebben uitgevoerd. Zij wisten niet dat u op een gedeeld woorddocument baseerde wat de plaats, de gebruikersbenaming en het wachtwoord is. Een controleproces vinden dat zinvol is voor u en uw organisatie, maar dit elke drie tot zes maanden doen is een goed uitgangspunt.

{{$include /help/_includes/hosting-related-links.md}}

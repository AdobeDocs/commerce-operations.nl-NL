---
title: De Adobe Commerce-software ophalen
description: Leer hoe u de Adobe Commerce-software downloadt.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# De Adobe Commerce-software ophalen

Je bent een van de 240.000 kooplieden wereldwijd die vertrouwen hebben in onze software voor e-handel. We hebben gegevens verzameld om u te helpen aan de slag te gaan met uw installatie.

## De software ophalen

Controleer de beschikbaarheid van opwindende nieuwe eigenschappen en versies en leer hoe u hen op onze [ pagina van de productbeschikbaarheid ](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/product-availability) kunt krijgen.

Raadpleeg de volgende tabel om aan de slag te gaan met de installatie van Adobe Commerce.

<table>
    <tbody>
        <tr>
            <th>Gebruikersbehoeften</th>
            <th>Beschrijving</th>
            <th>Installatie- en upgradestappen op hoog niveau</th>
            <th>Aan de slag-koppeling</th>
        </tr>
    <tr>
        <td><p>Integrator, packager</p></td>
        <td><p>Wil volledige controle over alle geïnstalleerde componenten, heeft toegang tot de toepassingsserver, hoogst technisch, zou Magento Open Source met andere componenten kunnen herverpakken.</p>
        </td>
        <td><ol><li>Creeert een Composer <em> project </em> dat de lijst van te gebruiken componenten bevat.</li>
            <li>Gebruikt Composer om pakketafhankelijkheden bij te werken; gebruikt <code>composer create-project</code> om het pakket Composer-metagegevens op te halen.</li>
            <li>Installeert de toepassing gebruikend de <a href="../advanced.md"> bevellijn </a>.</li>
        <li>Verbetert de toepassing en de uitbreidingen gebruikend de <a href="../../upgrade/implementation/perform-upgrade.md"> bevellijn </a>.</li></ol></td>
        <td><p><a href="../composer.md">De metapakket ophalen</a></p></td>
    </tr>
    <tr>
        <td><p>Medewerkende ontwikkelaar</p></td>
        <td><p>Hiermee wordt een bijdrage geleverd aan de codebase van de Magento Open Source, fouten in bestanden en wordt de toepassing aangepast. Zeer technisch, heeft hun eigen ontwikkelingsserver, begrijpt Composer en GitHub.</p>
            <p>U <em> kunt niet </em> de toepassing in een productiemilieu gebruiken.</p>
      <p>U moet bevorderen gebruikend <a href="../../upgrade/developer/git-installs.md"> Composer en de bevelen van het Git </a>.</p></td>
        <td><ol><li>Klonen de bewaarplaats GitHub.</li>
            <li>Gebruikt Composer om pakketafhankelijkheden bij te werken.</li>
            <li>Installeert de toepassing gebruikend <a href="../advanced.md"> bevellijn </a>.</li>
            <li>Verbetert de toepassing gebruikend <a href="../../upgrade/developer/git-installs.md"> Composer en de bevelen van het Git </a>.</li>
            <li>Past code onder de <code>app/code</code> folder aan.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clone the GitHub repository</a></p></td>
    </tr>
    </tbody>
</table>

## Nuttige informatie

Gebruik de koppelingen aan de linkerkant van de pagina om door onderwerpen in elk deel van de installatie te navigeren.

## Vereiste servermachtigingen

UNIX-systemen vereisen `root` privileges om software als een webserver, PHP, te installeren en te configureren. Als u deze software moet installeren, zorg ervoor u `root` toegang hebt.

Installeer *niet* de toepassing in de documentwortel van de Webserver als `root` gebruiker omdat de Webserver niet met die dossiers zou kunnen in wisselwerking staan.

U hebt `root` voorrechten nodig om de [ eigenaar van het dossiersysteem ](file-system/overview.md) tot stand te brengen en die eigenaar aan de groep van de Webserver toe te voegen. Met de eigenaar van het bestandssysteem kunt u `bin/magento` -opdrachten uitvoeren vanaf de opdrachtregel en snijtaken instellen, die taken voor u plannen.

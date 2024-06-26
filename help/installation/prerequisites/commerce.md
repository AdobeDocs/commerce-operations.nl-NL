---
title: De Adobe Commerce-software ophalen
description: Leer hoe u de Adobe Commerce-software downloadt.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# De Adobe Commerce-software ophalen

Je bent een van de 240.000 kooplieden wereldwijd die vertrouwen hebben in onze software voor e-handel. We hebben gegevens verzameld om u te helpen aan de slag te gaan met uw installatie.

## De software ophalen

Controleer de beschikbaarheid van spannende nieuwe functies en releases en leer hoe u deze op onze [pagina over productbeschikbaarheid](https://devdocs.magento.com/release/availability.html).

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
        <td><ol><li>Maakt een Composer <em>project</em> die de lijst met te gebruiken componenten bevat.</li>
            <li>Gebruikt Composer om pakketafhankelijkheden bij te werken; gebruikt <code>composer create-project</code> om de Composer-metapakket te verkrijgen.</li>
            <li>De toepassing wordt geïnstalleerd met de <a href="../advanced.md">opdrachtregel</a>.</li>
        <li>Hiermee werkt u de toepassing en extensies bij met de  <a href="../../upgrade/implementation/perform-upgrade.md">opdrachtregel</a>.</li></ol></td>
        <td><p><a href="../composer.md">De metapakket ophalen</a></p></td>
    </tr>
    <tr>
        <td><p>Medewerkende ontwikkelaar</p></td>
        <td><p>Hiermee wordt een bijdrage geleverd aan de codebase van de Magento Open Source, fouten in bestanden en wordt de toepassing aangepast. Zeer technisch, heeft hun eigen ontwikkelingsserver, begrijpt Composer en GitHub.</p>
            <p>U <em>kan</em> de toepassing gebruiken in een productieomgeving.</p>
      <p>U moet een upgrade uitvoeren met <a href="../../upgrade/developer/git-installs.md">Opdrachten Composer en Git</a>.</p></td>
        <td><ol><li>Klonen de bewaarplaats GitHub.</li>
            <li>Gebruikt Composer om pakketafhankelijkheden bij te werken.</li>
            <li>De toepassing installeren met <a href="../advanced.md">opdrachtregel</a>.</li>
            <li>Hiermee wordt de toepassing bijgewerkt met <a href="../../upgrade/developer/git-installs.md">Opdrachten Composer en Git</a>.</li>
            <li>Hiermee wordt code onder de <code>app/code</code> directory.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clone the GitHub repository</a></p></td>
    </tr>
    </tbody>
</table>

## Nuttige informatie

Gebruik de koppelingen aan de linkerkant van de pagina om door onderwerpen in elk deel van de installatie te navigeren.

## Vereiste servermachtigingen

UNIX-systemen vereisen `root` rechten om software zoals een webserver, PHP, te installeren en te configureren. Als u deze software moet installeren, controleert u of u `root` toegang.

Do *niet* installeer de toepassing in de webserverhoofdmap als de `root` omdat de webserver mogelijk niet kan communiceren met deze bestanden.

U hebt `root` rechten om de [eigenaar van bestandssysteem](file-system/overview.md) en voeg die eigenaar toe aan de webservergroep. U gebruikt de eigenaar van het bestandssysteem om het bestand uit te voeren `bin/magento` opdrachten van de opdrachtregel en van insteltaken, die taken voor u plannen.

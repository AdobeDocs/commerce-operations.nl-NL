---
title: Configuratie van zoekmachine
description: Configureer een zoekmachine met Adobe Commerce en Magento Open Source.
source-git-commit: 66681f06c15907a5d25e71005c27785f0745ed63
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# Configuratie van zoekmachine

In deze sectie worden de minimale instellingen besproken die u moet kiezen om Elasticsearch of OpenSearch met Adobe Commerce en Magento Open Source te testen. Vanaf versies 2.4.4 en 2.4.3-p2, alle gebieden geëtiketteerd **Elasticsearch** is ook van toepassing op OpenSearch.

Voor meer informatie over het configureren van uw zoekmachine raadpleegt u de [Handboek](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## De zoekfunctie configureren vanuit de beheerder

Om uw systeem te vormen om Elasticsearch of OpenSearch te gebruiken:

1. Meld u als beheerder aan bij de beheerder.
1. Klikken **Winkels** > Instellingen > **Configuratie** > **Catalogus** > **Catalogus** > **Catalogus zoeken**.
1. Van de **Zoekmachine** selecteert u de bijbehorende versie van uw zoekprogramma. Als u OpenSearch gebruikt, moet u Elasticsearch7 selecteren.

   De volgende lijst maakt een lijst van de vereiste configuratieopties om de verbinding met Handel te vormen en te testen.
Tenzij u de serverinstellingen van uw zoekmachine hebt gewijzigd, werken de standaardwaarden beter. Ga verder met de volgende stap.

   | Option | Beschrijving |
   |--- |--- |
   | **Hostnaam Elasticsearch-server** | Voer de volledig gekwalificeerde hostnaam of het IP-adres in van de computer waarop Elasticsearch of OpenSearch wordt uitgevoerd.<br>Adobe Commerce op cloudinfrastructuur: Haal deze waarde op van uw integratiesysteem. |
   | **Elasticsearch-serverpoort** | Voer de proxypoort van de webserver in. De standaardwaarde is 9200<br>Adobe Commerce op cloudinfrastructuur: Haal deze waarde op van uw integratiesysteem. |
   | **Elasticsearch-indexvoorvoegsel** | Voer het voorvoegsel van de index van het zoekprogramma in. Als u één instantie voor meer dan één installatie van de Handel (het Opvoeren en de milieu&#39;s van de Productie) gebruikt, moet u een uniek voorvoegsel voor elke installatie specificeren. Anders kunt u het standaardvoorvoegsel magento2 gebruiken. |
   | **Elasticsearch HTTP-auteur inschakelen** | Klikken **Ja** alleen als u verificatie hebt ingeschakeld voor uw zoekmachineserver. Geef in dat geval een gebruikersnaam en wachtwoord op in de opgegeven velden. |

1. Klikken **Verbinding testen**.

   Monsterrespons:

   ![succes](../../assets/configuration/elastic_test-success.png)

   Doorgaan met:

   - [Apache configureren voor uw zoekmachine](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Nginx voor uw zoekmachine configureren](../../installation/prerequisites/search-engine/configure-nginx.md)

   of u ziet:

   ![mislukt](../../assets/configuration/elastic_test-fail.png)

Zo ja, probeer dan het volgende:

- Zorg ervoor dat de zoekmachine-server actief is.
- Als de server op een verschillende gastheer van Handel is, login aan de server van de Handel en pingel de gastheer van de onderzoeksmotor. Los de kwesties van de netwerkconnectiviteit op en test opnieuw de verbinding.
- Onderzoek het bevelvenster waarin u Elasticsearch of OpenSearch voor stapelsporen en uitzonderingen begon. U moet deze oplossen voordat u verdergaat. Zorg er met name voor dat u de zoekfunctie hebt gestart als een gebruiker met `root` rechten.
- Controleer of [UNIX-firewall en SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) zijn beide uitgeschakeld, of stel regels in waarmee je zoekmachine en handel met elkaar kunnen communiceren.
- Controleer de waarde van de **Hostnaam Elasticsearch-server** veld. Controleer of de server beschikbaar is. U kunt het IP-adres van de server proberen.
- Gebruik de `netstat -an | grep <listen-port>` bevel om te verifiëren dat de haven in wordt gespecificeerd **Elasticsearch-serverpoort** wordt niet door een ander proces gebruikt.

   Als u bijvoorbeeld wilt zien of de zoekmachine op de standaardpoort wordt uitgevoerd, gebruikt u de volgende opdracht:

   ```bash
   netstat -an | grep 9200
   ```

   Als het op haven 9200 loopt, toont het gelijkaardig aan het volgende:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Zoekopdracht in catalogus opnieuw indexeren en de cache van de volledige pagina vernieuwen

Nadat u de configuratie van de zoekmachine hebt gewijzigd, moet u de zoekindex van de catalogus opnieuw indexeren en de volledige paginacache vernieuwen met de opdrachtregel of de beheerderslijn.

De cache vernieuwen met behulp van Admin:

1. Klik in Beheer op **Systeem** > **Cachebeheer**.
1. Schakel het selectievakje in naast **Paginacache**.
1. Van de **Handelingen** lijst in de rechterbovenhoek klikt u op **Vernieuwen**.

   ![cachebeheer](../../assets/configuration/refresh-cache.png)

De cache reinigen met de opdrachtregel: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Herindexeren met behulp van de opdrachtregel:

1. Meld u aan bij de Commerce-server als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Voer een van de volgende opdrachten in:

   Voer de volgende opdracht in om alleen de zoekindex van de catalogus opnieuw te indexeren:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Voer de volgende opdracht in om alle indexen opnieuw te indexeren:

   ```bash
   bin/magento indexer:reindex
   ```

1. Wacht tot het opnieuw indexeren voltooit.

   >[!INFO]
   >
   >In tegenstelling tot de cache worden indexeerders bijgewerkt door een uitsnijdtaak. Controleer of [uitsnijden is ingeschakeld](../cli/configure-cron-jobs.md) voordat u de zoekfunctie gaat gebruiken.


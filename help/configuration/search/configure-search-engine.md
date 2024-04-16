---
title: Configuratie van zoekmachine
description: Configureer een zoekmachine voor on-premisse implementaties van Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Configuratie van zoekmachine

Deze sectie bespreekt de minimummontages die u moet verkiezen om Elasticsearch of OpenSearch met plaatsingen op-gebouw van Adobe Commerce te testen.

>[!TIP]
>
>In versies 2.4.4 en 2.4.3-p2, alle gebieden geëtiketteerd **Elasticsearch** is ook van toepassing op OpenSearch.
>Toen de steun voor Elasticsearch 8.x in versie 2.4.6 werd geïntroduceerd, werden de nieuwe etiketten gecreeerd om tussen Elasticsearch en configuraties te onderscheiden OpenSearch.

Voor meer informatie over het configureren van uw zoekmachine raadpleegt u de [Handboek](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## De zoekfunctie configureren vanuit de beheerder

>[!TIP]
>
>Voor instructies voor het upgraden naar een nieuwe versie van de zoekmachine raadpleegt u [upgradevoorwaarden](../../upgrade/prepare/prerequisites.md).

Om uw systeem te vormen om Elasticsearch of OpenSearch te gebruiken:

1. Meld u als beheerder aan bij de beheerder.
1. Klikken **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Van de **[!UICONTROL Search Engine]** selecteert u de bijbehorende versie van uw zoekprogramma.

   In de volgende tabel staan de vereiste opties voor het configureren en testen van de verbinding met Commerce. Tenzij u de serverinstellingen van uw zoekmachine hebt gewijzigd, werken de standaardwaarden beter. Ga verder met de volgende stap.

   | Optie | Beschrijving |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Voer de volledig gekwalificeerde hostnaam of het IP-adres in van de computer waarop de Elasticsearch of OpenSearch wordt uitgevoerd.<br>Adobe Commerce op cloudinfrastructuur: haal deze waarde van uw integratiesysteem. |
   | **[!UICONTROL Server Port]** | Voer de proxypoort van de webserver in. De standaardwaarde is 9200<br>Adobe Commerce op cloudinfrastructuur: haal deze waarde van uw integratiesysteem. |
   | **[!UICONTROL Index Prefix]** | Voer het voorvoegsel van de index van het zoekprogramma in. Als u één exemplaar voor meer dan één installatie van Commerce (het Opvoeren en de milieu&#39;s van de Productie) gebruikt, moet u een uniek voorvoegsel voor elke installatie specificeren. Anders kunt u het standaardvoorvoegsel magento2 gebruiken. |
   | **[!UICONTROL Enable HTTP Auth]** | Klikken **[!UICONTROL Yes]** alleen als u verificatie hebt ingeschakeld voor uw zoekmachineserver. Geef in dat geval een gebruikersnaam en wachtwoord op in de opgegeven velden. |
   | **[!UICONTROL Server Timeout]** | Voer de hoeveelheid tijd (in seconden) in die moet worden gewacht wanneer u probeert verbinding te maken met de Elasticsearch of de OpenSearch-server. |

1. Klik op **[!UICONTROL Test Connection]**.

   Monsterrespons:

   ![succes](../../assets/configuration/elastic_test-success.png)

   Doorgaan met:

   - [Apache configureren voor uw zoekmachine](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Nginx voor uw zoekmachine configureren](../../installation/prerequisites/search-engine/configure-nginx.md)

   of u ziet:

   ![mislukt](../../assets/configuration/elastic_test-fail.png)

Zo ja, probeer dan het volgende:

- Zorg ervoor dat de zoekmachine-server actief is.
- Als de server zich op een andere host dan Commerce bevindt, meldt u zich aan bij de Commerce-server en pingelt u de host van de zoekmachine. Los de kwesties van de netwerkconnectiviteit op en test opnieuw de verbinding.
- Onderzoek het bevelvenster waarin u Elasticsearch of OpenSearch voor stapelsporen en uitzonderingen begon. U moet deze oplossen voordat u verdergaat. Zorg er met name voor dat u de zoekfunctie hebt gestart als een gebruiker met `root` rechten.
- Controleer of [UNIX-firewall en SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) zijn beide uitgeschakeld, of stel regels in waarmee je zoekmachine en Commerce met elkaar kunnen communiceren.
- Controleer de waarde van de **[!UICONTROL Server Hostname]** veld. Controleer of de server beschikbaar is. U kunt in plaats daarvan het IP-adres van de server proberen.
- Gebruik de `netstat -an | grep <listen-port>` bevel om te verifiëren dat de haven in wordt gespecificeerd **[!UICONTROL Server Port]** wordt niet door een ander proces gebruikt.

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

1. Klik in Beheer op **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Schakel het selectievakje in naast **[!UICONTROL Page Cache]**.
1. Van de **[!UICONTROL Actions]** lijst in de rechterbovenhoek klikt u op **Vernieuwen**.

   ![cachebeheer](../../assets/configuration/refresh-cache.png)

De cache reinigen met de opdrachtregel: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Herindexeren met de opdrachtregel:

1. Meld u aan bij uw Commerce-server als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
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

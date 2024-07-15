---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Controleren of communicatie veilig is

Deze sectie bespreekt twee manieren om te verifiëren dat de Basisauthentificatie van HTTP werkt:

* Een `curl` -opdracht gebruiken om te verifiëren dat u een gebruikersnaam en wachtwoord moet invoeren om de clusterstatus op te halen
* HTTP Basic-verificatie configureren in de beheerfunctie

## Een opdracht `curl` gebruiken om de clusterstatus te verifiëren

Voer de volgende opdracht in:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Bijvoorbeeld, als u het bevel op de server van de onderzoeksmotor ingaat en uw volmacht gebruikt haven 8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

Het volgende bericht geeft aan dat verificatie is mislukt:

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Probeer nu het volgende bevel:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Bijvoorbeeld:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Dit keer slaagt het bevel met een bericht gelijkend op het volgende:

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## HTTP Basic-verificatie configureren in de beheerfunctie

Voer de zelfde taken uit zoals die in [ de motorconfiguratie van het Onderzoek ](../configuration/search/configure-search-engine.md) *worden besproken behalve* klik **[!UICONTROL Yes]** van de **[!UICONTROL Enable HTTP Auth]** lijst en ga uw gebruikersbenaming en wachtwoord op de verstrekte gebieden in.

Klik op **[!UICONTROL Test Connection]** om te controleren of het werkt en klik vervolgens op **[!UICONTROL Save Config]** .

U moet de cache leegmaken en opnieuw indexeren voordat u verdergaat.

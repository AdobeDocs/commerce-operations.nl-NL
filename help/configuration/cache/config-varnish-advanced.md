---
title: Geavanceerde Varnish-configuratie
description: Leer hoe u geavanceerde Varnish-functies voor Adobe Commerce configureert, zoals health checks, Grace en saint-modi. Ontdek de optimalisatietechnieken van VCL.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Geavanceerde Varnish-configuratie

Varnish biedt verschillende functies die voorkomen dat klanten te maken krijgen met lange vertragingen en time-outs wanneer de Commerce-server niet goed werkt. Deze functies kunnen worden geconfigureerd in het `default.vcl` -bestand. Dit onderwerp beschrijft de toevoegingen die Commerce in het VCL (de Taal van de Configuratie van de Varnish) dossier verstrekt u van Admin downloadt.

Zie het [&#x200B; Handboek van de Verwijzing van de Varnish &#x200B;](https://varnish-cache.org/docs/index.html) voor details over het gebruiken van de Taal van de Configuratie van de Varnish.

## Health check

Met de functie voor de Varnish-health check wordt de Commerce-server opgezocht om te bepalen of deze tijdig reageert. Als het normaal reageert, wordt nieuwe inhoud opnieuw gegenereerd nadat de periode Tijd tot live (TTL) is verlopen. Als dat niet het geval is, dient Varnish altijd de inhoud van de schaal.

Commerce definieert de volgende standaardhealth check:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Deze health check roept om de 5 seconden het `pub/health_check.php` -script aan. Dit script controleert de beschikbaarheid van de server, elke database en Redis (indien geïnstalleerd). Het script moet een reactie binnen 2 seconden retourneren. Wanneer het script bepaalt dat een van deze bronnen is ingedrukt, wordt een 500 HTTP-foutcode geretourneerd. Als deze foutcode wordt ontvangen in zes van de tien pogingen, wordt de backend als ongezond beschouwd.

Het script `health_check.php` bevindt zich in de map `pub` . Als uw Commerce-hoofdmap `pub` is, moet u het pad in de parameter `url` wijzigen van `/pub/health_check.php` in `health_check.php` .

Voor meer informatie, zie [&#x200B; Varnish gezondheidscontroles &#x200B;](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) documentatie.

## Respijtmodus

Met de modus Grace kan Varnish een object in cache boven de TTL-waarde houden. Varnish kan dan de verlopen (verouderd) inhoud dienen terwijl het een nieuwe versie haalt. Dit verbetert de stroom van verkeer en vermindert ladingstijden. Het wordt in de volgende situaties gebruikt:

- Als de Commerce-backend gezond is, maar een aanvraag langer duurt dan normaal
- Als de Commerce backend niet gezond is.

De subroutine `vcl_hit` definieert hoe Varnish reageert op een aanvraag voor objecten die in de cache zijn geplaatst.

### Als de Commerce-backend gezond is

Wanneer uit de gezondheidscontroles blijkt dat de Commerce-backend gezond is, controleert Varnish of de tijd in de respijtperiode blijft. De standaardgraadperiode is 300 seconden, maar een handelaar kan de waarde van Admin plaatsen zoals die in [&#x200B; wordt beschreven vormt Commerce om Varnish &#x200B;](configure-varnish-commerce.md) te gebruiken. Als de respijtperiode niet is verlopen, levert Varnish de schaalinhoud en wordt het object asynchroon vernieuwd vanaf de Commerce-server. Als de respijtperiode is verlopen, wordt de verouderde inhoud door Varnish weergegeven en wordt het object synchroon vernieuwd vanaf de Commerce-achtergrond.

De maximumhoeveelheid tijd dat Varnish een stapelvoorwerp dient is de som respijtperiode (300 seconden door gebrek) en de waarde van TTL (86400 seconden door gebrek).

Als u de standaardrespijtperiode wilt wijzigen vanuit het `default.vcl` -bestand, bewerkt u de volgende regel in de `vcl_hit` -subroutine:

```conf
if (obj.ttl + 300s > 0s) {
```

### Als de Commerce-backend niet gezond is

Als de Commerce-backend niet reageert, wordt door Varnish 3 dagen (of zoals gedefinieerd in `beresp.grace`) en de resterende TTL (die standaard één dag is) opgeslagen vanaf het cachegeheugen, tenzij de inhoud in de cache handmatig wordt gewist.

## Sint-modus

In de modus Saint zijn ongezonde achtergronden uitgesloten voor een configureerbare hoeveelheid tijd. Als gevolg hiervan kunnen ongezonde backends geen verkeer dienen wanneer Varnish als taakverdelingsmechanisme wordt gebruikt. U kunt de modus Sint gebruiken met de modus Grijswaarden, zodat ongezonde back-endservers op een complexe manier kunnen worden afgehandeld. Als bijvoorbeeld een back-endserver ongezond is, kunnen pogingen opnieuw worden gerouteerd naar een andere server. Als alle andere servers zijn uitgevallen, dienen ze objecten in het cachegeheugen op te slaan. De back-end hosts en black-outperiodes in de modus Beveiliging worden gedefinieerd in het `default.vcl` -bestand.

De modus Saint kan ook worden gebruikt wanneer Commerce-instanties afzonderlijk offline worden gebruikt voor het uitvoeren van onderhouds- en upgradetaken zonder dat dit van invloed is op de beschikbaarheid van de Commerce-site.

### Voorwaarden voor de modus Sint

Eén computer aanwijzen als primaire installatie. Installeer op deze computer de hoofdinstantie van Commerce, mySQL-database en Varnish.

Op alle andere computers moet de Commerce-instantie toegang hebben tot de mySQL-database van de primaire computer. De secundaire machines moeten ook toegang hebben tot de bestanden van het primaire Commerce-exemplaar.

U kunt het versieren van statische bestanden ook op alle computers uitschakelen. Dit kan van Admin onder **worden betreden Slaat** > Montages > **Configuratie** > **Geavanceerd** > **de Montages van de Ontwikkelaar** > **de Statische Montages van Dossiers** > **Onderteken Statische Dossiers** = **Nr**.

Tot slot moeten alle Commerce-instanties zich in de productiemodus bevinden. Voordat Varnish begint, wist u de cache bij elke instantie. In Admin, ga **van het 0&rbrace; Systeem &lbrace;> Hulpmiddelen >** het Beheer van het Geheime voorgeheugen **en klik** het Geheime voorgeheugen van Magento **duwen.** U kunt ook de volgende opdracht uitvoeren om de cache te wissen:

```bash
bin/magento cache:flush
```

### Installatie

Saint mode maakt geen deel uit van het grootste Varnish-pakket. Het is een aparte versie `vmod` die moet worden gedownload en geïnstalleerd. Dientengevolge, moet u Varnish van bron opnieuw compileren, zoals die in de [&#x200B; installatieinstructies &#x200B;](https://varnish-cache.org/docs/index.html) voor uw versie van Varnish wordt beschreven.

Nadat u opnieuw compileert, kunt u de Sint-modusmodule installeren. Voer in het algemeen de volgende stappen uit:

1. Verkrijg de broncode van [&#x200B; Varnish modules &#x200B;](https://github.com/varnish/varnish-modules). Kloont de Git-versie (hoofdversie) omdat de 0.9.x-versie een broncodecout bevat.
1. Bouw de broncode met autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Zie [&#x200B; de moduleinzameling van de Varnish &#x200B;](https://github.com/varnish/varnish-modules) voor informatie over het installeren van de Saint wijzemodule.

### Voorbeeld-VCL-bestand

Het volgende codevoorbeeld toont de code die aan uw VCL- dossier moet worden toegevoegd om veiligheidswijze toe te laten. Plaats de `import` -instructies en `backend` -definities boven in het bestand.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```

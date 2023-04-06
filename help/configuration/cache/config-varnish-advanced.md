---
title: Geavanceerde Varnish-configuratie
description: Veelzijdige functies configureren, zoals health check, respijtmodi en verfmodi.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---


# Geavanceerde Varnish-configuratie

Varnish verstrekt verscheidene eigenschappen die klanten verhinderen lange vertragingen en onderbrekingen te ervaren wanneer de server van de Handel niet behoorlijk functioneert. Deze eigenschappen kunnen in worden gevormd `default.vcl` bestand. Dit onderwerp beschrijft de toevoegingen die de Handel in het VCL (de Taal van de Configuratie van de Varnish) dossier verstrekt u van Admin downloadt.

Zie de [Varnish Reference Manual](https://varnish-cache.org/docs/6.3/reference/index.html) voor details over het gebruiken van de Taal van de Configuratie van de Varnish.

## Health check

Met de functie Varnish health check wordt de Commerce-server opgevraagd of deze tijdig reageert. Als het normaal reageert, wordt nieuwe inhoud opnieuw gegenereerd nadat de periode Tijd tot live (TTL) is verlopen. Als dat niet het geval is, dient Varnish altijd de inhoud van de schaal.

De handel bepaalt de volgende standaardgezondheidscontrole:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Elke 5 seconden, roept deze gezondheidscontrole `pub/health_check.php` script. Dit script controleert de beschikbaarheid van de server, elke database en Redis (indien geïnstalleerd). Het script moet een reactie binnen 2 seconden retourneren. Wanneer het script bepaalt dat een van deze bronnen is ingedrukt, wordt een 500 HTTP-foutcode geretourneerd. Als deze foutcode wordt ontvangen in zes van de tien pogingen, wordt de backend als ongezond beschouwd.

De `health_check.php` het script bevindt zich in het dialoogvenster `pub` directory. Als de hoofdmap van de handel `pub`en zorg ervoor dat u het pad in het dialoogvenster `url` parameter van `/pub/health_check.php` tot `health_check.php`.

Zie voor meer informatie de [Varnish health checks](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) documentatie.

## Respijtmodus

Met de modus Grace kan Varnish een object in cache boven de TTL-waarde houden. Varnish kan dan de verlopen (verouderd) inhoud dienen terwijl het een nieuwe versie haalt. Dit verbetert de stroom van verkeer en vermindert ladingstijden. Het wordt in de volgende situaties gebruikt:

- Wanneer de achtergrond van de Handel gezond is maar een verzoek langer duurt dan normaal
- Als de terugval van de Handel niet gezond is.

De `vcl_hit` subroutine definieert hoe Varnish reageert op een aanvraag voor objecten die in cache zijn geplaatst.

### Wanneer de steun van de Handel gezond is

Wanneer uit de gezondheidscontroles blijkt dat de handelsachterstand gezond is, controleert Varnish of de tijd in de respijtperiode blijft. De standaardrespijtperiode is 300 seconden, maar een handelaar kan de waarde van Admin instellen zoals beschreven in [Handel configureren voor gebruik van Varnish](configure-varnish-commerce.md). Als de respijtperiode niet is verlopen, levert Varnish de schaalinhoud en vernieuwt asynchroon het object van de Commerce-server. Als de respijtperiode is verlopen, levert Varnish de schaalinhoud en wordt het object synchroon vernieuwd vanaf de achtergrond van de Handel.

De maximumhoeveelheid tijd dat Varnish een stapelvoorwerp dient is de som respijtperiode (300 seconden door gebrek) en de waarde van TTL (86400 seconden door gebrek).

De standaardrespijtperiode wijzigen vanuit de `default.vcl` bestand, bewerkt u de volgende regel in het dialoogvenster `vcl_hit` subroutine:

```conf
if (obj.ttl + 300s > 0s) {
```

### Wanneer de steun van de Handel niet gezond is

Als de achtergrond van de Handel niet antwoordt, dient Varnish statische inhoud van geheim voorgeheugen drie dagen (of zoals bepaald in `beresp.grace`) plus de resterende TTL (die door gebrek één dag is), tenzij de caching inhoud manueel wordt gezuiverd.

## Sint-modus

In de modus Saint zijn ongezonde achtergronden uitgesloten voor een configureerbare hoeveelheid tijd. Als gevolg hiervan kunnen ongezonde backends geen verkeer dienen wanneer Varnish als taakverdelingsmechanisme wordt gebruikt. U kunt de modus Sint gebruiken met de modus Grijswaarden, zodat ongezonde back-endservers op een complexe manier kunnen worden afgehandeld. Als bijvoorbeeld een back-endserver ongezond is, kunnen pogingen opnieuw worden gerouteerd naar een andere server. Als alle andere servers zijn uitgevallen, dienen ze objecten in het cachegeheugen op te slaan. De back-end hosts en de time-outperiode voor de modus Afbeelding worden gedefinieerd in het dialoogvenster `default.vcl` bestand.

De wijze van Saint kan ook worden gebruikt wanneer de instanties van de Handel individueel offline worden genomen om onderhouds en verbeteringstaken uit te voeren zonder de beschikbaarheid van de plaats van de Handel te beïnvloeden.

### Voorwaarden voor de modus Sint

Eén computer aanwijzen als primaire installatie. Installeer op deze computer de belangrijkste instantie van Handel, mijnSQL-database en Varnish.

Op alle andere machines, moet de instantie van de Handel toegang hebben tot het primaire gegevensbestand mySQL van de machine. De secundaire machines moeten ook toegang hebben tot de bestanden van de primaire instantie van de Handel.

U kunt het versieren van statische bestanden ook op alle computers uitschakelen. Dit is toegankelijk via de beheerder onder **Winkels** > Instellingen > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **Instellingen Statische bestanden** > **Statische bestanden ondertekenen** = **Nee**.

Tot slot moeten alle instanties van de Handel in productiemodus zijn. Voordat Varnish begint, wist u de cache bij elke instantie. Ga in Beheer naar **Systeem** > Gereedschappen > **Cachebeheer** en klik op **Magento-cache leegmaken**. U kunt ook de volgende opdracht uitvoeren om de cache te wissen:

```bash
bin/magento cache:flush
```

### Installatie

De Saint-mode maakt geen deel uit van het grootste Varnish-pakket. Het is een apart versienummer `vmod` die moeten worden gedownload en geïnstalleerd. Dientengevolge, zou u Varnish van bron, zoals die in de volgende artikelen wordt beschreven opnieuw moeten compileren:

- [Varnish 6.4 installeren](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Varnish 6.0 installeren](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Nadat u opnieuw compileert, kunt u de Sint-modusmodule installeren. Voer in het algemeen de volgende stappen uit:

1. De broncode ophalen uit [Varnish modules](https://github.com/varnish/varnish-modules). Kloont de Git-versie (master versie) omdat de 0.9.x-versie een broncodefout bevat.
1. Bouw de broncode met autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Zie [Verzameling van de module Varnish](https://github.com/varnish/varnish-modules) voor informatie over de installatie van de module Saint Mode.

### Voorbeeld-VCL-bestand

Het volgende codevoorbeeld toont de code die aan uw VCL- dossier moet worden toegevoegd om veiligheidswijze toe te laten. Plaats de `import` instructies en `backend` definities boven aan het bestand.

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

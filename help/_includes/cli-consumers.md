---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# CLI-opties voor gebruikers in een wachtrij met berichten

| Naam | Beschrijving | Waarde | Vereist |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Hiermee bepaalt u of consumenten op een bericht in de wachtrij wachten. | 1 - Ja, 0 - Nee | Nee |

* `0`: De consumenten verwerken beschikbare berichten in de rij, sluiten de verbinding van TCP, en eindigen. De consumenten wachten niet op extra berichten om de rij in te gaan, zelfs als het aantal verwerkte berichten minder dan is `--max_messages` waarde die tijdens het starten van de consument is opgegeven.

* `1`: De consumenten blijven berichten van de berichtrij verwerken tot het bereiken van het maximumaantal berichten (de waarde voor `--max_messages` op de `queue:consumers:start` bevel) alvorens de verbinding van TCP te sluiten en het consumentenproces te beëindigen. Als de wachtrij wordt leeggemaakt voordat de wachtrij wordt bereikt `--max_messages` de consument wacht op meer berichten . Als u workers gebruikt om consumenten te runnen in plaats van een uitsnijdtaak, stelt u deze variabele in op `1`.

>[!WARNING]
>
>De `--consumers-wait-for-messages` optie is een globale optie en kan niet afzonderlijk voor elke consument worden gevormd.

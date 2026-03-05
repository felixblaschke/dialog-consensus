# dialog-consensus

Skill fuer kollaborative Dialoge zwischen mehreren Modellen mit gemeinsamem Ziel, chronologischem Protokoll und laufendem Konsens. Die Modelle agieren als Expert Board: jede Loesungsoption wird explizit mit Pro- und Contra-Argumenten bewertet, optional aus der Perspektive einer zugewiesenen Persona.

## Befehle

| Befehl                    | Beschreibung                                                                                                                                          |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `dialog <file>`           | Ziel klären und Dialog-Datei erstellen/öffnen. Keine Analyse, nur Zieldefinition.                                                                     |
| `talk <file> [<Persona>]` | Modellbeitrag mit Pro/Contra-Bewertung schreiben und Konsens aktualisieren. Optionale Persona (z. B. `Du bist ein UX Experte`) lenkt die Perspektive. |
| `talkuser <file>`         | Nutzerfeedback ins Protokoll aufnehmen (kein Konsens-Update).                                                                                         |
| `talksummary <file>`      | Zusammenfassung ausgeben: Einigkeit, Uneinigkeit, mögliche Nutzer-Impulse. Keine Dateiänderung.                                                       |

## Typischer Ablauf

1. `dialog bugfix123.md` — Ziel iterativ klären
2. `talk bugfix123.md` — erste Analyse
3. `talk bugfix123.md Du bist ein Security Experte` — weitere Perspektive
4. `talksummary bugfix123.md` — Stand prüfen
5. `talkuser bugfix123.md` — eigenes Feedback einbringen
6. `talk bugfix123.md` — Dialog fortführen

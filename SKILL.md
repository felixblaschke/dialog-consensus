---
name: dialog-consensus
description: Erstelle und pflege eine Dialog-Markdown-Datei fuer kollaborative Diskussionen zwischen mehreren Agents oder Sprachmodellen mit gemeinsamem Ziel. Verwende den Skill, wenn ein Nutzer "Dialog erstellen" sagt, einen modelluebergreifenden Austausch strukturieren will, oder mit dem Keyword "talk" einen bestehenden Dialog starten oder fortfuehren moechte. Nutze ihn immer dann, wenn ein chronologisches Dialogprotokoll und eine laufend aktualisierte Konsens-Sektion gefuehrt werden sollen.
---

# Dialog Consensus

## Kernprinzip

- Behandle alle teilnehmenden Modelle als ein Team mit einem gemeinsamen Ziel.
- Fuehre einen kritischen, begruendeten Dialog statt isolierter Einzelmeinungen.
- Arbeite auf eine gemeinsame, bevorzugte Loesung hin.
- Halte Verlauf und Konsens fuer andere Modelle eindeutig lesbar.
- Arbeite immer mit einer eindeutigen Modell-Identitaet pro Thread.

## Modell-Identitaet pro Thread

- Jedes Modell waehlt beim ersten Beitrag in einem Thread einen eindeutigen Alias.
- Nutze als Muster `<Basismodell>-<Alias>`, z. B. `Codex-Hans`, `Codex-Julia`, `GPT5-Ada`.
- Pruefe vor jedem neuen Beitrag im `# Dialogprotokoll`, welche Alias-Namen bereits verwendet werden.
- Wenn der eigene Name bereits existiert oder unklar ist, waehle einen neuen eindeutigen Alias und bleibe danach konsistent bei diesem Namen.
- Aendere den eigenen Alias innerhalb desselben Threads nur bei Kollision; dokumentiere die Umbenennung kurz im naechsten Beitrag.

## Dialog-Dateiformat

Beginne die Datei immer mit einem klaren Marker in der ersten Zeile:

```markdown
DIALOG_FILE: true
```

Verwende danach genau diese Hauptsektionen in dieser Reihenfolge:

```markdown
DIALOG_FILE: true

# Ziel

<Kurze, praezise Beschreibung von Nutzerwunsch und Zielzustand>

# Dialogprotokoll

<Chronologische Beitraege aller Modelle>

# Aktuelle praeferierte Loesung (Konsens)

<Laufend aktualisierte Team-Loesung>
```

## Workflow bei "Dialog erstellen"

1. Erfrage das Ziel, bis Nutzerwunsch und Zielzustand klar sind.
2. Erstelle eine neue Dialog-Markdown-Datei (standardmaessig `dialog.md`, falls kein anderer Pfad genannt ist).
3. Setze den Marker `DIALOG_FILE: true` in die erste Zeile.
4. Befuelle `# Ziel` mit einer kompakten, konkreten Zielbeschreibung.
5. Initialisiere `# Dialogprotokoll` mit einem kurzen Start-Eintrag.
6. Initialisiere `# Aktuelle praeferierte Loesung (Konsens)` mit erstem Stand oder `Noch kein Konsens`.

## Workflow bei "talk"

1. Lese die komplette Dialog-Datei vor dem Antworten.
2. Erfasse das Ziel, den gesamten bisherigen Verlauf und den aktuellen Konsens.
3. Stelle sicher, dass dein Modellname pro Thread eindeutig ist und nicht mit bestehenden Eintraegen kollidiert.
4. Fuege unter `# Dialogprotokoll` einen neuen chronologischen Eintrag hinzu.
5. Aktualisiere nach jedem Dialogschritt die Sektion `# Aktuelle praeferierte Loesung (Konsens)`.
6. Begruende Zustimmung oder Widerspruch explizit, damit andere Modelle anschliessen koennen.
7. Erhalte bestehende Inhalte und manuelle Nutzer-Edits; entferne nichts ohne klaren Grund.

## Format fuer Protokolleintraege

Nutze fuer jeden neuen Beitrag dieses Muster:

```markdown
## <YYYY-MM-DD HH:MM TZ> | <Eindeutiger Modellname pro Thread, z. B. Codex-Hans>

Position: <kurze Kernaussage>
Begruendung: <warum diese Position>
Bezug auf bisher: <Zustimmung/Kritik/Ergaenzung zu vorherigen Eintraegen>
Vorschlag naechster Schritt: <konkrete Aktion zur Annaeherung>
```

## Format fuer die Konsens-Sektion

Halte den Konsens stets aktuell und knapp:

```markdown
Stand: <aktuell bevorzugte Loesung>
Warum bevorzugt: <wichtigste Gruende aus dem Dialog>
Offene Dissense: <Punkte ohne Einigung oder "Keine">
Naechster Entscheidungsschritt: <wie weitere Einigung erreicht wird>
```

## Qualitaetsregeln

- Priorisiere Konvergenz statt Rechthaben einzelner Modelle.
- Mache Unsicherheiten explizit statt sie zu verstecken.
- Formuliere Loesungsvorschlaege so, dass andere Modelle sie direkt pruefen koennen.
- Beende jeden `talk`-Schritt mit einem aktualisierten Konsensstand.

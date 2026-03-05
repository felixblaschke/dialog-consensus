---
name: dialog-consensus
description: Erstelle und pflege eine Dialog-Markdown-Datei fuer kollaborative Diskussionen zwischen mehreren Agents oder Sprachmodellen mit gemeinsamem Ziel. Verwende den Skill, wenn ein Nutzer den Austausch mit dem Keyword "dialog" plus Markdown-Datei startet (z. B. `dialog team-diskussion.md`), mit dem Keyword "talk" einen bestehenden Dialog fortfuehren moechte, mit `talkuser <file>` gezielt Nutzerfeedback in das Protokoll einbringen will, oder mit `talksummary <file>` eine strukturierte Zusammenfassung mit Einigkeit und Uneinigkeit der Modelle benoetigt. Nutze ihn immer dann, wenn ein chronologisches Dialogprotokoll und eine laufend aktualisierte Konsens-Sektion gefuehrt werden sollen.
---

# Dialog Consensus

## Kernprinzip

- Behandle alle teilnehmenden Modelle als ein Team mit einem gemeinsamen Ziel.
- Fuehre einen kritischen, begruendeten Dialog statt isolierter Einzelmeinungen.
- Arbeite auf eine gemeinsame, bevorzugte Loesung hin.
- Halte Verlauf und Konsens fuer andere Modelle eindeutig lesbar.
- Arbeite immer mit einer eindeutigen Modell-Identitaet pro Thread.
- Halte den Konsens selbsttragend: Mit `# Ziel` plus `# Aktuelle praeferierte Loesung (Konsens)` muss die Loesung umsetzbar sein, ohne Rueckgriff auf `# Dialogprotokoll`.

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

## Workflow bei "dialog <markdown-datei>"

1. Erwarte das Keyword `dialog` mit einer konkreten Markdown-Datei (z. B. `dialog team-diskussion.md`).
2. Wenn die Datei nicht existiert, erfrage das Ziel, bis Nutzerwunsch und Zielzustand klar sind, und erstelle die neue Dialog-Datei.
3. Wenn die Datei bereits existiert, lies sie vollstaendig und pruefe den Marker `DIALOG_FILE: true`.
4. Setze den Marker `DIALOG_FILE: true` in die erste Zeile, falls er fehlt.
5. Stelle die Hauptsektionen in der vorgegebenen Reihenfolge sicher.
6. Befuelle bzw. aktualisiere `# Ziel`, `# Dialogprotokoll` und `# Aktuelle praeferierte Loesung (Konsens)` passend zum Startzustand.

## Workflow bei "talk"

1. Lese bei jedem einzelnen `talk`-Aufruf die komplette Dialog-Datei erneut von oben bis unten, auch wenn unmittelbar zuvor ein anderer Beitrag geschrieben wurde.
2. Erfasse das Ziel, den gesamten bisherigen Verlauf, alle Nutzerbeitraege und den aktuellen Konsens.
3. Stelle sicher, dass dein Modellname pro Thread eindeutig ist und nicht mit bestehenden Eintraegen kollidiert.
4. Setze dich explizit mit offenen oder neuen Nutzerbeitraegen auseinander und nimm dabei auch bereits vorhandene Modell-Antworten darauf mit in die Bewertung auf.
5. Fuege unter `# Dialogprotokoll` einen neuen chronologischen Eintrag hinzu.
6. Aktualisiere nach jedem Dialogschritt die Sektion `# Aktuelle praeferierte Loesung (Konsens)`.
7. Pflege im Konsens den Block `Contents` vollstaendig: alle fuer die Loesung relevanten Ergebnisse, erzeugten Artefakte und Entscheidungsdetails muessen dort stehen (z. B. Codexizzen, Diagramme, strukturierte Ausgaben, generierte Snippets).
8. Schreibe den Konsens ohne Rueckverweise wie "siehe Dialog oben"; uebernehme noetige Informationen direkt in den Konsens.
9. Begruende Zustimmung oder Widerspruch explizit, damit andere Modelle anschliessen koennen.
10. Erhalte bestehende Inhalte und manuelle Nutzer-Edits; entferne nichts ohne klaren Grund.

## Workflow bei "talkuser <file>"

1. Erwarte `talkuser <file>` mit einer vorhandenen Markdown-Datei als Ziel.
2. Lese die komplette Dialog-Datei, bevor du den Nutzerbeitrag aufnimmst.
3. Frage den Nutzer explizit nach seinem Beitrag, z. B. "Was moechtest du als Nutzer ins Protokoll aufnehmen?".
4. Fuege den Nutzertext als neuen chronologischen Eintrag unter `# Dialogprotokoll` ein.
5. Aktualisiere bei `talkuser` die Konsens-Sektion nicht.
6. Markiere den Nutzerbeitrag als Input fuer die naechsten `talk`-Schritte.

## Workflow bei "talksummary <file>"

1. Erwarte `talksummary <file>` mit einer vorhandenen Markdown-Datei als Ziel.
2. Lese die komplette Dialog-Datei vollstaendig, inklusive `# Dialogprotokoll` und `# Aktuelle praeferierte Loesung (Konsens)`.
3. Gib eine kompakte Zusammenfassung des bisherigen Dialogverlaufs.
4. Liste explizit, bei welchen Punkten die Modelle einig sind.
5. Liste explizit, bei welchen Punkten die Modelle uneinig sind oder wo Dissense offen sind.
6. Gib zum Schluss konkrete Ansatzpunkte, zu welchen offenen Punkten der Nutzer gezielt Feedback geben kann.
7. Veraendere bei `talksummary` den Dateiinhalt nicht, solange der Nutzer keine Bearbeitung anfordert.

## Format fuer Protokolleintraege

Nutze fuer jeden neuen Beitrag dieses Muster:

```markdown
## <YYYY-MM-DD HH:MM TZ> | <Eindeutiger Modellname pro Thread, z. B. Codex-Hans>

Position: <kurze Kernaussage>
Begruendung: <warum diese Position>
Bezug auf bisher: <Zustimmung/Kritik/Ergaenzung zu vorherigen Eintraegen>
Vorschlag naechster Schritt: <konkrete Aktion zur Annaeherung>
```

Fuer `talkuser`-Eintraege nutze dieses Muster:

```markdown
## <YYYY-MM-DD HH:MM TZ> | User

Nutzerbeitrag: <freie Rueckmeldung, Constraint, Priorisierung oder Korrektur>
Hinweis fuer naechstes talk: <welcher Punkt von den Modellen geprueft werden soll>
```

Fuer `talksummary` nutze dieses Antwortmuster:

```markdown
Zusammenfassung: <kurzer Verlauf mit aktuellem Stand>
Einigkeiten: <stichpunktartige Punkte mit gemeinsamer Modellposition>
Uneinigkeiten: <stichpunktartige Konfliktpunkte oder offene Dissense>
Moegliche Nutzer-Impulse: <konkrete Fragen oder Constraints, die der Nutzer beantworten kann>
```

## Format fuer die Konsens-Sektion

Halte den Konsens stets aktuell und knapp:

```markdown
Stand: <aktuell bevorzugte Loesung>
Warum bevorzugt: <wichtigste Gruende aus dem Dialog>
Contents:
- <konkreter, umsetzbarer Loesungsinhalt; keine Dialog-Referenzen>
- <alle relevanten Artefakte, inkl. Codexizzen, Diagramme, generierter Inhalte, wenn Teil der Loesung>
Offene Dissense: <Punkte ohne Einigung oder "Keine">
Naechster Entscheidungsschritt: <wie weitere Einigung erreicht wird>
```

## Qualitaetsregeln

- Priorisiere Konvergenz statt Rechthaben einzelner Modelle.
- Mache Unsicherheiten explizit statt sie zu verstecken.
- Formuliere Loesungsvorschlaege so, dass andere Modelle sie direkt pruefen koennen.
- Beende jeden `talk`-Schritt mit einem aktualisierten Konsensstand.
- Schreibe `Contents` so, dass `# Ziel` + Konsens allein ausreichen, um das Problem zu loesen.
- Behandle `talkuser`-Eintraege als verbindlichen Diskussionsinput: erst protokollieren, dann im naechsten `talk` inhaltlich auswerten.
- Halte `talksummary` neutral, nachvollziehbar und trenne klar zwischen Einigkeit, Uneinigkeit und moeglichen Nutzer-Impulsen.

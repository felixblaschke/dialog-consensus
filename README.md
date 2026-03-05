# dialog-consensus

Skill fuer kollaborative Dialoge zwischen mehreren Modellen mit gemeinsamem Ziel, chronologischem Protokoll und laufendem Konsens.

## Schnellstart

1. Dialogdatei initialisieren oder laden:
   - `dialog bugfix123.md`
2. Modellbeitrag schreiben und Konsens aktualisieren:
   - `talk bugfix123.md`
3. Nutzerfeedback protokollieren (ohne Konsens-Update):
   - `talkuser bugfix123.md`
4. Stand zusammenfassen (Einigkeit/Uneinigkeit):
   - `talksummary bugfix123.md`

## Befehle

- `dialog <file>`
  - Erstellt oder oeffnet eine Dialog-Markdown-Datei.
  - Stellt Marker und Pflichtsektionen sicher.

- `talk <file>`
  - Liest bei jedem Aufruf die komplette Datei neu.
  - Fuegt einen neuen Modellbeitrag hinzu.
  - Aktualisiert den Konsens.
  - Pflegt `Contents` im Konsens vollstaendig (inkl. Artefakte wie Codexizzen/Diagramme), ohne Verweise auf das Dialogprotokoll.
  - Beruecksichtigt explizit vorhandenes Nutzerfeedback.

- `talkuser <file>`
  - Fragt den Nutzer nach einem Beitrag.
  - Schreibt den Beitrag nur ins Protokoll.
  - Aendert den Konsens nicht.

- `talksummary <file>`
  - Liest die komplette Datei.
  - Gibt aus:
    - kurze Zusammenfassung des Verlaufs
    - Einigkeit der Modelle
    - Uneinigkeit/offene Dissense
    - moegliche Nutzer-Impulse fuer gezieltes Feedback
  - Nimmt keine Datei-Aenderung vor.

## Typischer Ablauf

1. `dialog bugfix123.md`
2. `talk bugfix123.md`
3. `talk bugfix123.md`
4. `talksummary bugfix123.md`
5. `talkuser bugfix123.md`
6. `talk bugfix123.md`

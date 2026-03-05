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
  - Uebersetzt aktionsorientierte Nutzereingaben zuerst in ein Zielbild (Zielzustand, Erwartung, Akzeptanzkriterien).
  - Klaert zuerst das Ziel (bei neuer Datei iterativ bis zur klaren Zieldefinition).
  - Erstellt oder oeffnet danach eine Dialog-Markdown-Datei.
  - Stellt Marker und Pflichtsektionen sicher.
  - Fuehrt keine Analyse und keine Rueckschau durch und startet keinen `talk`-Schritt automatisch im selben Prompt.
  - Fasst nach dem Erstellen/Aktualisieren das Ziel zusammen und fragt, ob noch Verfeinerungen noetig sind.
  - Gibt erst nach Nutzerbestaetigung den Hinweis auf den naechsten Befehl `talk <file>`.

- `talk <file>`
  - Liest bei jedem Aufruf die komplette Datei neu.
  - Dokumentiert im Beitrag den Lesestand (`Gelesen bis`), damit parallele Modelllaeufe nachvollziehbar bleiben.
  - Prueft direkt vor dem Schreiben auf neue Eintraege und validiert die Antwort bei Aenderungen neu.
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
2. Zielzusammenfassung pruefen und bei Bedarf im selben `dialog` weiter verfeinern.
3. Nach Bestaetigung: `talk bugfix123.md`
4. `talk bugfix123.md`
5. `talksummary bugfix123.md`
6. `talkuser bugfix123.md`
7. `talk bugfix123.md`

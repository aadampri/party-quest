# Framework-Design

## Architektur

Party Quest ist ein **template-basiertes** Framework. Jede Quest-Instanz ist eine eigenständige HTML-Datei mit:

- Story-Texten (themenspezifische Erzählung)
- Spielbeschreibungen mit Regeln
- Ergebnis-Tabellen (dynamisch je nach Spieleranzahl)
- Spiel-Auswahl (welche Spiele aktiv sind)
- Druck-optimiertes Layout für A4

### Komponentenmodell

```
┌─────────────────────────────────────┐
│  UI-Panel (nur am Bildschirm)       │
│  - Spieleranzahl                    │
│  - Namenseingabe                    │
│  - Spiel-Auswahl                   │
│  - Drucken-Button                   │
└─────────────────────────────────────┘
┌─────────────────────────────────────┐
│  Eröffnung (Brief/Geschichte)       │  ← Seite 1
└─────────────────────────────────────┘
┌─────────────────────────────────────┐
│  Legende (Symbole, Regelübersicht)  │  ← Seite 2
├─────────────────────────────────────┤
│  Spiel-Block × N                    │  ← Seiten 2–N
│  ┌─ Titel                           │
│  ├─ Story-Text (thematisch)         │
│  ├─ Regelliste                      │
│  ├─ Ergebnis-Tabelle (dyn. Zeilen)  │
│  └─ Hinweis (Gewinner → Empfänger)  │
├─────────────────────────────────────┤
│  Finale (Gruppenaktivität)          │
├─────────────────────────────────────┤
│  Ersatzspiele (ausgeblendet wenn    │
│  nicht verwendet)                   │
├─────────────────────────────────────┤
│  Material-Checkliste                │
├─────────────────────────────────────┤
│  Extras (Sticker, Vorlagen)         │
└─────────────────────────────────────┘
```

## Spieltypen

Spiele fallen in messbare Kategorien:

| Typ | Metrik | Beispiel |
|-----|--------|----------|
| **Zeit** | Schnellste gewinnt | Balance-Rennen, Hindernisparcours |
| **Genauigkeit** | Nächster am Ziel | Gewichtsschätzung, Würfelvorhersage |
| **Distanz** | Weiteste gewinnt | Standweitsprung, Werfen |
| **Sammeln** | Meiste gesammelt | Fangen, Schwamm tränken |
| **Glück** | Zufallsergebnis | Würfeln, Karte ziehen |
| **Kreativ** | Bewertet/abgestimmt | Beste Verkleidung |

### Energielevel

Jedes Spiel hat ein Energieprofil:

- 🟢 **Ruhig** — Basteln, Puzzle, Raten (sitzen/stehen)
- 🟡 **Mittel** — Werfen, Balancieren, Präzisionsaufgaben
- 🔴 **Hoch** — Rennen, Wettlauf, Hindernisse

**Empfohlener Bogen:** 🟢 → 🟡 → 🟡 → 🔴 → 🟡 → 🔴 → Finale

## Spieler-Skalierung

- N Spieler → N-1 Spiele nötig (letztes Token geht an das Kind ohne eines)
- Spiel-Auswahl erlaubt N-1 Spiele aus dem Gesamtkatalog zu wählen
- Tabellen passen Zeilen dynamisch an
- Funktioniert für 2–9 Spieler (begrenzt durch verfügbare Spiele: 6 Haupt + 2 Ersatz = 8 max)

## Druck-Design

- Ziel: A4 Papier (210×297mm, druckbarer Bereich ~190×277mm)
- Jeder Spiel-Block nutzt `page-break-inside: avoid`
- Hintergrundfarben drucken via `print-color-adjust: exact`
- UI-Panel beim Druck ausgeblendet
- Alle Inhalte müssen in Graustufen lesbar sein

## Bastel-Vorlagen

Optionale druckbare Vorlagen (z.B. Schläger-Form) nutzen:
- SVG in 1:1 Maßstab in mm-Einheiten
- Parametrisierbare Dimensionen (Schieberegler)
- 5cm Kontrollmaß-Linie (unskaliert) zur Druck-Überprüfung
- Anleitungen beim Druck ausgeblendet, nur die Vorlage druckt

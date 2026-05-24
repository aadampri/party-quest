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

## Token-Bindungs-Mechanik

Die **Kernschleife** ist: Spiel → Gewinner → Gewinner wählt Empfänger → Empfänger erhält Token → Wiederholen. Aber *wie* das Token ein Kind mit der Belohnung am Ende verbindet, ist eine Designentscheidung mit mehreren Varianten:

### Bindungsstrategien

| Strategie | Wann Bindung passiert | Schatz-Vorbereitung | Ideal für |
|-----------|----------------------|---------------------|-----------|
| **Bindung beim Empfang** | Empfänger markiert Token mit persönlichem Symbol bei Erhalt | Schätze sind unmarkiert; Symbole am Ende zuordnen | Flexibel — keine Vorbereitung pro Kind nötig |
| **Vor-gebundene Tokens** | Tokens sind *vor* der Party mit Symbolen markiert | Jeder Schatz ist vorab mit passendem Symbol beschriftet | Weniger Arbeit während der Party; Überraschungseffekt |
| **Positionell** | Token = Puzzleteil; Position auf zusammengesetzter Karte zeigt auf Schatz | Schätze an Orten versteckt, die die Karte enthüllt | Am immersivsten; erfordert räumliches Puzzle |

### So funktioniert es (Detail)

```
┌─────────────────────────────────────────────────────────────┐
│                 BINDUNG BEIM EMPFANG                         │
│                                                             │
│  1. Kind erhält blankes Puzzleteil                          │
│  2. Kind markiert es mit persönlichem Symbol (Sticker/Malen)│
│  3. Am Ende: zusammengesetztes Puzzle zeigt den Ort         │
│  4. Jedes Kind findet Schatz mit seinem Symbol              │
│                                                             │
│  Symbolzuweisung: bei Party-Start (aus Set wählen)          │
│  Schatz-Vorbereitung: N gleiche Schätze, am Ende beschriften│
│                       ODER vorab beschriften und zuordnen    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                 VOR-GEBUNDENE TOKENS                         │
│                                                             │
│  1. Vor der Party: jedes Puzzleteil mit Symbol markieren    │
│  2. Vor der Party: jeden Schatz mit passendem Symbol        │
│  3. Empfänger bekommt zufälliges Teil (Symbol = Schicksal)  │
│  4. Am Ende: Kind ordnet Symbol auf seinem Teil einem       │
│     Schatz zu — „welcher Schatz gehört DIR?"                │
│                                                             │
│  Pro: Null Aufwand während der Party, Überraschung          │
│  Contra: N verschiedene Schätze vorab vorbereiten           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                 POSITIONELL                                  │
│                                                             │
│  1. Zusammengesetzte Teile ergeben Karte/Bild               │
│  2. Karte enthüllt EINEN gemeinsamen Ort                    │
│  3. Gruppe geht zusammen hin und findet ALLE Schätze        │
│  4. Individuelle Bindung über Namensschilder oder           │
│     Symbol-Sticker an jedem Schatz am Fundort               │
│                                                             │
│  Pro: Dramatischste Enthüllung, stärkster Gruppenmoment     │
│  Contra: Alle Schätze müssen an einem Ort sein              │
└─────────────────────────────────────────────────────────────┘
```

### Symbole statt Farben

**Thematische Symbole** statt Farben für persönliche Marker verwenden:
- Farben wirken willkürlich und lösen „Ich wollte blau!" Konflikte aus
- Thematische Symbole sind Teil der Geschichte (Käsesorten, Tierpfoten, Planeten-Icons)
- Symbole funktionieren in Graustufen (wichtig für Ausdrucke)
- Kinder fühlen Besitz über „ihr" Symbol während der ganzen Party

### Beispiel-Instanzen

| Thema | Symbole | Bindungsstrategie |
|-------|---------|-------------------|
| Katzen & Mäuse | Käsesorten (Schweizer, Gouda, Brie…) | Bindung beim Empfang (Sticker auf Puzzleteil) |
| Piraten | Totenkopf-Varianten (Hut, Augenklappe, Papagei…) | Vor-gebunden (Münzen vorab gestempelt) |
| Weltraum | Planeten-Icons (Saturn, Mars, Mond…) | Positionell (Sternkarte zeigt Koordinaten) |

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

---
layout: default
---
# Party Quest

Ein Framework für strukturierte Kinder-Partyspiele mit einer Quest-Erzählstruktur.

## Konzept

**Kernidee:** Eine Reihe von Mini-Spielen, verbunden durch eine Geschichte. Jeder Spielgewinner bringt ein gemeinsames Ziel voran (Puzzleteile, Kartenfragmente, Schlüssel), das zu einer Gruppenbelohnung am Ende führt.

### Kern-Schleife

```
Spiel → Gewinner → Gewinner wählt Empfänger → Empfänger erhält Token → Wiederholen
```

Nachdem alle Tokens verteilt sind, setzt die Gruppe sie zusammen, um das Finale freizuschalten (Schatz finden, Truhe öffnen, Rätsel lösen).

### Komplexitätsstufen

| Stufe | Token-System | Ideal für |
|-------|-------------|-----------|
| **Einfach** | Sticker auf eine fertige Karte kleben | 3–5 Jahre |
| **Mittel** | Puzzleteile durch Spiele verdienen | 5–7 Jahre |
| **Fortgeschritten** | Puzzleteile + Zusammensetzen enthüllt Versteck | 7+ Jahre |

## Framework-Parameter

| Parameter | Beschreibung | Bereich |
|-----------|-------------|---------|
| Spieler | Anzahl der Kinder | 2–9 |
| Spiele | Anzahl Mini-Spiele (= Spieler - 1) | 1–8 |
| Komplexität | Einfach / Mittel / Fortgeschritten | — |
| Thema | Story-Rahmen (Katzen/Mäuse, Piraten, Weltraum...) | Beliebig |

## So funktioniert's

1. **Thema wählen** — liefert die Erzählung für jedes Spiel
2. **Spieleranzahl festlegen** — bestimmt wie viele Spiele nötig sind
3. **Spiele auswählen** aus dem Katalog — Mix aus körperlich, geistig, kreativ, Glück
4. **Spielplan drucken** — interaktives HTML mit editierbaren Tabellen
5. **Party durchführen** — Story-Texte vorlesen, Spiele spielen, Ergebnisse eintragen

## Struktur

```
de/          ← Du bist hier (Deutsch)
en/          ← Englische Version
templates/   ← Sprachneutrale Starter-Vorlagen
```

## Beispiele

- [Katzen & Mäuse](examples/katzen-und-maeuse/) — Der Hauskater ist im Urlaub, Mäuse suchen den versteckten Käse

## Spieldesign-Prinzipien

1. **Jedes Kind gewinnt etwas** — die Puzzle-Mechanik stellt sicher, dass jeder ein Teil bekommt
2. **Gewinner wählt Empfänger** — soziales Element, kein Kind ist „letztes"
3. **Spieltypen mischen** — körperlich/geistig/Glück abwechseln, verschiedenen Kindern eine Chance geben
4. **Energie-Bogen** — ruhig starten (Basteln), steigern (Bewegung), Höhepunkt (Rennen), Finale (Gruppe)
5. **Ersatzspiele** — immer 2+ Reservespiele bereithalten
6. **Skalierbar** — gleiches Framework funktioniert für 3 oder 9 Kinder

## Lizenz

MIT

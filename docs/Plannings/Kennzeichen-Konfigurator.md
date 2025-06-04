# Optionen zum Rendern von individuellen Kennzeichen im Elferplatz-Konfigurator

## Kennzeichen mit Font "Hacken"
Die Kennzeichenschrift wird als Font über das Kennzeichen gelegt.  
Das Kennzeichen soll als weißes *Blank* gerendert werden.

**Pro**
- Schnell umsetzbar  
- Kein zusätzlicher Rendering-Aufwand  

**Contra**
- Kennzeichen hat keine Dreidimensionalität  
- Frontend muss die Schrift über jedes Bild legen  

---

## Jede Ziffer rendern und im Frontend zusammensetzen
Alle Stellen des Kennzeichens werden einzeln gerendert und im Frontend anhand vieler kleiner Bilder zusammengesetzt.

**Pro**
- Das Kennzeichen ist dreidimensional  

**Contra**
- Reflektionen der Karosserie im Kennzeichen (und umgekehrt) fehlen  
- Frontend muss die einzelnen Ziffern für jedes Bild zusammensetzen  

---

## Kennzeichen-Presets only
Es gibt drei vorgefertigte Kennzeichen, aus denen ausgewählt werden kann.

**Pro**
- Kennzeichen ist realgetreu  

**Contra**
- Keine Individualisierbarkeit  

---

## Kennzeichen-Konfigurator mit Geometry Nodes und nur auf Anfrage rendern
Ein Blender-Konfigurator wird gebaut, mit dem Kennzeichen generiert werden können.  
Bei spezieller Kennzeichenanfrage kann das Auto mit genau diesem Kennzeichen vom Server gerendert werden.

**Pro**
- Kennzeichen ist realgetreu  

**Contra**
- Viel zu viele Möglichkeiten, um die Kennzeichen vorab zu rendern:  
  - Buchstaben, Spacing, Kennzeichengröße, Reflektionen der Karosserie → mindestens $e \cdot 10^{30}$ Kombinationen  
- Rendering dauert ca. 30 Sekunden – zu lange für das Anzeigen im Frontend  

---

## Kennzeichen händisch vom Render-Team erstellen lassen
Nur auf Anfrage wird das Auto mit einem speziellen Kennzeichen vom 3D-Team gerendert – wie es z. B. Porsche selbst macht.

**Pro**
- Kein Kennzeichengenerator nötig  
- Realgetreu  

**Contra**
- Kein Kennzeichengenerator verfügbar  

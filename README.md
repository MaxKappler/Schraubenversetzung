# SC-Schraubenversetzung – GitHub Pages

Ein bildschirmfüllender 3D-Viewer ohne sichtbare Texte, Menüs oder Regler.
Alle 320 Atomkugeln sind grau und haben den festen Radius **0,28 a**.
Die Versetzungslinie bei x = y = 0 ist immer eingeschaltet, schwarz,
durchgezogen und 3,5 Bildschirmpixel dick. Sie wird als Orientierungslinie
über den Kugeln gezeichnet, damit sie durchgehend sichtbar bleibt.
Beim Blick exakt entlang der Linie erscheint sie als Punkt.

## Veröffentlichen oder vorhandene Website aktualisieren

1. ZIP entpacken.
2. Die enthaltene `index.html` im Hauptverzeichnis deines GitHub-Repositorys
   hochladen und die bisherige Datei ersetzen. Alle weiteren Dateien können
   ebenfalls durch die neue Fassung ersetzt werden.
3. Änderung speichern (Commit changes). Bei bereits eingerichtetem GitHub
   Pages wird die Website danach automatisch aktualisiert.
4. Für eine neue Website: **Settings → Pages → Deploy from a branch → main →
   / (root) → Save**. Falls dein Branch anders heißt, diesen auswählen.

`index.html` muss im Hauptverzeichnis liegen. Nicht nur die ZIP-Datei hochladen.
Offizielle Anleitung: https://docs.github.com/en/pages/quickstart

## Bedienung

- Mit der Maus oder einem Finger ziehen: drehen.
- Mausrad oder zwei Finger: zoomen; Atomradius und Atompositionen bleiben fest.
- Nach Anklicken des Modells: Pfeiltasten drehen, `+` und `-` zoomen, `R` setzt
  die Blickrichtung und den Zoom zurück.

Der Viewer füllt die gesamte Website aus. Es gibt keine Bedienoberfläche,
keine Beschriftungen, keine automatische Drehung und keine Ausschnittwahl.

## Dateien

| Datei | Zweck |
| --- | --- |
| `index.html` | Kompletter Viewer mit allen Koordinaten, CSS und JavaScript. |
| `Atomkoordinaten.csv` | Dieselben ursprünglichen 320 Atompositionen. |
| `.nojekyll` | Statische Veröffentlichung ohne Jekyll-Verarbeitung. |
| `README.md` | Diese Anleitung; wird auf der Website nicht eingeblendet. |

Keine Installation und keine externen Bibliotheken nötig. `index.html` lässt
sich auch direkt per Doppelklick im Browser öffnen.

## Modell

Unverändertes SC-Schraubenversetzungsmodell mit Burgersvektor b = a [001]:

```text
x/a = i + 1/2
y/a = j + 1/2
z/a = k + theta/(2*pi) - 1/2
theta = atan2(y, x) modulo 2*pi
i, j = -4, ..., 3
k = -2, ..., 2
```

Der kleinste Mittelpunktabstand beträgt a; bei Radius 0,28 a bleibt somit
ein Mindestabstand von 0,44 a zwischen den Kugeloberflächen. In der
orthografischen Projektion können sich Kugeln verdecken.

Es ist ein geometrisches Modell auf Grundlage des elastischen
Verschiebungsfelds. Versetzungskern und freie Oberflächen sind nicht
atomistisch relaxiert. Die schwarze Linie ist eine Orientierungshilfe,
kein zusätzliches Atom oder physischer Stab.

- Hamada et al. (2018): https://doi.org/10.1186/s40736-018-0037-8
- Carpio & Bonilla (2005): https://doi.org/10.1103/PhysRevB.71.134105

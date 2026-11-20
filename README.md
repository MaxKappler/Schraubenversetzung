# SC-Schraubenversetzung – GitHub Pages

Ein bildschirmfüllender 3D-Viewer mit zwei Vektorpfeilen und einer 90°-Taste.
Alle 320 Atomkugeln sind grau und haben den festen Radius **0,28 a**.
Die Versetzungslinie ist ein durchgehender schwarzer 3D-Zylinder bei x = y = 0,
mit Radius 0,035 a und Enden bei z = ±3,4 a. Kugeln und Linie werden gemeinsam
mit WebGL und einem Tiefenpuffer dargestellt: Vordere Kugeln verdecken die
Linie; die Linie verdeckt dahinterliegende Kugeln. Diese Reihenfolge wird
beim Drehen für jeden Bildpunkt bestimmt. Die Liniendicke skaliert beim
Zoomen wie die übrige Geometrie. Beim Blick entlang der Linie ist ihre
kreisförmige Stirnfläche sichtbar.

## Vektoren

- **Blau: Linienvektor ξ**, die gewählte positive Tangentenrichtung +[001].
  Der Pfeil sitzt am positiven Ende der Versetzungslinie. ξ ist ein
  dimensionsloser Einheitsvektor; seine gezeichnete Länge ist illustrativ.
- **Rot: Burgersvektor b = a [001]**, parallel zum Linienvektor. Der Abstand
  vom Pfeilanfang bis zur Spitze beträgt genau a. Zur besseren Sichtbarkeit
  ist dieser freie Vektor seitlich versetzt gezeichnet.

Beide Pfeile sind echte 3D-Geometrie mit derselben Tiefenprüfung wie die Atome.
Die kleinen Beschriftungen ξ und b bleiben als Bildschirmanmerkungen lesbar.

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

- Mit der Maus oder einem Finger ziehen: drehen. Die Bewegung folgt auch
  nach der 90°-Drehung den Bildschirmrichtungen, ohne vertauschte Achsen.
- Mausrad oder zwei Finger: zoomen; Atomradius und Atompositionen bleiben fest.
- **90° drehen**: gesamte Ansicht um genau 90° im Uhrzeigersinn drehen,
  sodass die Versetzungslinie horizontal liegt. **90° zurück** stellt die
  vertikale Ausrichtung wieder her. Blickwinkel und Zoom bleiben erhalten.
  Beim Blick exakt entlang der Achse wird zusätzlich der anfängliche
  Neigungswinkel wiederhergestellt, damit die Linie sichtbar wird.
- Nach Anklicken des Modells: Pfeiltasten drehen, `+` und `-` zoomen, `R` setzt
  die Blickrichtung und den Zoom zurück.

Der Viewer füllt die gesamte Website aus. Außer den Vektorbezeichnungen und
der 90°-Taste gibt es keine weiteren Texte, Regler oder Menüs.

## Dateien

| Datei | Zweck |
| --- | --- |
| `index.html` | Kompletter Viewer mit allen Koordinaten, CSS und JavaScript. |
| `Atomkoordinaten.csv` | Dieselben ursprünglichen 320 Atompositionen. |
| `.nojekyll` | Statische Veröffentlichung ohne Jekyll-Verarbeitung. |
| `README.md` | Diese Anleitung; wird auf der Website nicht eingeblendet. |

Keine Installation und keine externen Bibliotheken nötig. `index.html` lässt
sich auch direkt per Doppelklick in einem Browser mit aktiviertem WebGL öffnen.

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

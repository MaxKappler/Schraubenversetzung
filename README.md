# SC-Schraubenversetzung – GitHub Pages

Eine eigenständige Website mit dem bisherigen 320-Atom-Modell. Alle Kugeln sind gleich grau; die mittlere Lage wird nicht blau hervorgehoben.

**Das zitierte Modell ist eine Schraubenversetzung (screw dislocation), keine Stufenversetzung (edge dislocation).** Die Website übernimmt genau diese Schraubengeometrie.

## Schnell veröffentlichen

1. Dieses ZIP auf deinem Computer entpacken.
2. Ein neues GitHub-Repository anlegen, zum Beispiel `sc-schraubenversetzung`. Mit GitHub Free muss das Repository für Pages öffentlich sein.
3. Im Repository **Add file → Upload files** wählen. Die entpackten Dateien hochladen. `index.html` muss direkt im Hauptverzeichnis des Repositorys liegen, nicht in einem zusätzlichen Unterordner. Nicht nur die ZIP-Datei hochladen.
4. Die Dateien auf dem Branch `main` speichern (Commit changes).
5. **Settings → Pages → Build and deployment** öffnen.
6. Bei **Source** die Option **Deploy from a branch** wählen, als Branch **main** und als Ordner **/ (root)** auswählen, dann **Save**.
7. Nach dem Deployment erscheint dort der Website-Link. Bei einem normalen Projekt-Repository lautet er `https://DEIN-NAME.github.io/sc-schraubenversetzung/`.

Falls dein Branch anders heißt, diesen statt `main` auswählen. Ein Benutzer-Repository mit dem Namen `DEIN-NAME.github.io` wird direkt unter `https://DEIN-NAME.github.io/` angezeigt. Die erste Veröffentlichung kann einige Minuten dauern.

Offizielle Anleitung: https://docs.github.com/en/pages/quickstart

## Dateien

| Datei | Zweck |
| --- | --- |
| `index.html` | Vollständige Website inklusive CSS, JavaScript und aller Atompositionen. |
| `Atomkoordinaten.csv` | Unveränderte Atomkoordinaten als zusätzlich angebotener Download. |
| `.nojekyll` | Leere Datei für statische Veröffentlichung ohne Jekyll-Verarbeitung. Die Seite funktioniert auch ohne diese Datei. |
| `README.md` | Diese Anleitung. |

**Kein npm, kein Build-Schritt, kein Servercode und keine externen JavaScript-Bibliotheken.** Zum lokalen Ansehen `index.html` per Doppelklick öffnen. Alle notwendigen Modelldaten stehen direkt in der HTML-Datei. Die Website verwendet keine externen Schriften, Tracker oder CDN-Dateien.

## Bedienung

- Maus / ein Finger ziehen: Modell drehen.
- Mausrad / zwei Finger auseinanderziehen: zoomen.
- Schaltflächen für räumliche Ansicht, Draufsicht und Seitenansicht.
- Regler für Zoom und Kugelradius.
- Wahl zwischen allen 320 Atomen und einer Kernumgebung mit 80 Atomen.
- Optional Versetzungslinie und automatische Drehung einschalten.
- Darstellung zurücksetzen stellt alle Ausgangswerte wieder her.
- Tastatur nach Anklicken des Modells: Pfeiltasten drehen, `+` / `−` zoomen, `R` setzt zurück.
- Vollbild steht bereit, wenn der Browser die Fullscreen-API unterstützt.

## Physikalisches Modell

Einfach kubisches Gitter (SC), 8 × 8 Atomsäulen mit je 5 Atomen; Burgersvektor b = a [001].

Die ursprünglichen Atompositionen sind unverändert:

```text
x/a = i + 1/2
y/a = j + 1/2
z/a = k + theta/(2*pi) - 1/2
theta = atan2(y, x) modulo 2*pi
i, j = -4, ..., 3
k = -2, ..., 2
```

Die Versetzungslinie liegt bei x = y = 0. Ein kontinuierlich verfolgter vollständiger Umlauf erhöht die Höhe um b = a. Die endliche Oberfläche besitzt eine entsprechende Stufe. Die Positionsdaten enthalten 320 Kugelmittelpunkte, keine Bindungen.

Der anfängliche Kugelradius ist 0,28 a. Der kleinste Mittelpunktabstand beträgt a, der kleinste Oberflächenabstand daher 0,44 a. Auch beim maximal einstellbaren Radius 0,38 a berühren sich die Kugeln räumlich nicht. In der Projektion können sie sich natürlich verdecken. Alle Atome nutzen dieselbe graue Schattierung; es existiert keine Farbzuweisung nach Atomlage.

Dies ist ein geometrisches Modell auf Grundlage des elastischen Verschiebungsfelds. Versetzungskern und freie Oberflächen sind nicht atomistisch relaxiert. Die Kugelgröße ist eine Darstellungsgröße. Die Kernansicht ändert nur den gezeigten Ausschnitt.

Quellen zur Geometrie:

- Hamada et al. (2018): *An algebraic description of screw dislocations in SC and BCC crystal lattices*. https://doi.org/10.1186/s40736-018-0037-8
- Carpio & Bonilla (2005): *Discrete models of dislocations and their motion in cubic crystals*. https://doi.org/10.1103/PhysRevB.71.134105

## Anpassen

Die Website ist absichtlich in einer einzigen HTML-Datei enthalten. Darstellung: im `<style>`-Block. Kugelfarbe: Farbstopps in `sphereSprite()`. Standardwerte: Objekt `initial` im JavaScript. Die Atomkoordinaten stehen im JSON-Block mit der ID `atom-data`.

Die Darstellung projiziert dreidimensionale Koordinaten orthografisch auf ein HTML-Canvas, sortiert die Kugeln nach Tiefe und verwendet eine gemeinsame Kugelschattierung. Sie benötigt kein WebGL. Werden die wissenschaftlichen Atompositionen geändert, müssen sowohl der JSON-Block als auch die CSV aktualisiert werden.

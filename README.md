# BikeFit Analyzer 🚴🏁

Video-basiertes Bike-Fitting für **Rennrad** und **Zeitfahrrad/Triathlon** – läuft komplett im Browser, keine Daten verlassen dein Gerät.

Du lädst ein Seitenvideo von dir auf der Rolle hoch, die App erkennt per Pose-Erkennung (Google MediaPipe) deine Gelenke, misst über mehrere Kurbelumdrehungen die wichtigsten Winkel und sagt dir konkret, was du ändern solltest – z. B. „Sattel ca. 6 mm höher“ oder „Armpads ca. 10 mm tiefer“.

## Was gemessen wird

| Messwert | Wofür |
|---|---|
| Kniebeugung am unteren Totpunkt | Sattelhöhe |
| Kniewinkel am oberen Totpunkt | Knie-Stauchung, Kurbellänge |
| Hüftwinkel am oberen Totpunkt | offene Hüfte (wichtig fürs Laufen nach dem Rad) |
| Rückenwinkel | Stack / Lenker- bzw. Pad-Höhe |
| Schulterwinkel | Reach |
| Ellbogenwinkel | Lenker / Extensions |
| Knie über Pedal (3 Uhr) | Sattel vor/zurück (Rennrad) |
| Trittfrequenz, Fußgelenk-Range | Info |

Dazu: Snapshots der Schlüsselpositionen mit eingezeichneten Winkeln, Winkelverlauf als Diagramm, Verlauf aller Analysen und ein **Vergleich Rennrad ↔ Zeitfahrer**.

## Millimeter-Angaben

Der Maßstab wird aus deiner **Kurbellänge** berechnet (der Fuß beschreibt einen Kreis mit etwa diesem Radius). Kurbellänge also korrekt eintragen. Die mm-Werte sind Schätzungen – immer schrittweise (max. ~5 mm) ändern und neu filmen.

## So filmst du richtig

- Rad auf der Rolle, Kamera **exakt seitlich** auf Hüfthöhe, ca. 3 m Abstand, Querformat, Stativ
- Enge Kleidung, gutes Licht, Rennschuhe
- Warmfahren, dann 20–30 s bei 85–95 U/min filmen
- Rennrad: Hände an den Hoods · Zeitfahrer: Aeroposition
- Wenn möglich 60 fps

## Auf GitHub Pages veröffentlichen

1. Neues Repository anlegen (z. B. `bikefit`)
2. `index.html` und `README.md` hochladen (**Add file → Upload files**)
3. **Settings → Pages → Source: Deploy from a branch → `main` / `root`** → Save
4. Nach ~1 Minute läuft die App unter `https://<dein-name>.github.io/bikefit/`

Lokal öffnen per Doppelklick funktioniert in manchen Browsern nicht (Module/Kamera-Sicherheit) – GitHub Pages oder `python3 -m http.server` nutzen.

## Zielbereiche anpassen

Ganz oben im `<script>` in `index.html` steht das Objekt `PROFILES` mit allen Richtwerten (Rennrad sportlich/Komfort, Zeitfahrer Lang-/Kurzdistanz). Dort kannst du die Bereiche nach deinem Geschmack oder den Vorgaben deines Fitters ändern.

## Grenzen

- MediaPipe schätzt Gelenkzentren, nicht anatomische Marker – rechne mit ±2–3° Messunsicherheit.
- Schräge Kameraperspektive verfälscht Winkel deutlich.
- Ersetzt kein professionelles Fitting, besonders nicht bei Schmerzen oder Taubheitsgefühlen.

## Technik

Eine einzige HTML-Datei, kein Build. Pose-Erkennung: [MediaPipe Pose Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/pose_landmarker) (wird beim ersten Start geladen). Verlauf wird im `localStorage` deines Browsers gespeichert, Export/Import als JSON.

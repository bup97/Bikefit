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

## Ansichten: Seite, hinten, vorne

Oben im Setup wählst du die **Ansicht**. Die Live-Ausrichtung passt ihre Checkliste automatisch an.

| Ansicht | Kamera | Was analysiert wird |
|---|---|---|
| **Seite** | exakt seitlich, Höhe Hüfte–Tretlager | Sattelhöhe, Sattel vor/zurück, Front, Fußwinkel, Becken auf/ab, Rutschen nach vorn |
| **Hinten** | genau hinter dem Rad, Sattelhöhe | Becken-Kippen (Wackeln), Becken-Schiefstand (Beinlänge), Knie-Spur, Oberkörper |
| **Vorne** | genau vor dem Rad, Kniehöhe | Knie-Spur (Knie über Fuß), Fußrotation, Oberkörper |

Links/rechts ist immer aus Sicht des Fahrers. Seitliche Werte werden in % der Hüftbreite angegeben (10 % ≈ 1,5–2 cm). Die Empfehlungen von hinten/vorne werden mit der letzten Seitenanalyse desselben Rads abgeglichen (z. B. Becken kippt **und** Bein zu gestreckt → Sattel tiefer).

## Sattel: Neigung & Position

- Neigung eintragen oder **mit dem Handy messen** (Lagesensor als digitale Wasserwaage: Nullpunkt auf dem Boden, dann längs auf den Sattel).
- Beschwerden ankreuzen (Taubheit, Rutschen, Druck auf Händen …) → konkrete Empfehlung in Grad, getrennt für Rennrad und Zeitfahrer.
- Sattelhöhe/-versatz aus der Seitenanalyse und Becken-Kippen aus der Analyse von hinten werden hier zusammengeführt.

## Fußstellung & Cleats

- Schuhgröße + Fußtest + Beschwerden → Startposition der Cleats längs (mm hinter dem Großzehen-Grundgelenk, am Zeitfahrer weiter hinten), Rotation, seitliche Position, Keile/Einlagen.
- Fließen automatisch ein: Fußwinkel und Fußgelenk-Bewegung aus dem Seitenvideo, Knie-Spur und Fußrotation aus dem Video von vorne.
- Schritt-für-Schritt-Anleitung zum Anzeichnen der Cleats.

Alle Eingaben werden pro Rad im Browser gespeichert.

## Millimeter-Angaben

Der Maßstab wird aus deiner **Kurbellänge** berechnet (der Fuß beschreibt einen Kreis mit etwa diesem Radius). Kurbellänge also korrekt eintragen. Die mm-Werte sind Schätzungen – immer schrittweise (max. ~5 mm) ändern und neu filmen.

## Live-Kamera-Ausrichtung & Aufnahme

Mit **„Live-Ausrichtung starten“** öffnet sich das Kamerabild mit Drittel-Linien, gelbem Fadenkreuz und einer Wasserwaage (Lagesensor des Handys). Die App erkennt dich live und prüft:

- Querformat · ganzer Körper im Bild · passender Abstand · Fahrer mittig
- Kamera **exakt seitlich** (90° zum Rad) · Kamerahöhe zwischen Hüfte und Tretlager
- Handy waagerecht und nicht gekippt · genug Licht für die Gelenkerkennung

Sind alle Punkte grün, wird der Rahmen grün und eine Sprachansage meldet „Perfekt ausgerichtet“ (Hinweise zum Korrigieren kommen ebenfalls per Sprache – praktisch, wenn du schon auf dem Rad sitzt). Danach startet die Aufnahme mit Countdown direkt in der App und das Video wird automatisch in die Analyse übernommen. Kamera-Zugriff braucht https – GitHub Pages passt.

## PRO-Modus: Handy als Kamera am Laptop

Im Setup den Schalter **Pro-Modus** aktivieren (wird gemerkt). Dann gibt es zwei zusätzliche Wege:

**1. Handy koppeln (WLAN, QR-Code)**
1. Am Laptop: **„Handy als Kamera koppeln“** → QR-Code und 6-stelliger Code erscheinen.
2. Mit der iPhone-Kamera den QR-Code scannen (oder auf dem Handy die Seite öffnen → Pro-Modus → „Dieses Gerät ist die Kamera“ → Code eingeben).
3. Auf dem Handy **„Kamera starten & verbinden“** tippen, Kamera- und Bewegungszugriff erlauben.
4. Das Kamerabild läuft live auf dem Laptop: Ausrichtung, Checkliste, Sprachansagen (über die Laptop-Lautsprecher) und Aufnahme passieren dort. Die Wasserwaage nutzt den Lagesensor des Handys, Hinweise erscheinen zusätzlich oben auf dem Handy-Display.

Das Video läuft direkt zwischen den Geräten (WebRTC). Für den Verbindungsaufbau wird kurz der öffentliche PeerJS-Vermittlungsserver genutzt. In Firmen- oder Gast-WLANs mit Client-Isolation kann die Verbindung blockiert sein.

**2. Kamera-Auswahl / Continuity-Kamera (Mac)**
„Kameras suchen“ listet alle Kameras. Am Mac erscheint dort die **iPhone-Kamera** (gleiche Apple-ID, WLAN & Bluetooth an, iPhone in der Nähe) – auswählen und „Live-Ausrichtung starten“.

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

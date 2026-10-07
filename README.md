# Panoramaview

Ein einfacher 360°-Panoramaviewer, ähnlich wie Google Street View, als statische HTML-Seite.
Er basiert auf [Pannellum](https://pannellum.org/) und lässt sich per `<iframe>` in andere Webseiten einbetten.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | Der Viewer |
| `panoramen.js` | Liste der Panoramen (hier neue Bilder eintragen) |
| `embed-beispiel.html` | Beispiele zum Einbetten und Übersicht der URL-Parameter |
| `Panoramabilder/` | Die Bilder |

## Lokal testen

Der Viewer braucht einen kleinen Webserver, weil Browser Bilder per `file://` nicht in WebGL laden.

```bash
python -m http.server 8000
```

Danach im Browser `http://localhost:8000/` öffnen.

## Veröffentlichen auf GitHub Pages

1. Ein neues Repository auf GitHub anlegen, z. B. `panoramaview`.
2. Den Inhalt dieses Ordners hochladen.
3. Im Repository unter **Settings → Pages** als Quelle den Branch `main` und den Ordner `/ (root)` wählen.
4. Nach ein bis zwei Minuten ist der Viewer erreichbar unter `https://ram1630.github.io/panoramaview/`.

## Einbetten

Dieser Code funktioniert auf jeder Webseite, weil er seine Gestaltung selbst mitbringt.
Das Fenster passt sich der Seitenbreite an (höchstens 900 px, Format 16:9):

```html
<!-- 360°-Panorama von https://ram1630.github.io/panoramaview/ -->
<div style="position:relative; width:100%; max-width:900px; aspect-ratio:16/9; border-radius:12px; overflow:hidden;">
  <iframe src="https://ram1630.github.io/panoramaview/?scene=berg&amp;nav=0&amp;autorotate=-2"
          title="360°-Panorama der Bergstation"
          style="position:absolute; inset:0; width:100%; height:100%; border:0;"
          allowfullscreen loading="lazy"></iframe>
</div>
```

Im Viewer erzeugt die Schaltfläche **</>** den passenden Code für die aktuelle Ansicht.

URL-Parameter: `scene`, `yaw`, `pitch`, `hfov`, `nav=0` (Navigation ausblenden), `autorotate=<Grad/s>`.

# Lotlinie – Haltungsanalyse zur Verlaufsdokumentation

Web-App für die Praxis: Haltungsfotos analysieren (seitlich/frontal), Winkel
messen (CVA, Rumpflot, Schulter-/Beckenschiefstand …), Verläufe vergleichen
und Berichte als PDF drucken. Läuft komplett im Browser – **alle Fotos und
Daten bleiben auf dem Gerät.**

## Neu in Version 1.1
 
- **Zoom:** zwei Finger zum Zoomen, ein Finger verschiebt den Ausschnitt
  (wenn gezoomt). Reset über den ×-Chip links oben im Bild.
- **✨ KI-Vorschlag (Beta):** schlägt Startpositionen für die Punkte vor
  (Modell ~7 MB, lädt einmalig vom CDN, braucht Internet). Vorschläge sind
  Schätzungen – jeden Punkt prüfen! C7/Beckenkamm werden immer nur geschätzt.
- **iPhone-Unterstützung** inkl. App-Icon, Export über den Teilen-Dialog.

## Einrichtung (einmalig, ~5 Minuten)

1. Dieses Repo auf GitHub anlegen (Name z. B. `lotlinie`, **Public**) und alle
   Dateien hochladen.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* →
   Branch `main`, Ordner `/ (root)` → **Save**.
3. Nach ca. 1 Minute läuft die App unter
   `https://DEIN-GITHUB-NAME.github.io/lotlinie/`
4. **Android:** URL in Chrome öffnen → Menü ⋮ → „Zum Startbildschirm hinzufügen".
   **iPhone:** URL in Safari öffnen → Teilen-Symbol → „Zum Home-Bildschirm".
   Fertig – liegt mit Icon wie eine App auf dem Homescreen.

   Hinweis iPhone: Falls im Homescreen-Modus beim Bericht kein Druckdialog
   erscheint, die Seite einmal direkt in Safari öffnen und dort drucken.
   Der Export nutzt den Teilen-Dialog („In Dateien sichern" wählen).

## Neue Version einspielen

1. Neue `index.html` erhalten (z. B. von Claude, nach bestandenen Tests).
2. Im Repo: `index.html` öffnen → Stift/Upload → ersetzen → **Commit**.
3. Am Handy Seite neu laden. GitHub Pages cached bis zu 10 Minuten –
   die Versionsnummer im Footer zeigt, welcher Stand gerade läuft.

## Tests (automatisiert, optional lokal)

    pip install playwright pillow
    python -m playwright install chromium
    cd tests
    python make_testimgs.py   # erzeugt Testfotos mit bekannter Geometrie
    python run_test.py        # 16 End-to-End-Tests inkl. Winkel-Verifikation

Die Tests simulieren den kompletten Ablauf (Punkte tippen, Vergleich,
Export/Import, PDF) in einem echten Chrome mit Samsung-Bildschirmgröße.

## Wichtig (Datenschutz)

- Das Repo ist öffentlich: **Es enthält nur Code, niemals Patientendaten.**
- Exportierte Aufnahmen (`lotlinie_*.json`) enthalten Fotos → **niemals ins
  Repo committen**, sondern lokal in der Patientenakte ablegen.
- Die App überträgt nichts: keine Cloud, kein Tracking, keine Cookies.

Interne Dokumentationshilfe – Richtwerte dienen der Orientierung und
ersetzen keine klinische Beurteilung.

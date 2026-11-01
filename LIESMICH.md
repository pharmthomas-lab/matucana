# Matucana – ScienceHub auf dem Smartphone (Prototyp, Schnittstelle „Maurice 0.010“)

Web-App ohne App-Store: im Handy-Browser öffnen und „Zum Startbildschirm hinzufügen“. Sie spricht direkt mit dem Datenbankserver
(Supabase), ohne VPN und ohne Netzlaufwerk.

**Funktionen:**
- **Verbrauch melden** (Parodia): Chemikalie suchen, Gebinde wählen, Menge eingeben.
- **DC-Foto** (Rhipsalis): Platte fotografieren. Das Handy verkleinert das Foto auf höchstens 2400 px. In Echinopsis erscheint es
  unter Rhipsalis → DC als Entwurf zum Prüfen.

**Anmeldung:** dienstliche E-Mail-Adresse (Benutzerverwaltung) und ScienceHub-Passwort. Das Konto entsteht still bei der Anmeldung
in Echinopsis (ab Service Pack 1 zu Melchor Múzquiz), sobald die Adresse eingetragen ist.

**Sicherheit:** Angemeldete Handys dürfen nur die Funktionen im Schema `matucana` aufrufen, keine Tabelle lesen. Jede Funktion
prüft das ScienceHub-Konto (aktiv, nicht „nur lesen“) und trägt die Person in Bewegungen bzw. Protokoll ein.

## Einrichten (Admin)
1. `py werkzeuge\matucana_einrichten.py "<databases-Ordner auf T:>"` – legt das Schema `matucana` an (ändert keine Daten).
2. Supabase-Dashboard → Project Settings → Data API → **Exposed schemas**: `matucana` ergänzen.
3. In `konfig.json` den Publishable key eintragen (derselbe wie in `speicher.json`).
4. Die Dateien dieses Ordners (`index.html`, `konfig.json`, `manifest.webmanifest`, `icon.png`) auf einen Webserver mit HTTPS legen
   (z. B. GitHub Pages oder Webspace der CAU).

## Testen ohne Supabase
`py tests\matucana_test.py --server` startet eine nachgebaute Schnittstelle mit lokalem Testserver auf http://127.0.0.1:8781
(Anmeldung `thomas@test.invalid` / `kaktus`).

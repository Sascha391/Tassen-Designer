# ☕ Foto Riede – Fun Produkte

Ein **Online-Gestalter**, mit dem Kunden von **Foto Riede** ihr **persönliches Produkt**
(z. B. eine **Tasse**) selbst gestalten: Foto hochladen, Text & Sticker dazu, mit fertigen
Design-Hintergründen und Vorlagen – am Ende landet die Bestellung mit **druckfertigem Motiv**
in einem geschützten **Backend**.

Gedacht als **eigenständige Seite**, die von der Homepage [foto-riede.de](https://www.foto-riede.de)
nur verlinkt wird – kein Eingriff in die bestehende Homepage nötig.

## 🔗 Links

| | Adresse |
|---|---|
| 🎨 **Kundenseite (live)** | **https://foto-riede-fun-produkte.web.app** |
| 🔒 **Backend / Verwaltung** | https://foto-riede-fun-produkte.web.app/bestellungen.html |
| 💻 Quellcode (GitHub) | https://github.com/Sascha391/Tassen-Designer |
| 🔥 Firebase-Konsole | https://console.firebase.google.com/project/foto-riede-tassen |

## ✨ Funktionen für Kunden (`index.html`)

- **Produkt & Größe wählen** – Produkte, Preise und Maße kommen live aus dem Backend
- **CEWE-artiger Editor** mit Seitenleiste und großer Arbeitsfläche:
  - **Fotos** – hochladen **oder per Drag & Drop** in die Fläche ziehen, verschieben & skalieren
  - **Hintergrund** – Farben, kachelbare **Muster** und **30 Design-Hintergründe**
    (Aquarell, Verlauf, Marmor, Terrazzo, Bokeh, Streifen …)
  - **Cliparts** – Sticker/Emojis
  - **Rahmen** – Foto in Form legen (Kreis, Herz, Stern, abgerundet) + Zierrahmen
  - **Text** – Schriftart, Farbe, Fett/Kursiv, Ausrichtung, Größe
  - **Vorlagen** – fertige Designs als Startpunkt (Geburtstag, Weihnachten, Liebe …)
- **Komfort:** Rückgängig/Wiederholen, Ebenen (vorne/hinten), Drehen, Spiegeln, Duplizieren,
  **Hilfslinien & Einrasten** an der Mitte, Touch-Bedienung fürs Handy
- **Zwei Maße pro Größe**
  - 📄 **Papiergröße** = das ganze Druckblatt (z. B. 24 × 10 cm, passend zur Vorlage)
  - 🎨 **Designgröße** = der Gestaltungsbereich (z. B. 20 × 8 cm), als gestrichelter Rahmen
- **Bestellung in zwei Schritten:** erst gestalten → „Weiter zur Bestellung" → Kontaktdaten
- **Kein Kundenlogin** nötig – gestalten, bestellen, fertig

## 🔒 Backend / Verwaltung (`bestellungen.html`, mit Login)

- **Bestellungen** – live, mit Motiv-Vorschau, Größe, Preis, Summe & Maßen;
  Motiv als druckfertige Datei **herunterladen** (Papiergröße, ~250 DPI);
  Status setzen (neu → in Arbeit → fertig → abgeholt), löschen
- **Produkte & Preise** – selbst verwalten (Größen/Preise/Maße, aktiv/inaktiv)
- **Hintergründe** – alle Design-Hintergründe sortieren, aus-/einblenden, löschen;
  **eigene** per Bild-Upload, Farbe oder Verlauf ergänzen
- **Farben & Rahmen** – Hintergrund- und Rahmenfarben verwalten
- **Vorlagen** – eigene Vorlagen anlegen/bearbeiten/löschen
- Je Bereich ein **„Standard laden"**-Knopf, der die eingebauten Inhalte einmalig übernimmt

## 🛠️ Technik

Reine Frontend-App (HTML/JS, [Fabric.js](https://fabricjs.com) für den Editor).
Design-Hintergründe & Muster werden **prozedural als SVG** erzeugt – keine externen Bilddateien.

Eigenes **Firebase-Projekt** (Projekt-ID `foto-riede-tassen`):

- **Firestore-Sammlungen:**
  - `tassen_bestellungen` – eingehende Bestellungen (inkl. Motiv als Bild)
  - `tassen_produkte` – Produktkatalog (Name, Preise, Papier- & Designmaße)
  - `tassen_hintergruende` – Design-Hintergründe
  - `tassen_hgfarben` / `tassen_rahmenfarben` – Hintergrund- & Rahmenfarben
  - `tassen_vorlagen` – Vorlagen
- **Firebase Authentication** (E-Mail/Passwort) – Login fürs Backend
- **Sicherheitsregeln** (`firestore.rules`): Kunden dürfen bestellen & aktive Inhalte **lesen**,
  nur der eingeloggte Admin darf **schreiben**
- Die Kundenseite lädt alle Inhalte aus Firebase, **fällt aber auf eingebaute Standards zurück**,
  falls das Backend leer/offline ist → läuft immer

### Dateien
- `index.html` – die Kundenseite (Produkt-Designer)
- `bestellungen.html` – Bestell- & Inhalts-Verwaltung (mit Login)
- `firestore.rules` – Datenbank-Sicherheitsregeln
- `firebase.json` / `.firebaserc` – Hosting-/Projekt-Konfiguration

## 🎨 Markenlook
Foto-Riede-Grün **#95C11F**, Schrift **Arial**, Logo-Icon (grüner Kreis mit „R"),
Claim „Fotostudio beim Schwarzen Tor".

## ▶️ Lokal testen
Beide Dateien einfach im Browser öffnen (Doppelklick). Für Bestellungen/Backend ist eine
Internetverbindung nötig (Firebase).

## 🚀 Veröffentlichen (Firebase Hosting)
```bash
firebase deploy --only hosting          # Website aktualisieren
firebase deploy --only firestore:rules  # Datenbank-Regeln aktualisieren
```
Live unter **https://foto-riede-fun-produkte.web.app** – diese Adresse wird als Link/Button
auf der Homepage eingebaut.

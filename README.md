# ☕ Foto Riede – Tassen-Designer

Ein Online-Gestalter, mit dem Kunden von **Foto Riede** ihre **persönliche Tasse** selbst
gestalten: **Foto hochladen**, **Text** dazuschreiben, frei verschieben & skalieren – mit
**Live-Vorschau** auf der Tasse. Am Ende schicken sie die Bestellung ab, und sie landet mit
**druckfertigem Motiv** in einem geschützten **Bestell-Backend**.

Gedacht als **eigenständige Seite**, die von der Homepage (foto-riede.de) nur verlinkt wird –
kein Eingriff in die bestehende Homepage nötig.

## Funktionen
- **Produkt & Größe wählen** – Produkte, Preise und Maße kommen live aus dem Backend
- **Gestalten** – Foto-Upload, Text (Schriftart/Farbe), verschieben, skalieren, Tassenfarbe
- **Zwei Maße pro Größe**
  - 📄 **Papiergröße** = das ganze Druckblatt (z. B. 24 × 10 cm, passend zur PSD-Vorlage)
  - 🎨 **Designgröße** = der Gestaltungsbereich (z. B. 20 × 8 cm), als gestrichelter Rahmen
  - Das **Seitenverhältnis der Fläche passt sich automatisch** an die eingetragenen Maße an
- **Kein Kundenlogin** – Kunde gestaltet, bestellt, fertig (Bestätigung „Bestellung eingegangen!“)
- **Bestell-Backend** (`bestellungen.html`, nur für Foto Riede, mit Login):
  - alle Bestellungen live, mit Motiv-Vorschau, Größe, Preis, Summe & Maßen
  - Motiv als druckfertige Datei **herunterladen** (Papiergröße, ~250 DPI)
  - Status setzen (neu → in Arbeit → fertig → abgeholt), löschen
  - **Produkte & Preise** selbst verwalten (anlegen, Größen/Preise/Maße pflegen, aktiv/inaktiv)

## Technik
Reine Frontend-App (HTML/JS, [Fabric.js](https://fabricjs.com) für den Editor). Eigenes
**Firebase-Projekt `foto-riede-tassen`** (getrennt von den anderen Apps):

- **Firestore** `tassen_bestellungen` – eingehende Bestellungen (inkl. Motiv als Bild)
- **Firestore** `tassen_produkte` – Produktkatalog (Name, Preise, Papier- & Designmaße)
- **Firebase Authentication** (E-Mail/Passwort) – Login fürs Backend
- Sicherheitsregeln: Kunden dürfen bestellen & aktive Produkte lesen, nur der eingeloggte
  Admin darf Bestellungen/Produkte verwalten

### Dateien
- `index.html` – die Kundenseite (Tassen-Designer)
- `bestellungen.html` – das Bestell- & Produkt-Backend (mit Login)

## Markenlook
Foto-Riede-Grün **#95C11F**, Schrift **Arial**, Logo-Icon (grüner Kreis mit „R“),
Claim „Fotostudio beim Schwarzen Tor“.

## Lokal testen
Beide Dateien einfach im Browser öffnen (Doppelklick). Für Bestellungen/Backend ist eine
Internetverbindung nötig (Firebase).

## Veröffentlichen
Als statische Seite hostbar (z. B. **Firebase Hosting** → feste Adresse wie
`https://foto-riede-tassen.web.app`). Diese Adresse wird dann nur als Link/Button auf der
Homepage eingebaut.

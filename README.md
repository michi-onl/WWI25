# GrünWohnen – Nachhaltige Studentenwohnungen

**Statisches Website-Projekt für nachhaltiges Wohnen**  
_DHBW Heidenheim | WWI25 Kurs B | Web Design 2025/26_

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## Was ist GrünWohnen?

GrünWohnen ist eine responsive Website für nachhaltige Studentenapartments in Aalen, Heidenheim, Ulm und Herbrechtingen. Das Projekt zeigt moderne Wohnkonzepte mit transparenter CO₂-Bilanz und optimaler ÖPNV-Anbindung.

## Tech Stack

- **HTML5**: Semantisches Markup mit WCAG 2.2 Level A
- **CSS3**: Custom Properties, OKLCH-Farbraum, Variable Fonts
- **Bootstrap 5.3.8**: Responsive Grid & UI-Komponenten
- **RemixIcon 4.1.0**: Icon-Set
- **Geist**: Variable Font (100-900 weights)

## Quick Start

```bash
# VS Code
# Rechtsklick auf index.html → "Open with Live Server"
```

→ Öffne `http://127.0.0.1:5500`

## Features

- ✅ 8+ Seiten mit konsistenten Layouts
- ✅ Responsive Design (320px – 1920px)
- ✅ Automatisches Dark/Light Mode (`prefers-color-scheme`)
- ✅ OKLCH-Farbsystem für wahrnehmungsgleiche Farben
- ✅ WebP-Bilder für optimale Performance
- ✅ Glassmorphism-Navigation mit `backdrop-filter`
- ✅ HTML5-native Formularvalidierung

## Projekt-Struktur

```
WWI25/
├── assets/
│   ├── favicon/       # Favicon-Varianten
│   ├── icons/         # SVG Icons
│   └── images/        # WebP-Bilder
├── css/
│   ├── styles.css     # Haupt-Stylesheet
│   └── fonts/         # Geist Variable Font
├── legal/             # AGB & Datenschutz
├── index.html         # Homepage
├── apartments.html    # Apartment-Übersicht
├── standorte.html     # Standorte mit CO₂-Bilanz
├── nachhaltigkeit.html
├── bewerben.html      # Bewerbungsformular
├── team.html
├── faq.html
└── kontakt.html
```

## Technische Highlights

### OKLCH-Farbraum

Statt RGB/HSL nutzen wir OKLCH für wahrnehmungsgleiche Helligkeit und größeren Farbraum:

```css
:root {
  --primary: oklch(0.4598 0.1116 152.04);
  --accent: oklch(0.6824 0.1503 54.97);
}
```

### Variable Font

Ein einziges WOFF2-File für alle Schriftschnitte (100-900):

```css
@font-face {
  font-family: "Geist";
  font-weight: 100 900;
  src: url("fonts/Geist.woff2") format("woff2");
}
```

### Automatisches Theme-Switching

System-basiert ohne JavaScript-Toggle:

```css
@media (prefers-color-scheme: dark) {
  :root {
    --background: oklch(0.2814 0.0107 118.02);
  }
}
```

## Browser-Support

| Browser | Min. Version | OKLCH | backdrop-filter |
| ------- | ------------ | ----- | --------------- |
| Chrome  | 110+         | ✅    | ✅              |
| Firefox | 113+         | ✅    | ✅              |
| Safari  | 16.4+        | ✅    | ✅              |
| Edge    | 110+         | ✅    | ✅              |

**Hinweis:** OKLCH benötigt Browser ab 2023.

## Performance

- **WebP-Format**: ~30% kleinere Dateigröße vs. JPEG
- **Variable Font**: Ein File statt mehrerer Font-Weights
- **CDN**: Bootstrap & RemixIcon via CDN geladen
- **Keine JavaScript-Frameworks**: Minimaler Overhead

## Erfüllte Anforderungen

✅ Reines HTML/CSS (kein Backend)  
✅ Mindestens 8 Seiten  
✅ 4+ unterschiedliche Layouts  
✅ WCAG 2.2 Level A  
✅ 2+ Browser-Engines getestet  
✅ Framework-Nutzung erlaubt (Bootstrap)

## Hinweise

- **Lokaler Server erforderlich**: Website muss über HTTP-Server geöffnet werden, nicht als `file://`
- **Kein JavaScript**: Projekt erfüllt DHBW-Vorgabe (nur Theme-Detection-Script und Popup-Script)
- **Fiktives Projekt**: Dies ist eine Studierendenarbeit, keine echte Firma

## Lizenz

MIT License – siehe [LICENSE](LICENSE)

## Disclaimer

Dies ist eine Projektwebsite von Studierenden der DHBW Heidenheim für Lernzwecke. Sie repräsentiert nicht die Hochschule und steht in keiner offiziellen Verbindung zur DHBW.

---

**Projekt für:** DHBW Heidenheim | WWI25 Kurs B | Web Design 2025/26

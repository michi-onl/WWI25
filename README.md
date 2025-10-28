# GrünWohnen - Nachhaltige Studentenwohnungen

**Ein statisches Website-Projekt für nachhaltiges studentisches Wohnen**

[![DHBW Heidenheim](https://img.shields.io/badge/DHBW-Heidenheim-red)](https://www.heidenheim.dhbw.de)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.8-7952B3?logo=bootstrap&logoColor=white)](https://getbootstrap.com/)

## 📋 Inhaltsverzeichnis

- [Über das Projekt](#über-das-projekt)
- [Technologie-Stack](#technologie-stack)
- [Installation & Setup](#installation--setup)
- [Projekt-Struktur](#projekt-struktur)
- [Technische Entscheidungen](#technische-entscheidungen)
- [Code-Besonderheiten](#code-besonderheiten)
- [Design-System](#design-system)
- [Testhinweise](#testhinweise)
- [Browser-Unterstützung](#browser-unterstützung)

## 🌱 Über das Projekt

GrünWohnen ist eine statische Website für nachhaltige Studentenwohnungen in Aalen, Heidenheim, Ulm und Herbrechtingen. Das Projekt entstand im Rahmen des Web-Design-Kurses an der DHBW Heidenheim.

**Hauptfunktionen:**

- Apartment-Übersicht mit Filteroptionen
- Standort-Informationen mit ÖPNV-Anbindung und CO<sub>2</sub>-Bilanz
- Bewerbungsformular für Apartments
- FAQ-Bereich mit Accordion-Navigation
- Team- und Kontaktseiten

## 🛠 Technologie-Stack

- **HTML5**: Semantisches Markup
- **CSS3**: Custom Properties, OKLCH-Farbraum, Media Queries
- **JavaScript**: Minimal (nur für Theme-Detection)
- **Bootstrap 5.3.8**: Grid-System und UI-Komponenten
- **RemixIcon 4.1.0**: Icon-Set
- **Custom Fonts**: Geist Font Family (Variable Font)

## 🚀 Installation & Setup

### Voraussetzungen

- Moderner Webbrowser (Chrome 110+, Firefox 113+, Safari 16.4+, Edge 110+)
- Lokaler Webserver (Python, Node.js oder VS Code Live Server)

### Lokale Installation

**Option A: Python HTTP Server**

```bash
cd WWI25
python -m http.server 8000
```

Öffne http://localhost:8000 im Browser

**Option B: VS Code Live Server**

- Installiere \"Live Server\" Extension
- Rechtsklick auf `index.html` → \"Open with Live Server\"

**Option C: Node.js HTTP Server**

```bash
npx http-server
```

## 📁 Projekt-Struktur

```
WWI25/
├── assets/
│   ├── favicon/              # Favicon-Varianten
│   ├── icons/                # SVG Icons (sprout.svg)
│   └── images/               # WebP-Bilder
├── css/
│   ├── styles.css           # Haupt-Stylesheet
│   └── fonts/               # Geist Font (woff2)
├── legal/
│   ├── agb.html
│   └── datenschutz.html
├── index.html               # Homepage
├── apartments.html          # Apartment-Übersicht
├── standorte.html          # Standorte
├── nachhaltigkeit.html     # Nachhaltigkeitsstrategie
├── bewerben.html           # Bewerbungsformular
├── team.html               # Team-Vorstellung
├── faq.html                # FAQ
├── kontakt.html            # Kontaktformular
└── README.md               # Diese Datei
```

## 🔧 Technische Entscheidungen

### Warum OKLCH-Farbraum?

**Entscheidung:** Verwendung von OKLCH statt RGB/HSL für das Farbsystem

**Begründung:**

- **Wahrnehmungsgleichheit**: Farben mit gleichem Lightness-Wert werden vom menschlichen Auge als gleich hell wahrgenommen
- **Größerer Farbraum**: Zugriff auf moderne Display-Capabilities (P3, Rec.2020)
- **Bessere Konsistenz**: Farbvarianten (hell/dunkel) sind vorhersehbarer
- **Zukunftssicherheit**: Moderner Standard für Web-Farbmanagement

**Implementierung:**

```css
:root {
  --primary: oklch(0.4598 0.1116 152.04);
  --body: oklch(0.2621 0.0095 248.19);
  --border: oklch(0.9335 0.0143 128.63);
  --accent: oklch(0.6824 0.1503 54.97);
}
```

### Warum Bootstrap 5.3.8?

**Entscheidung:** Bootstrap als UI-Framework

**Begründung:**

- **Responsive Grid**: Schnelle Umsetzung von Mobile-First-Design
- **Bewährte Komponenten**: Cards, Navbar, Accordion, Forms bereits optimiert
- **Accessibility**: ARIA-Attribute und Tastaturnavigation integriert
- **Konsistenz**: Einheitliches Spacing-System (0.25rem-Schritte)
- **Dokumentation**: Umfangreiche Docs beschleunigen Entwicklung

**Anpassung:** Eigene CSS-Variablen überschreiben Bootstrap-Defaults für individuelle Brand-Identity

### Warum Vanilla JavaScript?

**Entscheidung:** Kein Framework (React, Vue), nur minimales Vanilla JS

**Begründung:**

- **Performance**: Keine Framework-Overhead bei statischer Website
- **Simplicity**: Projekt benötigt keine komplexe State-Management
- **Lernziel**: Fokus auf HTML/CSS-Grundlagen gemäß Kursvorgaben
- **Ladezeit**: Schnellere Initial Page Load ohne Framework-Bundle

**Verwendung:** Nur für `prefers-color-scheme` Detection (automatisches Dark/Light Mode)

### Warum WebP-Format?

**Entscheidung:** WebP statt JPEG/PNG für alle Bilder

**Begründung:**

- **Dateigröße**: ~30% kleiner als JPEG bei gleicher Qualität
- **Browser-Support**: Alle modernen Browser unterstützen WebP (2023+)
- **Performance**: Schnellere Ladezeiten, wichtig für \"Bahnfahrt\"-Test
- **Qualität**: Verlustfreie und verlustbehaftete Kompression möglich

### Warum Custom Fonts (Geist)?

**Entscheidung:** Geist Variable Font als Webfont

**Begründung:**

- **Variable Font**: Ein File für alle Weights (100-900), reduziert HTTP-Requests
- **Moderne Typografie**: Zeitgemäßes, klares Schriftbild
- **Performance**: woff2-Format für optimale Kompression
- **Kontrolle**: Konsistente Darstellung über alle Browser/Betriebssysteme

## 💻 Code-Besonderheiten

### Glassmorphism-Navigation

**Implementierung:** Navigation mit Glas-Effekt

```css
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 28px;
}
```

**Herausforderung:** `backdrop-filter` benötigt Vendor-Prefix für ältere Safari-Versionen

**Lösung:** `-webkit-backdrop-filter` als Fallback hinzugefügt

### Automatisches Theme-Switching

**Implementierung:** System-basiertes Dark/Light Mode ohne JavaScript-Toggle

```css
@media (prefers-color-scheme: light) {
  :root {
    --primary: oklch(0.4598 0.1116 152.04);
    --body: oklch(0.2621 0.0095 248.19);
    /* ... */
  }
}

@media (prefers-color-scheme: dark) {
  :root {
    --primary: oklch(0.5978 0.1184 155.32);
    --body: oklch(0.9109 0.007 247.9);
    /* ... */
  }
}
```

**Vorteil:** Respektiert User-Präferenz auf OS-Level, kein localStorage nötig

### CSS-Architektur

**Struktur:** Organisiertes Stylesheet in logischen Sektionen

```css
/* 1. Font Declarations */
@font-face {
  ...;
}

/* 2. Color System (OKLCH) */
:root {
  ...;
}

/* 3. Global Styles */
* {
  font-family: \"Geist\", sans-serif;
}

/* 4. Theme Switching */
@media (prefers-color-scheme: ...) {
  ...;
}

/* 5. Component Styles */
.navbar {
  ...;
}
.card {
  ...;
}
```

**Vorteil:** Übersichtliche Wartung, klare Trennung von Concerns

### Wiederverwendbare Komponenten

**Navigation-Pattern:** Identische Struktur auf allen Seiten

```html
<nav class=\"navbar navbar-expand-lg glass mx-2\">
  <!-- Logo -->
  <!-- Mobile Toggle -->
  <!-- Navigation Links -->
  <!-- CTA Buttons -->
</nav>
```

**Footer-Pattern:** Einheitlicher Footer über alle Seiten

**Vorteil:** Konsistente UX, einfache Wartung bei Änderungen

### Responsive Images

**Implementierung:** WebP mit beschreibenden Alt-Texten

```html
<img src=\"assets/images/modernes-nachhaltiges-studentenwohnheim.webp\"
alt=\"Modernes Studentenwohnheim mit Solarpanelen und Dachbegrünung\"
class=\"img-fluid rounded\" >
```

**Accessibility:** Detaillierte Alt-Texte für Screen Reader

### Form-Validierung

**Implementierung:** HTML5-native Validierung

```html
<input type=\"email\" required
pattern=\"[a-z0-9._%+-]+@[a-z0-9.-]+\\.[a-z]{2,}$\" class=\"form-control\" >
```

**Vorteil:** Browser-native Validierung, kein JavaScript nötig

## 🎨 Design-System

### Farbsystem (OKLCH)

**Light Mode:**

```css
--primary: oklch(0.4598 0.1116 152.04); /* Grün */
--body: oklch(0.2621 0.0095 248.19); /* Dunkelgrau */
--border: oklch(0.9335 0.0143 128.63); /* Hellgrau */
--accent: oklch(0.6824 0.1503 54.97); /* Orange */
```

**Dark Mode:**

```css
--primary: oklch(0.5978 0.1184 155.32); /* Hellgrün */
--body: oklch(0.9109 0.007 247.9); /* Hellgrau */
--border: oklch(0.3219 0.0205 139.43); /* Dunkelgrau */
--accent: oklch(0.6824 0.1503 54.97); /* Orange */
```

### Typografie

- **Font Family**: Geist (Variable Font, 100-900)
- **Base Size**: 1rem (16px)
- **Line Height**: 1.5
- **Headlines**: `.display-4`, `.display-5`, `.display-6`

### Spacing

- Bootstrap-System: `.p-{0-5}`, `.m-{0-5}`, `.g-{0-5}`
- Custom Gaps: `.gap-3` (1rem), `.gap-4` (1.5rem)

### Komponenten

**Cards:**

```css
.card {
  border-radius: 12px;
  border: 1px solid var(--border);
  transition: transform 0.2s ease;
}
.card:hover {
  transform: translateY(-4px);
}
```

**Buttons:**

```css
.btn-primary {
  background-color: var(--primary);
  border-radius: 28px;
  padding: 0.75rem 1.5rem;
}
```

## 🧪 Testhinweise

### Start der Website

**WICHTIG:** Website muss über lokalen Webserver geöffnet werden, nicht direkt als Datei.

1. Navigiere zum Projektordner `WWI25`
2. Starte lokalen Server (siehe [Installation & Setup](#installation--setup))
3. Öffne `http://localhost:8000` (oder angezeigten Port) im Browser
4. Navigation startet automatisch bei `index.html`

### Browser-Anforderungen

- **Empfohlen:** Chrome 110+, Firefox 113+, Safari 16.4+, Edge 110+
- **OKLCH-Support:** Erforderlich (Browser ab 2023)
- **backdrop-filter:** Erforderlich für Glassmorphism-Effekte

### Bekannte Einschränkungen

**OKLCH-Fallback:**

- Ältere Browser (< 2023) zeigen keine Farben korrekt an
- Keine Fallback-Farben implementiert (moderne Browser-Anforderung gemäß Kurs)

**Glassmorphism:**

- Funktioniert nicht in Browsern ohne `backdrop-filter`-Support
- Ältere Safari-Versionen benötigen `-webkit-` Prefix (bereits implementiert)

**Performance:**

- Webfonts laden asynchron, kurzes FOUT (Flash of Unstyled Text) möglich
- WebP-Bilder optimiert für \"Bahnfahrt\"-Test mit reduzierter Netzwerkgeschwindigkeit

**Mobile Ansicht:**

- Navbar kollabiert auf mobilen Geräten zum Hamburger-Menü
- Einige Elemente vereinfacht für bessere Touch-Bedienbarkeit

### Getestete Szenarien

- ✅ Responsive Design (Desktop, Tablet, Mobile)
- ✅ Dark/Light Mode Switching (automatisch via OS-Einstellung)
- ✅ Formular-Validierung (HTML5-native)
- ✅ Navigation über alle Seiten funktional
- ✅ Bilder laden korrekt (WebP-Format)
- ✅ Externe Links (Bootstrap CDN, RemixIcon CDN)

## 🌐 Browser-Unterstützung

| Browser | Version | Status                     |
| ------- | ------- | -------------------------- |
| Chrome  | 110+    | ✅ Vollständig unterstützt |
| Firefox | 113+    | ✅ Vollständig unterstützt |
| Safari  | 16.4+   | ✅ Vollständig unterstützt |
| Edge    | 110+    | ✅ Vollständig unterstützt |

**Kritische Features:**

- OKLCH Color Space (benötigt Browser 2023+)
- backdrop-filter (Glassmorphism)
- CSS Custom Properties
- WebP Image Format

## 📝 Lizenz & Disclaimer

**Lizenz:** MIT License

**Disclaimer:** Dies ist eine Projektwebsite von Studierenden der DHBW Heidenheim für Lernzwecke. Die Website repräsentiert nicht die Hochschule und steht in keiner offiziellen Verbindung zur DHBW.

---

**Projekt für:** DHBW Heidenheim | WWI25 Kurs B | Web Design 2025/26

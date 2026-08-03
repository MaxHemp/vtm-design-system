# VTM Human Signal · Validierungsbericht

Datum: 3. August 2026
Datei: `VTM-Human-Signal-Editorial-Knowledge-System.html`
Branch: `claude/vtm-master-designsystem-pvuyr8`

## Gegenstand

Vollständig eigenständige Creative-Direction-Datei „Human Signal ·
Editorial Knowledge System" für VTM. Die Originaldatei und
`VTM-Brand-Design-System-Master-Next.html` wurden nicht verändert; die
bestehenden Designsystem-Dateien dienten nur als inhaltliche und
technische Referenz.

## Creative Direction (Kurzbeschreibung)

- **Leitmotiv:** Ein lebendiges Wissenssystem aus Inhalten, Daten,
  Perspektiven und menschlicher Entscheidung. Kein Planeten-, Orbit-
  oder Weltraummotiv: Das räumliche Modell besteht aus überlagerten
  redaktionellen Ebenen, verbundenen Datenpunkten, Informationspfaden
  und verschobenen Ebenen mit Pointer-, Touch- und Scroll-Reaktion.
- **Farbwelt:** Warmes Editorial Paper (#FCFBF7) als Hauptfläche; Deep
  Cobalt für Struktur (Kapitelanker „Experience Levels", Footer),
  Signal Electric und Electric Blue für Aktivität, Research Brass für
  Erkenntnis und Wirkung, zurückhaltendes Coral (Mensch) und Mint
  (positive Zustände). Immersion entsteht über Licht, Ebenen, Schatten,
  transparente Überlagerungen, 1-Pixel-Linien, Konstruktionsachsen,
  Offset-Rahmen und ein SVG-basiertes Film-Grain (Data-URI, kein
  Netzwerkzugriff).
- **Typografie:** Bricolage Grotesque (Display), Instrument Sans
  (UI/Fließtext), Newsreader (Editorial/Zitate), IBM Plex Mono
  (Daten/Indizes). Expressiv eingesetzt: dreizeilige asymmetrische
  Hero-Komposition mit Cobalt-, Electric- und Brass-Newsreader-Zeile,
  Versatz-Zeilen, überlappende Ebenen. Google Fonts nur für die
  Vorschau; lokales WOFF2-Hosting ist in der Datei und in der
  JSON-Spezifikation als Produktionsanforderung dokumentiert.
- **Kapitel:** Immersiver Header → Editorial-Manifest →
  Scrollytelling „Vom Signal zur Entscheidung" (Signal, Connect,
  Structure, Human, Impact) → drei Motivwelten (Human Perspective,
  Systems in Motion, Progress and Impact) → Experience Levels A/B/C →
  Intent-Awareness mit Live-Panel → Machine Experience → dunkler
  Footer-Anker.

## Implementierte Interaktionen

| Interaktion | Umsetzung |
| --- | --- |
| WebGL-Wissenssystem im Header | Direktes WebGL ohne Bibliothek: 84 Punkte, Nachbarschaftslinien, Tiefenparallax auf Pointer, Scroll-Einfluss, Zeitdrift; DPR auf 1,5 begrenzt, `requestAnimationFrame`, pausiert bei verborgenem Tab, pausiert außerhalb des Viewports (IntersectionObserver), deaktiviert bei Reduced Motion/Save Data; SVG-Informationspfade bleiben immer als Grundebene sichtbar |
| Ebenen-Parallax | Redaktionelle Ebenen (Analyse/Research/Praxis) mit `data-depth`, geglättete Pointer-Verfolgung, nur bei feinem Pointer und aktiver Bewegung |
| Scrollytelling | Sticky Bühne mit 5 SVG-Zuständen; IntersectionObserver setzt `data-step`, Beschriftung („Signal … Impact", „n / 5") und aktive Schrittmarkierung; mobile kompakte Sticky-Bühne oberhalb der Schritte; ohne JavaScript Bühne im Endzustand „Impact", alle Texte sichtbar |
| Micro-Interactions | Gerichteter Signalimpuls auf Primärbutton, präzise animierte Link-Unterstreichung, Offset-Schatten-Press-Feedback (`:active` translate), Hover-Verschiebung der Level-Panels, Fokus-Pulse am Live-Indikator, Reveal beim Kapiteleintritt, Scroll-Fortschrittsleiste (Electric→Brass) |
| Motion-Schalter | Global sichtbar, „Bewegung pausieren/aktivieren", dynamisches `aria-label`, sichtbarer Statuspunkt, `aria-live`-Statusregion, `localStorage` mit try/catch, Synchronisation mit `prefers-reduced-motion` und Save Data (dann `aria-disabled`), steuert Ebenen-Drift, Headline-Einstieg, Live-Pulse, Reveal und WebGL |
| Intent-Awareness | Nur lokale Sitzung: INPUT (Touch/Pointer/Tastatur), READING MODE (Scroll-Geschwindigkeit → Lesen/Scannen; beim Scannen sinkt die Bewegungsdichte), ACTIVE TOPIC (Kapitel-Sichtbarkeit, „vertieft" bei wiederholter Interaktion), MOTION, SAVE DATA; kontextbezogene Weiter-Empfehlung; bei Touch rückt der Motion-Schalter in Daumenreichweite; keine Cookies, kein Storage über die Motion-Wahl hinaus, keine Übertragung |

## Validierungsergebnisse

Prüfumgebung: Python 3 (Standardbibliothek), Node 22 (`node --check`),
vorinstalliertes Headless-Chromium. Keine Paketinstallationen.

| Prüfung | Ergebnis |
| --- | --- |
| Vollständiges HTML | ✅ Doctype, je genau ein `html/head/body/main`, schließendes `</html>` |
| Struktur/Verschachtelung | ✅ Parser-Durchlauf ohne offene Tags und ohne Verschachtelungsfehler |
| Doppelte IDs | ✅ 32 IDs, keine Duplikate |
| Interne Links | ✅ Alle `#`-Ziele vorhanden (Navigation, CTAs, Empfehlung, Footer) |
| JavaScript-Syntax | ✅ `node --check` bestanden; Headless-Konsole ohne Seitenfehler |
| JSON-LD | ✅ `json.loads` gültig (schema.org WebPage/WebSite/Organization) |
| Designsystem-JSON | ✅ gültig; enthält alle geforderten Regeln (`examplesAreProductionOrders:false`, `generateMediaWithoutBrief:false`, `copyAsUniversalLayout:false`, `useGenericSaaSPatterns:false`, `humanReviewRequired:true`, `accessibilityRequired:true`, `motionMustHaveMeaning:true`) |
| WebGL-Fallback | ✅ SVG-Informationspfade immer sichtbar; Canvas wird bei fehlendem WebGL, Reduced Motion oder Save Data ausgeblendet (Headless mit `--force-prefers-reduced-motion` verifiziert: `canvas hidden`) |
| Reduced Motion | ✅ Headless verifiziert: `hs-motion-off`, Schalter „Bewegung aktivieren" + `aria-disabled`, Statusregion nennt die Systemeinstellung, Intent-Panel zeigt „Reduziert (System)" |
| Save Data | ✅ Logik-Review: `navigator.connection.saveData` → WebGL aus, Bewegung pausiert, Panel „Ein"; nicht automatisiert erzwingbar |
| Motion-Schalter | ✅ Headless: Standard „Bewegung pausieren"/Status „Bewegung ist aktiv."; Zustand, Beschriftung und `aria-label` synchron |
| Scrollytelling | ✅ Headless: Bühne startet mit JS bei „Signal", folgt den Schritten (verifiziert „Connect · 2/5" mit verbundenem Zustand), aktiver Schritt markiert; ohne JS Endzustand „Impact" im Markup |
| 320-Pixel-Reflow | ✅ DOM-Messung bei exakt 320 px: `scrollWidth = 320`, kein horizontaler Overflow; iFrame-Rendering visuell geprüft (Headline bricht kontrolliert, CTAs full-width, eigenständige vertikale Dramaturgie). Drei Reflow-Fehler wurden im Zuge der Validierung gefunden und behoben (Nav-Flex ohne `min-width:0`; `1fr`-Overrides ohne `minmax(0,1fr)`; Flex-Listenpunkte ohne Umbruch) |
| Desktopdarstellung | ✅ 1440×900: Hero schließt im Viewport ab (Headline, Lead, beide CTAs sichtbar); Sektionen per Headless-Renderings gesichtet |
| Touch-Bedienung | ✅ Code-Review: keine Hover-Abhängigkeit, Press-Feedback über `:active`, Touch-Erkennung positioniert den Motion-Schalter mittig unten; Ziele ≥ 44 px |
| Tastaturbedienung | ✅ Code-Review: ausschließlich native Links/Buttons, sichtbarer Fokus (`:focus-visible`), Skip-Link, keine Fokusfallen |
| Druckausgabe | ✅ Headless-PDF-Export erfolgreich; Overlays/Canvas im Druck ausgeblendet |
| Keine Konsolenfehler | ✅ Headless-Log ohne Seitenfehler (nur umgebungsbedingte dbus-Meldungen des Containers) |
| Keine Bild-/Videogenerierung | ✅ Alle Visual-Referenzen sind code-native SVG/CSS mit `data-media-status="example-only"`, `data-generation-allowed="false"`, `data-example-only="true"` (6 Kennzeichnungen, keine einzige `generation-allowed="true"`) |
| Keine Paketinstallation / Bibliotheken | ✅ Kein Framework, kein Three.js, keine Lottie-Bibliothek, keine externen Skripte (`<script src>`: 0), keine externen Bilder (`<img>`: 0) |
| Keine kostenpflichtigen Aufrufe | ✅ Keine API-Aufrufe; einzige Netzwerkabhängigkeit ist Google Fonts (Vorschau, dokumentiert) |

## Bekannte Einschränkungen

- **Headless-Grenzen:** Echte Touch-Gesten, Tastatur-Traversierung,
  Screenreader-Ausgabe und der Save-Data-Modus sind lokal nicht
  automatisierbar; sie wurden per Code-Review geprüft.
- **WebGL im Headless-Betrieb:** SwiftShader rendert die Szene; echte
  GPU-Performance (DPR, Frame-Zeiten) ist auf Zielgeräten zu
  verifizieren.
- **Direkte 320-px-Screenshots** des Headless-Chromium zeigen einen
  Beschnitt am rechten Rand; das ist ein bekanntes Artefakt des
  Screenshot-Modus (tritt identisch bei den bestehenden
  Designsystem-Dateien auf). Die DOM-Messung und das exakte
  iFrame-Rendering belegen den korrekten Reflow.
- **Google Fonts** bleibt die einzige externe Abhängigkeit der
  Vorschau; lokales WOFF2-Hosting ist als Produktionsanforderung
  dokumentiert (Kapitel Machine Experience und JSON-Spezifikation).
- **WebGPU** ist nur als Zukunftsoption dokumentiert, Lottie nur als
  mögliche spätere Produktionsform; beides ist bewusst nicht
  implementiert.

## Bestätigungen

- ✅ Originaldatei und Master-Next-Datei unverändert (`git status`:
  nur neue Dateien).
- ✅ Keine Bilder oder Videos erzeugt; keine Platzhalterdateien.
- ✅ Keine bezahlten API-Aufrufe, keine Higgsfield-Jobs.
- ✅ Keine Pakete oder Frameworks installiert; Prüfung ausschließlich
  mit vorinstallierten Werkzeugen.
- ✅ Keine neuen Netzwerkabhängigkeiten außer Google Fonts für die
  Vorschau.

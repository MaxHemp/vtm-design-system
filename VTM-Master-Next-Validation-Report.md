# VTM Master-Next · Validierungsbericht

Datum: 22. Juli 2026 (aktualisiert nach Merge-Review)
Branch: `claude/vtm-master-designsystem-pvuyr8`
Review-Empfehlung: **MERGE READY WITH KNOWN LIMITATIONS** (siehe Abschnitt „Abschließender Merge-Review“)

## Dateien

| Rolle | Datei |
| --- | --- |
| Ausgangsdatei (unverändert) | `VTM-Brand-Design-System-4.2-Luminous-Editorial-Original.html.html` |
| Ausgabedatei (Arbeitsfassung) | `VTM-Brand-Design-System-Master-Next.html` |
| Prüfbericht | `VTM-Master-Next-Validation-Report.md` |

Hinweis: Die Originaldatei liegt im Repository mit doppelter Endung
`.html.html` vor. Sie wurde bewusst **nicht** umbenannt, um die
Anforderung „Originaldatei unverändert“ ohne Interpretationsspielraum zu
erfüllen.

## Ergänzte Kapitel

Die Arbeitsfassung erweitert die 11 Kapitel der Version 4.2 additiv um:

| Nr. | ID | Inhalt |
| --- | --- | --- |
| 00 | `system-verstehen` | Zweck, Prioritätsregel (7 Stufen), Statussystem, verbindliche Interpretationsregel |
| – | `inhaltsuebersicht` | Zugängliche, responsive Inhaltsübersicht in 7 Themenbereichen (A–G) mit Sprunglinks zu allen Hauptkapiteln |
| 12 | `foundations` | Layoutmodi (720/1200/1440/Full Bleed), Raster (4/6/12 Spalten, min. 320 px), Spacing-Skala, Formen & Tiefe, Iconografie |
| 13 | `verlaufsregeln` | Einsatzregeln für Brand Gradient, Signature Gradient, Electric/Brass Beam, Hero Atmosphere |
| 14 | `medienklassifizierung` | `data-*`-Konvention (Rollen, Status, Flags), Klassifizierungstabelle, Demo-Kennzeichnung |
| 15 | `video-medien` | Video als optionales Medium, technische Regeln, Medienbudgets (250 KB / 450 KB / 2,5 MB / 5 MB) |
| 16 | `motion-system` | Motion Level 0/1/2, Dokumentation des globalen Motion-Schalters |
| 17 | `ui-komponenten` | Navigation, Breadcrumbs, Formulare/Validierung, Tabellen, Lade-/Leer-/Fehlerzustände, Dialoge, verbindliche UI-Regeln |
| 18 | `websites-landingpages` | Corporate-Aufbau, Editorial-Formate, Landingpage-Regeln (erlaubt / nicht erlaubt) |
| 19 | `webanwendungen` | Verbindliche App-Regeln, Nicht-Übernahme-Liste, Angebotssoftware ausschließlich als `component-demonstration` |
| 20 | `praesentationen` | 12 Folientypen als Demos, Gestaltungsregeln; keine PPTX-Datei erzeugt |
| 21 | `dokumente` | Angebots-/Report-Struktur, Geschäftsbrief-Muster mit Regeln; keine DOCX/PDF erzeugt |
| 22 | `email-newsletter` | Signatur- und Newsletter-Regeln mit Beispielsignatur; keine separate E-Mail-Datei |
| 23 | `anwendungsmatrix` | Zugängliche Tabelle: Bilder / Hintergrundvideo / max. Motion Level je Anwendung (10 Zeilen) |
| 24 | `accessibility-performance` | WCAG-2.2-AA-Prüfpunkte, Performanceziele (LCP/INP/CLS, lange Tasks, lokale WOFF2) |
| 25 | `assetvertrag` | Assetvertrag-Pflichtfelder, Produktionsprozess Brief → … → Published, Zusatzstatus |
| 26 | `ki-regeln` | Regeln für generative KI (erlaubt / menschlich verantwortet / verboten) |
| 27 | `claude-anwendung` | Grundregel, 10 Pflichten, 8 Verbote, Zugriff auf die JSON-Spezifikation |

## Technische Änderungen (Kurzbeschreibung)

Alle Änderungen sind additiv; kein bestehendes Token, kein Verlauf, keine
Komponente und kein Inhalt der Version 4.2 wurde entfernt oder
abgeschwächt.

1. **CSS:** Ein klar abgegrenzter Block „MASTER-NEXT · ADDITIVE
   ERWEITERUNG“ am Ende des Stylesheets (Statusbadges, TOC,
   Motion-Schalter, Demo-Komponenten, eigene Responsive-, Forced-Colors-,
   Reduced-Motion- und Print-Ergänzungen).
2. **Navigation:** Die Sticky-Navigation bleibt erhalten; ergänzt wurde
   genau ein Link („Inhalt“ → `#inhaltsuebersicht`), um die horizontale
   Navigation nicht zu überladen.
3. **Medienklassifizierung:** Bestehende Elemente erhielten additive
   `data-asset-id`-, `data-media-role`-, `data-media-status`- und
   Flag-Attribute (Logos, Hero-Atmosphäre, Signal Lines, Story-Visuals,
   Bildsprache-Platzhalter, Modernisierungsdiagramm, Newsletter-Formular,
   Artikel-Demo). Kein Asset trägt `production-required`.
4. **Motion-Schalter:** Globaler Button (fixiert, unten rechts) mit
   dynamischem `aria-label`, sichtbarem Status, `localStorage`-Speicherung
   in `try/catch`, Synchronisation mit `prefers-reduced-motion` und
   Statusregion (`aria-live="polite"`). Der Pausenstatus stoppt Brand
   Rail, Hero Orbits, Hero Signal, Hero Nodes, Panel Glint, Signal Pass
   und Research Glint. Ohne JavaScript bleibt der Button verborgen
   (`hidden`), alle Inhalte bleiben sichtbar.
5. **JSON-Spezifikation:** `<script type="application/json"
   id="vtm-design-system-specification">` mit Systemidentität,
   Interpretationsregeln, Prioritätsreihenfolge, Statussystem,
   Motion-Leveln, Anwendungsmatrix (10 Zeilen), Medienklassifizierung,
   Produktionsworkflow, Assetregister (12 Einträge, unbekannte Werte
   `null`/`pending`) und dokumentierten offenen Abhängigkeiten.
6. **Notwendige Anpassungen bestehender Inhalte** (dokumentationspflichtig):
   - `<title>` und Meta-Description: Kennzeichnung als Arbeitsfassung
     „Master-Next“ (eindeutige Maschinen-/Menschenlesbarkeit; keine neue
     Versionsnummer).
   - Hero-Eyebrow: „Brand & Design System · 4.2 · Arbeitsfassung
     Master-Next“.
   - Footer-Dokumentblock: Zusatzzeile „Arbeitsfassung Master-Next ·
     Entwurf“.
   Alle übrigen Inhalte der Version 4.2 sind unverändert.

## Prüfergebnisse

Prüfumgebung: Python 3 (Standardbibliothek), Node 22 (`node --check`),
vorinstalliertes Headless-Chromium. Es wurden **keine Pakete
installiert**.

| Prüfung | Ergebnis |
| --- | --- |
| Vollständiges HTML-Dokument | ✅ Doctype, je genau ein `html/head/body/main`, Datei endet mit `</html>` |
| HTML-Grundstruktur / ungeschlossene Elemente / Verschachtelung | ✅ Eigener Parser-Durchlauf (html.parser): keine offenen Tags, keine Verschachtelungsfehler |
| Doppelte IDs | ✅ 80 IDs, keine Duplikate |
| Interne Ankerziele | ✅ Alle `#`-Links (Navigation, TOC, Inhalte) haben existierende Ziele |
| JavaScript-Syntax | ✅ Beide Inline-Skripte bestehen `node --check`; Headless-Konsole ohne Fehler |
| JSON-Spezifikation | ✅ `json.loads` gültig; Matrix 10 Zeilen, Register 12 Assets, 11 Interpretationsregeln |
| Motion-Schalter (Logik) | ✅ Headless-Test: Standardzustand „Bewegung pausieren“/Status „aktiv“; mit `--force-prefers-reduced-motion` wird `motion-paused` gesetzt, Label wechselt auf „Bewegung aktivieren“, Statusregion nennt die Systemeinstellung |
| Keine Kerninhalte durch JavaScript verborgen | ✅ Reveal-Effekte nur unter `.motion-enabled`; Grundzustand aller Inhalte ist sichtbar |
| Verhalten ohne JavaScript | ✅ Inhalte vollständig sichtbar; Motion-Button bleibt `hidden` (Code-Review; kein JS-Zustand erforderlich) |
| Reduced Motion | ✅ Bestehende globale Regeln unverändert; Schalter synchronisiert (Headless getestet) |
| 320-Pixel-Reflow | ✅ soweit lokal prüfbar: Screenshot bei 320 px; sichtbarer Randbeschnitt ist ein Headless-Screenshot-Artefakt und tritt identisch beim unveränderten Original auf (Vergleichsrender) |
| Tabellen und Formulare | ✅ Code-Review: `caption`, `scope`, sichtbare Labels, `aria-describedby`, Fehlerdemo mit `aria-invalid`; alle Tabellen in scrollbaren `.table-wrap`-Containern |
| Fokuszustände | ✅ Globales `:focus-visible` der 4.2 gilt auch für neue Komponenten (Code-Review) |
| Druckdarstellung | ✅ Headless `--print-to-pdf` erfolgreich (100 Seiten); Motion-Button im Druck ausgeblendet, neue Demos mit `break-inside: avoid` |
| Keine neu hinzugefügten externen Requests | ✅ Ladende Ressourcen unverändert: Google-Fonts-CSS + zwei Ghost-Logo-URLs (Vorschauabhängigkeiten der 4.2). Neu sind ausschließlich Link-Ziele ohne Ladevorgang (`tel:`, `mailto:`, Website-Link in der Signatur-Demo) |
| Originaldatei unverändert | ✅ MD5 `16c1b9c05803505e5a2599b223e7fe71` vor und nach der Bearbeitung identisch; `git status` zeigt keine Änderung an der Originaldatei |

### Accessibility-Prüfpunkte (durchgeführt)

- Statusstufen werden durch Text + Badge kommuniziert, nie nur durch Farbe.
- Neue Navigationselemente (`nav`-Landmarken mit `aria-label`, Breadcrumb
  mit `aria-current="page"`).
- Motion-Schalter: dynamisches `aria-label`, sichtbare Beschriftung,
  `role="status"`-Region.
- Formulardemos: sichtbare Labels, Fehlertext am Feld,
  `aria-invalid`/`aria-describedby`.
- Demo-Elemente ohne Informationsgehalt tragen `aria-hidden="true"`.
- Touch-Ziele der neuen Bedienelemente: min. 44 px Höhe (`min-height`).

### Responsive-Prüfpunkte (durchgeführt)

- Neue Grids (TOC, Foliengrid, App-Shell, Briefkopf) brechen bei 1080 px /
  760 px / 520 px kontrolliert um.
- Breite Inhalte (Tabellen, App-Shell-Tabelle) scrollen in eigenen
  Containern; die Seite selbst scrollt nicht horizontal
  (`body { overflow-x: hidden; min-width: 320px }` aus 4.2 unverändert).
- Desktop- (1280 px) und Mobile-Render (320 px) per Headless-Chromium
  gesichtet.

## Nicht automatisiert geprüft

Ehrliche Einschränkungen der lokalen Prüfumgebung:

- **Screenreader-Verhalten** (NVDA/VoiceOver): nicht automatisiert
  prüfbar; Struktur- und ARIA-Review erfolgte im Code.
- **Forced-Colors-Darstellung**: CSS-Regeln ergänzt, aber kein visueller
  Test in einem Forced-Colors-Betriebssystemmodus.
- **Echte Endgeräte / Browser-Matrix** (Safari, Firefox, Mobile): nur
  Chromium headless getestet.
- **Kontrastmessung auf gerenderten Verläufen**: nicht instrumentell
  gemessen; es wurden ausschließlich bestehende, in 4.2 freigegebene
  Farbkombinationen wiederverwendet.
- **Felddaten-Performance (LCP/INP/CLS)**: als Ziele dokumentiert; lokal
  ohne Messinfrastruktur nicht erhebbar.

## Verbleibende externe Abhängigkeiten (dokumentiert, nicht heruntergeladen)

| Abhängigkeit | Zweck | Produktionsanforderung |
| --- | --- | --- |
| `fonts.googleapis.com` / `fonts.gstatic.com` | Vorschau der vier Markenschriften | Lokales WOFF2-Hosting |
| `storage.ghost.io/...Logo--2-.png` | Farbiges VTM-Logo (Vorschau) | Lokale Ablage `./assets/logos/` |
| `storage.ghost.io/...versicherungstech_logo_white.png` | Weißes VTM-Logo (Vorschau) | Lokale Ablage `./assets/logos/` |

Diese Abhängigkeiten stammen unverändert aus der Originaldatei und sind
zusätzlich in der JSON-Spezifikation unter `openDependencies` erfasst.

## Abschließender Merge-Review (22. Juli 2026)

Vor dem Merge wurden die zehn Review-Punkte gezielt geprüft
(Diff-Analyse, Skript-Prüfungen, Headless-Chromium-Renderings von
Inhaltsübersicht und neuen Kapiteln bei 1280 px und 320 px):

1. **Identität erhalten:** Das komplette Original-CSS und -JavaScript ist
   verbatim in der Arbeitsfassung enthalten (programmatisch geprüft; die
   einzige Abweichung ist Whitespace am Übergang zum additiven Block).
   Alle Kernfarben (#121E39, #123FA6, #2468E8, #C99B32), alle sechs
   Verlaufs-Token und alle vier Schriftrollen kommen exakt so oft vor wie
   im Original und sind im Rendering sichtbar.
2. **Keine Kapitel-Duplikate:** 29 Sections, alle IDs eindeutig; alle 11
   Originalkapitel unverändert vorhanden; `data-index` 00–27 ohne
   Doppelungen.
3. **Löschungen im Diff:** Der Datei-Diff Original → Master-Next weist
   9 entfernte Zeilen aus, die 7 logischen Änderungen entsprechen (drei
   identische Story-Visual-Zeilen zählen als eine Änderung). Jede ist
   eine beabsichtigte Ersetzung derselben Zeile durch eine erweiterte
   Fassung – es wurde kein Inhalt entfernt:
   1. Meta-Description → um Master-Next-Kennzeichnung erweitert
      (Maschinenlesbarkeit der Arbeitsfassung).
   2. `<title>` → „VTM Brand & Design System · Master-Next“
      (eindeutige Bezeichnung, keine neue Versionsnummer).
   3. Hero-Eyebrow → „… · 4.2 · Arbeitsfassung Master-Next“
      (sichtbare Kennzeichnung der Arbeitsfassung).
   4. `<div class="hero-atmosphere">` → um `data-media-role`/
      `data-media-status="code-native"` erweitert (Pflichtkennzeichnung).
   5. `<div class="grid-3">` (Story-System) → `data-example-only="true"`
      ergänzt (Beispielkennzeichnung).
   6. 3 × `<div class="story-visual">` → um `component-demonstration`-
      Attribute erweitert (Pflichtkennzeichnung).
   7. `<div id="article-demo">` → `data-example-only="true"` ergänzt
      (Beispielkennzeichnung).
   Keine Löschung betrifft CSS, JavaScript, Tokens, Verläufe oder
   redaktionelle Inhalte.
4. **Komponentenkonsistenz:** Alle neuen Kapitel nutzen die vorhandenen
   VTM-Bausteine (`chapter-head` mit Stroke-Index, `kicker`, `card`,
   `card-dark`, `card-research`, `table-wrap`, `rule-list`,
   `number-list`, `note`, `tag`/`status`, `compare-card`); per Rendering
   der Kapitel 12, 19, 20, 23, 24 verifiziert – kein zweites Designsystem.
5. **Navigation & Inhaltsübersicht:** Desktop-Rendering zeigt die
   unveränderte Sticky-Navigation (+1 Link „Inhalt“) und die
   TOC-Gruppen A–G dreispaltig; bei 320 px bricht die Übersicht sauber
   einspaltig um, Links mit ≥32 px Höhe, Hauptnavigation horizontal
   scrollbar wie im Original.
6. **Motion-Schalter:** Sichtbar (fixiert unten rechts), nativer
   `<button>` (tastaturbedienbar, globales `:focus-visible`).
   Headless-getestet: Standard „Bewegung pausieren“/Status „aktiv“;
   bei Systemeinstellung Reduced Motion „Bewegung aktivieren“ +
   Statusregion-Hinweis. **Korrektur im Review:** Ist Reduced Motion
   systemseitig aktiv, trägt der Schalter jetzt zusätzlich
   `aria-disabled="true"` (mit abgesenkter Optik), da die
   Systemeinstellung Vorrang hat und ein Klick die Animationen nicht
   reaktivieren kann. Beschriftung und tatsächlicher Zustand stimmen in
   allen Zuständen überein.
7. **Assetregister:** Kein Eintrag mit `production-required`, kein
   Eintrag mit `generationAllowed: true` (programmatisch geprüft). Der
   String `data-generation-allowed="true"` existiert ausschließlich als
   `<code>`-Zitat der geforderten Interpretationsregel in Kapitel 00 –
   kein Element trägt ihn als Attribut.
8. **Logos:** Alle 6 Logo-Elemente (Nav, 2 Specimens, Schutzraum,
   2 Footer) tragen `data-media-status="approved-brand-asset"` und
   `data-generation-allowed="false"`; Register bestätigt beide Logos als
   `approved-brand-asset` mit Generierungsverbot und Human-Review-Pflicht.
9. **Beispielkennzeichnung:** 22 × `data-example-only`; Beispieldaten,
   Bildplatzhalter, Angebotssoftware-Ansicht und Foliensystem sind
   dreifach gekennzeichnet (data-Attribute, sichtbare Badges
   „Beispiel“/„Kein Produktionsauftrag“, Registereinträge).
10. **Externe Zugriffe:** Ladende Ressourcen unverändert (Hosts:
    fonts.googleapis.com, fonts.gstatic.com, storage.ghost.io); keine
    neuen `preconnect`-Einträge, keine externen `<script src>`. Einzige
    neue externe URL ist das reine Linkziel
    `https://www.versicherungstech-magazin.de` in der
    E-Mail-Signatur-Demo (Kapitel 22 verlangt „Website als echte Links“);
    es wird beim Seitenaufruf nicht geladen und erzeugt keine
    Abhängigkeit. Als bekannte Einschränkung ausgewiesen.

**Review-Korrekturen:** ausschließlich die unter Punkt 6 beschriebene
`aria-disabled`-Ergänzung (JS + 5 Zeilen CSS). Keine neuen Kapitel,
keine Medien, keine gestalterischen Änderungen.

**Empfehlung: MERGE READY WITH KNOWN LIMITATIONS** – die bekannten
Einschränkungen sind die oben dokumentierten, lokal nicht
automatisierbaren Prüfungen (Screenreader, Forced-Colors-Anzeige,
Browser-Matrix, instrumentelle Kontrastmessung) sowie das Link-only-Ziel
aus Punkt 10. Blocker bestehen keine.

## Bestätigungen

- ✅ Die Originaldatei blieb byteidentisch unverändert (MD5-geprüft).
- ✅ Es wurden **keine Bilder und keine Videos erzeugt** – auch keine
  Platzhalterdateien; alle Beispiele sind code-nativ (HTML/CSS/SVG inline).
- ✅ Es erfolgten **keine bezahlten API-Aufrufe** und keine
  Higgsfield-Jobs.
- ✅ Es wurden **keine Pakete oder Frameworks installiert** (kein React,
  Vue, Angular, Tailwind, keine Animationsbibliotheken); die Prüfung
  nutzte ausschließlich vorinstallierte Werkzeuge.
- ✅ Es wurden keine Logos, Fonts, Bilder oder Videos heruntergeladen.
- ✅ Keine Umbenennung in Version 5.x; die Arbeitsfassung heißt
  ausschließlich „Master-Next“ (Status: draft).

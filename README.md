# Glace Administration — Website Setup-Anleitung

## Übersicht der Dateien

```
glace-administration/
├── index.html          ← Hauptseite
├── impressum.html      ← Impressum / Datenschutz
├── css/
│   └── style.css       ← Alle Styles
├── CNAME               ← Wird in Schritt 2 erstellt
└── README.md           ← Diese Datei
```

---

## Schritt 1: GitHub Repository erstellen & Website hochladen

1. **GitHub-Account erstellen** (falls noch nicht vorhanden): [github.com](https://github.com)

2. **Neues Repository anlegen:**
   - Klicke auf das **+** oben rechts → **New repository**
   - **Repository-Name:** `glace-administration` (oder ein Name deiner Wahl)
   - **Public** auswählen (muss public sein für kostenloses GitHub Pages)
   - Klicke auf **Create repository**

3. **Dateien hochladen:**
   - Im Repository auf **Add file → Upload files** klicken
   - Alle Dateien und den `css/`-Ordner per Drag & Drop hochladen
   - Unten auf **Commit changes** klicken

## Schritt 2: GitHub Pages aktivieren

1. Im Repository → **Settings** (oben rechts)
2. Links im Menü → **Pages**
3. Unter **Source** auswählen:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
4. Auf **Save** klicken
5. Nach ca. 1–2 Minuten ist die Seite verfügbar unter:
   `https://DEIN-USERNAME.github.io/glace-administration/`

## Schritt 3: IONOS Domain mit GitHub Pages verbinden

### 3a) CNAME-Datei im Repository erstellen

1. Im Repository → **Add file → Create new file**
2. Dateiname: `CNAME`
3. Inhalt (nur eine Zeile — deine Domain):
   ```
   www.deine-domain.de
   ```
4. **Commit changes** klicken

### 3b) DNS bei IONOS konfigurieren

1. Bei [IONOS einloggen](https://my.ionos.de)
2. Gehe zu **Domains & SSL** → Deine Domain auswählen
3. Klicke auf **DNS** bzw. **DNS-Einstellungen**

4. **Bestehende A-Records löschen** (die Standard-IONOS-Einträge)

5. **Vier A-Records erstellen** (für die Root-Domain, z. B. `deine-domain.de`):

   | Typ | Hostname | Ziel / Wert |
   |-----|----------|-------------|
   | A   | @        | `185.199.108.153` |
   | A   | @        | `185.199.109.153` |
   | A   | @        | `185.199.110.153` |
   | A   | @        | `185.199.111.153` |

6. **Einen CNAME-Record erstellen** (für `www`):

   | Typ   | Hostname | Ziel / Wert |
   |-------|----------|-------------|
   | CNAME | www      | `DEIN-USERNAME.github.io` |

   *(Ersetze `DEIN-USERNAME` durch deinen GitHub-Benutzernamen)*

### 3c) Custom Domain in GitHub Pages eintragen

1. Zurück im Repository → **Settings → Pages**
2. Unter **Custom domain** eintragen: `www.deine-domain.de`
3. Auf **Save** klicken
4. Warte, bis der DNS-Check grün wird (kann bis zu 24 Stunden dauern, meist aber wenige Minuten)
5. **Enforce HTTPS** aktivieren (Checkbox ankreuzen, sobald verfügbar)

## Schritt 4: Überprüfen

Nach der DNS-Propagation (kann 10 Minuten bis 24 Stunden dauern):

- `https://deine-domain.de` → leitet zu `https://www.deine-domain.de` weiter
- `https://www.deine-domain.de` → zeigt deine Website

### Troubleshooting

| Problem | Lösung |
|---------|--------|
| Seite zeigt 404 | Prüfe, ob `index.html` im Root des Repos liegt |
| DNS-Check schlägt fehl | A-Records und CNAME nochmal prüfen; IONOS-Cache kann bis 48h brauchen |
| Kein HTTPS | Warte bis der DNS-Check grün ist, dann „Enforce HTTPS" aktivieren |
| CSS lädt nicht | Prüfe, ob der `css/`-Ordner korrekt hochgeladen wurde |

---

## Personalisierung — Was du noch anpassen solltest

### Pflicht (Impressum):
- **`impressum.html`** — Ersetze alle Platzhalter:
  - `Dein Vorname Nachname` → dein echter Name
  - `Musterstraße 1` → deine Adresse
  - `12345 Musterstadt` → deine PLZ und Stadt

### Empfohlen:
- **`index.html`** — Kontaktdaten anpassen:
  - E-Mail-Adresse (`kontakt@glace-admin.de`) → deine echte E-Mail
  - Discord-Link → deinen tatsächlichen Discord-Server/Einladungslink
  - Zahlen in der Stats-Bar (50+, etc.) → deine echten Werte
  - Referenzen → deine tatsächlichen Projekte und Erfahrungen

### Optional:
- Eigenes Favicon hinzufügen (als `favicon.ico` oder `favicon.png`)
- Open Graph Bild für Social Media Previews (`og:image` Meta-Tag)
- Google Search Console einrichten für SEO

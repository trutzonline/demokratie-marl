# demokratie-marl.de

Website der **Demokratie AG Marl**: ein einfacher Blog mit Jekyll, gehostet über GitHub Pages.

- Startseite: neuester Beitrag groß, ältere Beiträge als Kacheln
- Seiten: Über uns, Impressum, Datenschutz
- Keine Cookies, kein Tracking, Schriften lokal eingebunden
- RSS-Feed (`/feed.xml`) und Sitemap werden automatisch erzeugt

## Einen neuen Artikel schreiben

1. Im Ordner `_posts/` eine neue Datei anlegen. Der Name muss so aussehen:
   `JJJJ-MM-TT-kurzer-titel.md`, z. B. `2026-12-03-veranstaltung-pauluskirche.md`
2. Oben in die Datei diesen Kopf schreiben, darunter den Text in Markdown:

   ```markdown
   ---
   title: Überschrift des Artikels
   author: Demokratie AG Marl        # optional
   image: /assets/img/beitraege/bild.jpg   # optional
   image_alt: Kurze Bildbeschreibung       # optional, für Screenreader
   teaser: Kurzer Text für die Kachel      # optional
   ---

   Erster Absatz …

   <!--more-->

   Rest des Artikels …
   ```

3. Speichern, committen, pushen. Nach ca. einer Minute ist der Artikel online.

**Hinweise**

- Der neueste Beitrag (nach Datum) erscheint automatisch groß auf der Startseite.
  Alles **vor** `<!--more-->` wird dort angezeigt, dazu ein Button „Ganzen Artikel lesen“.
  Ohne `<!--more-->` steht der ganze Artikel auf der Startseite.
- In den Kacheln wird automatisch der Anfang des Textes gezeigt oder, falls angegeben, der `teaser`.
- Bilder in `assets/img/beitraege/` ablegen, am besten vorher auf ca. 1600 px Breite verkleinern.
- Ein Artikel mit Datum in der Zukunft wird erst veröffentlicht, wenn das Datum erreicht ist und die Seite neu gebaut wird.

## Aufbau

```
_config.yml          Titel, Slogan, Navigation, Domain
_posts/              Die Artikel (Markdown)
_layouts/            Seitenvorlagen (home, post, page, default)
_includes/           Kopf, Fuß, Kachel, deutsches Datum
assets/css/style.css Design (Farben aus dem Logo)
assets/img/          Logo, Favicon, Vorschaubild
assets/fonts/        Schriften Fredoka & Nunito (SIL Open Font License)
ueber-uns.md         Über-uns-Seite
impressum.md         Impressum (vor dem Livegang ausfüllen!)
datenschutz.md       Datenschutzerklärung (vor dem Livegang ausfüllen!)
CNAME                Eigene Domain für GitHub Pages
```

## Lokale Vorschau (optional)

Voraussetzung: Ruby ist installiert.

```bash
bundle install
bundle exec jekyll serve
```

Dann im Browser <http://localhost:4000> öffnen.

## Veröffentlichen mit GitHub Pages

1. Repository auf GitHub anlegen und diesen Ordner hochladen.
2. Auf GitHub: **Settings → Pages** → Source „Deploy from a branch“, Branch `main`, Ordner `/ (root)`.
3. Unter **Custom domain** `demokratie-marl.de` eintragen (steht auch schon in der Datei `CNAME`).
4. Empfohlen: Domain im GitHub-Account verifizieren (**Profil-Settings → Pages → Add a domain**),
   damit niemand anderes sie für eine eigene Seite verwenden kann.

### DNS-Einträge bei united-domains

| Typ   | Name | Wert                  |
|-------|------|-----------------------|
| A     | @    | 185.199.108.153       |
| A     | @    | 185.199.109.153       |
| A     | @    | 185.199.110.153       |
| A     | @    | 185.199.111.153       |
| AAAA  | @    | 2606:50c0:8000::153   |
| AAAA  | @    | 2606:50c0:8001::153   |
| AAAA  | @    | 2606:50c0:8002::153   |
| AAAA  | @    | 2606:50c0:8003::153   |
| CNAME | www  | `<github-name>.github.io` |

Vorhandene A-/AAAA-Einträge (z. B. Parkseite von united-domains) vorher entfernen.
Sobald GitHub die Domain erkannt hat (kann bis zu 24 h dauern), unter **Settings → Pages**
den Haken bei **Enforce HTTPS** setzen.

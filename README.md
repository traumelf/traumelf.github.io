# Meine Traumelf

## Layout

### Mobile first

Die Seite reagiert auf die Größe des Bildschirms.

| Größe | Name | Variable | Verhalten | Testfarbe |
| :- | :- | :- | :- | :- |
| < 600px | Mobile | - | eine Spalte ohne sidebar | Pink |
| 600px bis 767px | Mobile landscape | $on-palm | eine Spalte ohne sidebar | Rot |
| 768px bis 991px | IPad | $on-laptop | zwei Spalten ohne sidebar | Grün |
| 992px bis 1199px | IPad Pro | $on-desktop | eine Spalte mit sidebar | Blau |
| 1200px + | Desktop | $on-wide-screen | zwei Spalten mit sidebar | Orange |


### Verfügbare Layouts

- default
  - layout-with-sidebar
    - home
    - about
    - post
    - spieler
    - suche
    - trainer
    - vereine
  - verein-layout-with-sidbar
    - verein


### Sidebar

Die Einstellungen zur Sidebar findet man in base.scss unter .wrapper
Die Spaltenaufteilung des Contents sind unter page.scss und post.scss konfiguriert.

```yml
// outter
display: grid;
grid-template-columns: repeat(6, 1fr);
grid-gap: $spacing-unit / 4;

//inner
display: flex;
flex-direction: column;
```

## Content

### Artikel erzeugen

1. Im  Ordner 'posts' eine neue Datei angelegen.
2. Der Name der Datei ist nach einem festen Schema anzulegen: "YYYY-MM-dd-vorname-nachname.md"
3. In der Datei ist oben der sogenannte "front matter" anzulegen.

Beispiel "front matter"

```yml
---
layout: post
title: Vorname Nachname
vgworttrackingid: abc123
author:
  display_name: Lukas große Klönne
  email: lgrkloenne@gmail.com
excerpt: 'Text auf der Startseite'
intro: 'Der Intro-Text im Artikel.'
description: 'Dieser Text wird ins meta.tag eingefügt'
categories:
- Spieler
tags:
- 1 FC Holzhausen
- FC St Pauli
images:
  person: Name-des-Spielers.png
  lineup: Name-der-Aufstellungsdatei.png
imagecredits: some / credits
---
{%- include post/intro-image-and-tactics.html -%}
```


Hinweise
* Die 3 Striche am Anfang und am Ende des front matter sind Pflicht.
* Die Texte für excerpt und intro sollten immer in Hochkomma stehen. Das ist zwar nicht immer notwendig verhindert aber Fehler.
* Die Variable description kann (muss nicht) gesetzt werden und überschreibt die globale description-Variable aus config.yml
* Im Feld "categories" ist nur eine Kategorie erlaubt. Entweder "Spieler" oder "Trainer".
* Die Tags dürfen über die Seite nur einmal existieren. Bitte nachsehen, ob das Tag schon vergeben wurde und es genau wie im alten Artikel stehend wieder verwenden. Ist es neu so kann man es einfach niederschreiben. Das Tag darf keine Umlaute enthalten, auch wenn es im Frontend mit Umlaut erscheint. Ebenso dürfen keine Punkte in den Tags enhalten sein. In der Browser-Zeile sieht man das ausgeschriebene Tag.
* Datei images/person muss unter "assets/images/person" liegen
* Datei images/linup muss unter "assets/images/linup" liegen
* Das include ist nicht Teil des front matter jedoch gehört es immer an den Anfang eines Artikels. Darüber werden die obigen Grafiken und Texte eingebunden.
* Danach kannst du im Markdown-Stil einen Artikel schreiben.

### Artikelstruktur

Auf Basis der bestehenden Artikel hat sich eine Struktur durchgesetzt, die stets gleich oder sehr ähnlich sein sollte. Headline der Kategorie 1 wird automatisch erzeugt. Ebenso eine weitere der Kategorie 2. Es kann also direkt mit den Spielernamen als Headline Kat. 3 bekonnen werden. Kategorie 2 folgt später noch einmal zum Ende des Artikels.

Beispiel-Struktur der Überschriften nach dem ersten include:

```
### Spieler 1 // Position // Team 1

### Spieler 2 // Position // Team 2

### Spieler n // Position // Team n

## Karriere-Insights

### Überschrift Kat 3

### Überschrift Kat 3
```

### VG-Wort

Das vgwort include wird in layout "post.html" an die Posts gehängt. Darüber wird die im "front matter" vergebene "vgwort_tracking_id" in jeden Artikel eingebunden.

### Werdegang Tabelle

Je Artikel soll eine Tabelle des Werdegangs stehen. Wichtig ist die korrekte Verschachtelung der HTML Tabellen-Tags. Hier ein HTML-Snippet:

```html
<table>
<tbody>
<tr><th>Jahre</th><th>Verein</th><th>Spiele (Tore)</th></tr>
<tr><td>1984–1986</td><td>BSG Chemie Leipzig</td><td>58 (15)</td></tr>
<tr><td>1986-1990</td><td>1. FC Lokomotive Leipzig</td><td>86 (2)</td></tr>
</tbody>
</table>
```

### Bilder und Videos

Für das Einbinden werden 2 includes bereitgestellt. Nach dem include sollte jeweils ein Kommentar in einem em-tag folgen.

Man kann Bilder und andere Medien auf über normales HTML einbinden. Es sollten jedoch die includes verwendet werden, da man darüber einen einheitlichen Stil sicherstellt.

#### Bilder

Für das Einbinden von Bildern muss die Datei unter "assets/images/artikelbilder" liegen. Der Name der dort liegenden Datei muss in ein include als Parameter eingebunden werden.

```
{%- include post/articleimage.html img='Ex-Profi-Heiko-Scholz-mit-den-Trikots-der-Nationamannschaft-min.png' -%}
<em>Foto: ein sinnvoller Kommentar</em>
```

#### Videos

Es werden nur Videos von YouTube per include eingebunden. Man muss die ID des Videos als Parameter angeben.

Beispiel: Ein Video ist bei YouTube über den Link https://www.youtube.com/watch?v=qiUQs8Uli3o aufrufbar. Demzufolge hat das Video die ID "qiUQs8Uli3o". Diese gibt man im include an.

```
{%- include post/youtube-iframe.html youtubeid='qiUQs8Uli3o' -%}
<em>Video: ein sinnvoller Kommentar</em>
```

### Verlinkung

Die Verlinkung geschieht manuell. Meist werden die Tags von Vereinen eingebunden. Hier ist auf die richtige Schreibweise der Links zu achten.

Beispiele

    <a class="internal-link" href="">
    <a class="internal-link" href="/verein/1-fc-koeln/">1. FC Köln</a>
    <a class="internal-link" href="/verein/1-fc-magdeburg/">1. FC Magdeburg</a>
    <a class="internal-link" href="/verein/fc-st-pauli/">FC St. Pauli</a>


## Technische Dokumentation

### Build-Prozess

Befehl zum Erzeugen der Seite

```
## local development
bundle exec jekyll build

## live
JEKYLL_ENV=production bundle exec jekyll build
```

Die statische Seite wird im Ordner "site" abgelegt. Von dort aus wird sie kopiert in einen von git getrackten Ordner.
Dieser wird deployt, sodass nur der statische Teil der Seite auf Github landet.


### Deployment

```
cd ~/Code/static-traumelf
git add .
git commit -m ''
git push
```

### Google Analytics

Google Analytics ist eingebunden über ein include "google-analytics.html". Der key ist in der config.yml zu finden. Google Analytics ist nur auf dem Server aktiv, d.h. eine lokale Umgebung erzeugt keine Events bzw. Daten, welche die Auswertung beeinflussen. Dazu wird auf dem Live-Server eine Umgebungsvariable gesetzt.

    JEKYLL_ENV=production bundle exec jekyll build


### Domain

  * https://meine-traumelf.de
  * traumelf.github.io

Die Domain ist beim Anbieter https://do.de hinterlegt. Dort ist ein Setup zur Weiterleitung
zu github konfiguriert.

#### DNS Setup

```
*.meine-traumelf.de MX traumelf.github.io
www.meine-traumelf.de CNAME traumelf.github.io
meine-traumelf.de ALIAS traumelf.github.io
```

### Liquid in Jekyll

Liquid ist die HTML Template Sprache, welche in Jekyll verwendet wird.

Dokumentation:

* https://shopify.github.io/liquid/

### JS Library "Tippy"

Für die Anzeige mittels popover wird eine Library namens Tippy verwendet.

Dokumentation:

* https://atomiks.github.io/tippyjs/

## Command line helpers

```bash
# wo bin ich?
pwd

# Liste der Dateien im aktuellen Verzeichnis
ls
ls -l
ls -al

# in ein Verzeichnis wechseln
cd ein/name/unterordner

## git
# den neueste Stand von externer Quelle holen
git pull

# branches listen
git branch

# in einen Branch wechseln
git checkout branchname

# optional einen neuen branch anlegen
git checkout -b neuerbranchname

# einen branch mit einem anderen mergen
git merge name-des-branches-den-ich-in-den-aktuellen-branch-mergen-möchte

# den Stand der Dinge des aktuellen branches publizieren
git push

## jekyll
# Seite bauen
jekyll build

# Seite bauen und bereitstellen
jekyll serve

# jekyll anhalten
ctrl + c
```

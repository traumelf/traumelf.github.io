# Meine Traumelf

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


## Wie erstelle ich einen neuen Artikel?

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

## Struktur eines Artikels

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



Das vgwort include wird in layout "post.html" an die Posts gehängt. Darüber wird die im "front matter" vergebene "vgwort_tracking_id" in jeden Artikel eingebunden.

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

## Einbinden von Bildern und Videos

Für das Einbinden werden 2 includes bereitgestellt. Nach dem include sollte jeweils ein Kommentar in einem em-tag folgen.

Man kann Bilder und andere Medien auf über normales HTML einbinden. Es sollten jedoch die includes verwendet werden, da man darüber einen einheitlichen Stil sicherstellt.

### Bilder

Für das Einbinden von Bildern muss die Datei unter "assets/images/artikelbilder" liegen. Der Name der dort liegenden Datei muss in ein include als Parameter eingebunden werden.

```
{%- include post/articleimage.html img='Ex-Profi-Heiko-Scholz-mit-den-Trikots-der-Nationamannschaft-min.png' -%}
<em>Foto: ein sinnvoller Kommentar</em>
```

### Videos

Es werden nur Videos von YouTube per include eingebunden. Man muss die ID des Videos als Parameter angeben.

Beispiel: Ein Video ist bei YouTube über den Link https://www.youtube.com/watch?v=qiUQs8Uli3o aufrufbar. Demzufolge hat das Video die ID "qiUQs8Uli3o". Diese gibt man im include an.

```
{%- include post/youtube-iframe.html youtubeid='qiUQs8Uli3o' -%}
<em>Video: ein sinnvoller Kommentar</em>
```

## Verlinkung

Die Verlinkung geschieht manuell. Meist werden die Tags von Vereinen eingebunden. Hier ist auf die richtige Schreibweise der Links zu achten.

Beispiele

    <a class="internal-link" href="">
    <a class="internal-link" href="/verein/1-fc-koeln/">1. FC Köln</a>
    <a class="internal-link" href="/verein/1-fc-magdeburg/">1. FC Magdeburg</a>
    <a class="internal-link" href="/verein/fc-st-pauli/">FC St. Pauli</a>

## Deployment

Das Deployment auf Live geschieht automatisch, sobald man den "master" branch pushed. Man muss sich vorher sicher sein, dass alles so ist wie es sein soll. Es ist immer ratsam in einem anderen branch zu arbeiten. Erst bei release eines neuen Artikels (oder Verbesserungen) soll der master branch gepushed werden.

## Google Analytics

Google Analytics ist eingebunden über ein include "google-analytics.html". Der key ist in der config.yml zu finden. Google Analytics ist nur auf dem Server aktiv, d.h. eine lokale Umgebung erzeugt keine Events bzw. Daten, welche die Auswertung beeinflussen. Dazu wird auf dem Live-Server eine Umgebungsvariable gesetzt.

    JEKYLL_ENV=production bundle exec jekyll build

## Server

Dies ist Dokumentation zum Server und ist nicht relevant für die Jekyll-Website selbst.

### SSH Zugriff

    ssh martin@46.231.179.8

### Deployment via Webhook

1. webhook > http://46.231.179.8/api/update
2. /home/martin/webhookendpoint.py
3. /home/martin/jekyll_rebuild.sh

Der endpoint wird durch Apache bereitgestellt. Siehe config

    vim /etc/apache2/sites-enabled/traumelf.de-le-ssl.conf'

Das Python-Script muss als background job laufen.

    python webhookendpoint.py &

### Domain

  * https://meine-traumelf.de

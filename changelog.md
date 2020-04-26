
# Changelog

## Offen

## Version 1.0.1
* Posts h3 anpassen
* About page - Alex entfernen
* Schriftart +1px = 17px
* Schriftart = Calibri
* Favicon ist vorhanden
* Sharing Buttons farbig und in der Größe angepasst
* YouTube Videos in voller Breite des Textes
* sidebars für jede Seite wählbar
 * (Vereinsseiten - in Sidebar Blogroll und Twitter-Feed entfernen)
 * Sidbar für Vereinsseiten sind hardcoded in verein-layout-with-sidebar
* Cookie-Hinweis
* Vereinsseiten mit Seitentitel und Meta-description
 * meta:  Legenden deines Lieblingsvereins {Name des Vereins} stellen ihre persönliche Traumelf aus früheren Mitspielern vor.
 * title: {Name des Vereins} Legenden | Meine Traumelf
* Variable in config um Anzahl der Artikel in Sidebar einstellen zu können

## Version 1.0
* Links equivalent zur bestehenden Seite
* Logo im header
* Responsive layout
* Brand color grün gesetzt (Hexadezimalwert #15a52e)
* Bug fixes im header
* Seite "Spieler" mit Liste der Artikel versehen wie auf Startseite
* Seite "Trainer" mit Liste der Artikel versehen wie auf Startseite
* Tag-Links in Sidebar als Buttons darstellen
* Teaser-Text für page "Vereine" anlegen  (tags-text.html)
* Teaser-Text für jede tag page anlegen (tag-text.html)
* Seite "Vereine" - Liste der Vereine mit Logo, darunter Liste der Interview-Partner
* Logo zur Vereinsseite hinzugefügt
* Vereinsnamen in deutschem Format mit Umlauten - tags müssen jedoch ohne Umlaute bestehen bleiben
* Links zu den externen Seiten (FB, Insta, pipapo) in Sidebar aufnehmen unter dem Punkt "Auswärts"
* YouTube include
* Intro include
* Alle vorhandenen Interviewseiten überarbeiten !
* Brand-Colors an Logo anpassen
* Alle neuen Interviews nach Rainer Zobel (Trainer) von Live übernehmen und überarbeiten!
 * Steffi Jones
 * Florian Bruns
 * Heiko Scholz
 * Thomas Broich
 * Karsten Baumann
 * Roy Präger
 * Norbert Brinkmann
 * Heiner Pahl
 * Christof Babatz
 * Markus Kreuz
 * Markus Pröll
 * Bernd Franke
* Seite "Spieler" und Seite "Trainer" Bildgröße korrigieren
* Post Seite - Größe des Personbildes korrigieren
* Artikelseite - Intro-Bild und -Text nebeneinander
* Liste in Sidebar mit borders versehen
* Tracking via VG-Wort als include einbinden und in README aufnehmen
* alle Artikel mit VG-Wort-ID versehen !
* Anleitung zur Verwendung von Jekyll in README aufnehmen
* fehlende VG-Wort-ID ausbessern
 * Christof Babatz - keine ID
 * Joachim Streich - keine ID
* Schriftart an alte Seite anpassen
* pagination
* include tag-text.html mit Parameter "germanteamname"
* Text-Verein anpassen: Hier findest du alle bisherigen Traumelf-Interviews. Taktische Anordnung: alphabetisch nach Vereinen
* Font size 14, Font family "Calibri"
* Sidebar Werbung entfernen
* Sidebar Twitter hoch
* post.meta: Tag -> Vereine, germanteamname verwenden
* Anpassungen der headelines in den Artikeln
* internal Links farblich unterstreichen / hervorheben
* Hover Effekt (Zoom) für die Bilder auf Startseite, Spieler und Trainer übernehmen
* Related posts: 3 Stück, gleiches Tag (wenn kein gleiches Tag dann neueste Artikel)
* pagination auf "Trainer" und "Spieler"
* Alle Seiten names "tag" in "verein" umbenennnen
* Seite "tag" mit der Übersicht aller Vereine umbenennnen in "vereine"
* Alle Links auf tag-Seiten auf verein-Seiten ändern
* germanteamname in related posts
* Schriftgröße 16px
* pagination nach 12 Artikeln
* Google Tracking einbauen
* Responsive Artikelseite
* Aktiver Seitenbereich in Hauptnavi hervorheben
* Sharing Buttons
* include für Tipico-Werbung am Artikel-Ende - siehe "includes/promotion/post-tipico-banner.html"
* Bildcredits ins front matter aufnehmen und in post.meta anzeigen
* vgwort-pixel erscheint als Absatz (p tag) in den Artikeln und nimmt zuviel Platz ein
* about page
* Impressum überarbeiten
* Kontakt-Seite entfernen da redundant
* Vereinslogos vervollständigen
* Punkte aus den Vereinsnamen herausnehmen (es dürfen keine Punkte in den Tags enthalten sein)
* Sitemap für die Suchmaschinen erzeugen - baseurl/sitemap.xml
* Suchfunktion ohne externen Service mit https://lunrjs.com/
* Liste der letzten 10 Artikel in der Sidebar anzeigen
* front matter erweitern um eine Variable um damit den meta-tag "description" anzupassen

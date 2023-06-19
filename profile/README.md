# Digitales Museumsarchiv
Dieses Projekt enthält den Versuch, für die Archive der deutschen Straßenbahnmuseen ein einheitliches Vorgehen
bei der Digitalisierung vorzuschlagen.
Alle ÖPNV-affinen Museen stehen vor den gleichen Herausforderungen im Umgang mit der Digitalisierung,
der eingehenden Materialflut und dem Umgang mit Archivmaterial in einem neuen Zeitalter.
Daher soll hier zusammengetragen werden, vor welchen gleichartigen Herausforderungen alle stehen
und wie man ihnen am Besten begegnen kann.
Ziel dabei ist nicht, eine Art Vorschrift zu entwickeln, wie man am Besten vorgehen muss oder sollte,
sondern einen gemeinsamen Nenner zu finden, wie der Bedarf von allen am Besten abgedeckt werden kann,
ohne dass in jeder Stadt oder jedem Verbundraum das Rad immer wieder neu erfunden wird.

## Grundlagen
Basis aller Daten ist das Dateisystem. Viele Archive haben schon eine Sammlung von PDF- oder Bilddateien zusammengetragen.
Um diese nicht zu gefährden, gibt es für das gesamte Archivsystem ausschließlich lesenden Zugriff auf die Bestandsdaten.

Nötige Katalogdaten werden - um den Import und Export zu erleichtern - in einem Schattenverzeichnis gespeichert, das identischen Aufbau hat.
Auf die Katalogdaten hat das System Lese-/Schreib- und Löschzugriff.

Um die Datenabfrage und -auswertung zu beschleunigen werden Referenzdaten in einer Datenbank gehalten.
Die Datenbank wird bei Bedarf aus den Bestands- und Katalogdaten ganz oder teilweise neu erstellt.

Für die Implementierung kommen ausschließlich Open-Source-Komponenten zum Einsatz. Als Tools für die Entwicklung kommen 
ebenfalls ausschließlich Toolsets zum Einsatz, die kostenlos zur Verfügung stehen, oder die vom Hersteller für die Arbeit an
Open-Source Projekten kostenlos lizensiert werden.

## Komponenten bzw. Teilprojekte

Die Teilprojekte sind dokumentiert in 
[Komponenten / Teilprojekte](/profile/Teilprojekte.md)

# Digitales Museumsarchiv
Dieses Projekt enthält den Versuch, für die Archive der deutschen Straßenbahnmuseen ein einheitliches Vorgehen
bei der Digitalisierung vorzuschlagen.
Alle ÖPNV-affinen Museen stehen vor den gleichen Herausforderungen im Umgang mit der Digitalisierung,
der eingehenden Materialflut und dem Umgang mit Archivmaterial in einem neuen Zeitalter.
Daher soll hier zusammengetragen werden, vor welchen gleichartigen Herausforderungen alle stehen
und wie man ihnen am besten begegnen kann.
Ziel dabei ist nicht, eine Art Vorschrift zu entwickeln, wie man am besten vorgehen muss oder sollte,
sondern einen gemeinsamen Nenner zu finden, wie der gemeinsame Bedarf von allen am besten abgedeckt werden kann,
ohne dass in jeder Stadt oder jedem Verbundraum das Rad immer wieder neu erfunden wird.

## Grundlagen

### Anwendungsarchitektur

Basis aller Daten ist das Dateisystem. Viele Archive haben schon eine Sammlung von PDF- oder Bilddateien zusammengetragen.
Um diese nicht zu gefährden, gibt es für das gesamte Archivsystem ausschließlich lesenden Zugriff auf die Bestandsdaten.

Nötige Katalogdaten werden - um den Import und Export zu erleichtern - in einem Schattenverzeichnis gespeichert, das identischen Aufbau hat.
Auf die Katalogdaten hat das System Lese-/Schreib- und Löschzugriff.

Um die Datenabfrage und -auswertung zu beschleunigen werden Referenzdaten in einer Datenbank gehalten.
Die Datenbank wird bei Bedarf aus den Bestands- und Katalogdaten ganz oder teilweise neu erstellt.

Die Projektsprache ist - schon aufgrund des Zielpublikums - Deutsch, ebenso sind alle UI-Elemente in deutscher Sprache gehalten.

### Zielsysteme

Für die Serverseite sind Linux-Systeme vorgesehen, die ohne vollständige grafische Oberfläche betrieben werden und daher
keine teure Hardware erfordern. Das auf dem Server laufende Backend wird als Linux-DEB-Paket und als Docker-Image bereitgestellt.

Für alle Client-Systeme, die einen Webbrowser beinhalten, wird ein Webclient angeboten, der auf allen aktuellen Browsern
lauffähig sein sollte. Die nötige Anwendung wird ebenfalls als Linux-Paket und als Docker-Image bereitgestellt.

Um hardwarenahe Funktionalitäten wie Kamera-Zugriff oder Scannen von Covers anbieten zu können, wird ein Desktop-Client
angeboten. Dieser wird plattformneutral in Java entwickelt und als Linux-Paket und als Windows-MSI-Installer bereitgestellt.

Als Erleichterung bei der Datenerfassung wird eine Android-App angeboten, die primär zum Scannen von Barcodes "am Regal",
hauptsächlich für Bücher und Medien neueren Datums, gedacht ist. Diese wird entweder als "Side load" oder vielleicht auch über
den offiziellen Google-Store angeboten.

Aufgrund zu hoher Hardwarekosten ist keine Unterstützung für die Apple Plattform vorgesehen.

### Toolset
Für die Implementierung kommen ausschließlich kostenlose Open-Source-Komponenten zum Einsatz. Als Tools für die 
Entwicklung kommen ebenfalls ausschließlich Toolsets zum Einsatz, die kostenlos zur Verfügung stehen, oder die vom 
Hersteller für die Arbeit an Open-Source-Projekten kostenlos lizenziert werden.

#### Projektspeicherort

Das Projekt und alle seine Teilprojekte sind bei Github hinterlegt. Je nach Entwicklungsstand wird der Sourcecode in 
Public Repositories offengelegt.

#### Buildsystem

Für alle Builds und Bereitstellungen kommen voraussichtlich Github-Actions zum Einsatz

#### IDE

Als Entwicklungswerkzeug werden empfohlen:

- IDEA Intellij (kostenlos für Studenten und Open-Source-Entwickler)
- Microsoft Visual Studio Code (kostenlos)

#### Codeanalyse, Vulnerability Scan etc.

Hierfür ist SonarCloud vorgesehen, ggf. mit Unterstützung von OWASP Dependency Check.

## Komponenten bzw. Teilprojekte

### Backend ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Entwicklung-yellow.svg)
Das Backend läuft auf dem zentralen Server und hat als einzige Komponente direkten Zugriff auf die Bestandsdaten.

Andere Komponenten greifen über eine Rest-Schnittstelle zu, um Jobs zu starten, Katalogdaten zu bearbeiten, oder Daten abzufragen.
#### Betriebssysteme
Aus Kostengründen sind Linux-Server vorgesehen, vorzugsweise mit einer leicht bedienbaren Oberfläche,
wie z.B. das Projekt "OpenMediaVault". Windows-Server sind von den Lizenzkosten her deutlich teurer, hinzu kämen noch
höhere Kosten für die benötigte Hardware aufgrund der grafischen Oberfläche.
Alternativ kann das Backend als Docker-Image auf jeder kompatiblen Plattform installiert werden.
![Generic badge](https://img.shields.io/badge/OS-Linux-green.svg?logo=linux)
![Generic badge](https://img.shields.io/badge/Package-deb-green.svg?logo=debian)
![Docker](https://badgen.net/badge/icon/docker?icon=docker&label)

#### Entwicklungsplattform
Das Backend wird realisiert mit Spring-Boot.
![Generic badge](https://img.shields.io/badge/Plattform-Spring_Boot-green.svg?logo=springboot)

### Frontend Web ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Definition-red.svg)
Das webbasierte Frontend ist eine Webanwendung, über die alle Abfragen gestartet werden. Die verschiedenen Abfragevarianten werden
über REST an das Backend übergeben und die Antworten des Backends werden im Frontend angezeigt.
#### Betriebssysteme
Als reine Webanwendung kann das Frontend von jedem modernen Browser aufgerufen werden. ![Generic badge](https://img.shields.io/badge/OS-beliebig-green.svg?logo=googlechrome)

Gehostet wird das Backend auf einem Linux-Server oder als Docker-Image. ![Generic badge](https://img.shields.io/badge/Package-deb-green.svg?logo=debian)
![Docker](https://badgen.net/badge/icon/docker?icon=docker&label)

#### Entwicklungsplattform
Die Plattform ist noch auszuwählen. Derzeit sind folgende Möglichkeiten in Evaluation:
- Angular
- React
- Vaadin

### Frontend Desktop App ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Definition-red.svg)
Die Desktop-App wird für Vorgänge benötigt, die aus einem Webclient nicht möglich sind, z.B. aufgrund von Hardware-Zugriffen.
Folgende Operationen sind für die Desktop-App vorgesehen:
- Aufnahme von Einzelbildern mit der Webcam
- Suche nach ISBN/EAN-Barcodes im aufgenommenen Bild
- ISBN/EAN-Barcode auswerten
- Foto einer aufgedruckten ISBN mit OCR auswerten
- Abfrage von Mediendaten und Cover aus einer externen Datenbank (Partner gesucht!)
- Ggf. Mediendaten manuell erfassen und Coverfoto aufnehmen.
- Katalogdaten erzeugen und in DB speichern

#### Betriebssysteme

Unter Linux kann das Paket direkt installiert werden.
Zu prüfen ist eine Verteilungsmöglichkeit über die gängigen Paketmanager. ![Generic badge](https://img.shields.io/badge/Package-deb-green.svg?logo=debian)

Unter Windows ist es mit heutigen Mitteln problemlos möglich, direkt im Java-Build sowohl eine Windows-gängige-EXE-Datei
zu erzeugen, als auch einen Standard-MSI-Installer mit Deinstallations- und Updatefähigkeit. ![Generic badge](https://img.shields.io/badge/Package-MSI-green.svg?logo=windows)

#### Entwicklungsplattform
Die Desktop-App wird mit JavaFX erstellt und ist damit auf Linux und Windows lauffähig. ![Generic badge](https://img.shields.io/badge/Plattform-Java_FX-green.svg)

### Frontend Mobile App ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Definition-red.svg)
Der Mobile-Client stellt eine Vereinfachung des Desktop-Clients dar und dient zur Datenerfassung "vor dem Regal", also
ohne z.B. alle Bücher erst zu einem Schreibtisch tragen zu müssen. Aufgrund der geringeren Displaygröße sind auf dem
Mobilgerät nur einige der Funktionen der Desktop App vorgesehen.
- Aufnahme von Einzelbildern mit der Webcam
- Suche nach ISBN/EAN-Barcodes im aufgenommenen Bild
- ISBN/EAN-Barcode auswerten
- Foto einer aufgedruckten ISBN mit OCR auswerten
- Abfrage von Mediendaten und Cover aus einer externen Datenbank (Partner gesucht!)
- Katalogdaten erzeugen und in DB speichern

Soweit möglich sollte in der Desktop- und der Mobile-App versucht werden, Code wiederzuverwenden bzw. auf die gleichen
Module zuzugreifen.

#### Betriebssysteme ![Generic badge](https://img.shields.io/badge/OS-Android-green.svg?logo=android)
Der Mobile Client wird ausschließlich für die Android-Plattform entwickelt. Die Windows-Phone-Umgebung hat keine
nennenswerte Verbreitung und die Apple Plattform würde zu hohe Hardware-Kosten auslösen.


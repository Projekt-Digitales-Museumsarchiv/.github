# Komponenten bzw. Teilprojekte


### Backend ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Entwicklung-yellow.svg)
Das Backend läuft auf dem zentralen Server und hat als einzige Komponente direkten Zugriff auf die Bestandsdaten.

Andere Komponenten greifen über eine Rest-Schnittstelle zu, um Jobs zu starten, Katalogdaten zu bearbeiten, oder Daten abzufragen.
#### Betriebssysteme
Aus Kostengründen sind Linux-Server vorgesehen, vorzugsweise mit einer leicht bedienbaren Oberfläche,
wie z.B. das Projekt "OpenMediaVault". Windows-Server sind von den Lizenzkosten her deutlich teurer, hinzu kämen noch
höhere Kosten für die benötigte Hardware aufgrund der graphischen Oberfläche.
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
Die Desktop App wird für Vorgänge benötigt, die aus einem Webclient nicht möglich sind, z.B. aufgrund von Hardware-Zugriffen.
Folgende Operationen sind für die Desktop App vorgesehen:
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
zu erzeugen, wie auch einen Standard-MSI-Installer mit Deinstallations- und Updatefähigkeit. ![Generic badge](https://img.shields.io/badge/Package-MSI-green.svg?logo=windows)

#### Entwicklungsplattform
Die Desktop App wird mit JavaFX erstellt und ist damit auf Linux und Windows lauffähig. ![Generic badge](https://img.shields.io/badge/Plattform-Java_FX-green.svg)

### Frontend Mobile App ![Generic badge](https://img.shields.io/badge/Projektstatus-In_Definition-red.svg)
Der Mobile Client stellt eine Vereinfachung des Desktop Clients dar und dient zur Datenerfassung "vor dem Regal", also
ohne z.B. alle Bücher erst zu einem Schreibtisch tragen zu müssen. Aufgrund der geringeren Displaygröße sind auf dem
Mobilgerät nur einige der Funktionen der Desktop App vorgesehen.
- Aufnahme von Einzelbildern mit der Webcam
- Suche nach ISBN/EAN-Barcodes im aufgenommenen Bild
- ISBN/EAN-Barcode auswerten
- Foto einer aufgedruckten ISBN mit OCR auswerten
- Abfrage von Mediendaten und Cover aus einer externen Datenbank (Partner gesucht!)
- Katalogdaten erzeugen und in DB speichern

Soweit möglich sollte in der Desktop und der Mobile App versucht werden, Code wiederzuverwenden bzw. auf die gleichen
Module zuzugreifen.

#### Betriebssysteme ![Generic badge](https://img.shields.io/badge/OS-Android-green.svg?logo=android)
Der Mobile Client wird ausschließlich für die Android-Plattform entwickelt. Die Windows-Phone-Umgebung hat keine
nennenswerte Verbreitung und die Apple Plattform würde zu hohe Hardware-Kosten auslösen.

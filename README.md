# NotizKlar für iPod touch – iOS 12 MVP

NotizKlar ist ein natives UIKit-Projekt für iPod touch mit **iOS 12.5.8**. Es enthält keine Netzwerk- oder Cloud-Aufrufe in der App; Audioaufnahmen und Notizen werden lokal gespeichert und von Geräte-Backups ausgeschlossen.

## Bereits umgesetzt

- Neue Gesprächs- oder Meetingnotizen anlegen
- Audioaufnahme im M4A-Format mit Mikrofonfreigabe
- Lokale Speicherung der Aufnahme
- Manuell bearbeitbares Transkript
- Lokale Strukturierung eines Transkripts in Zusammenfassung, Kernpunkte und Aufgaben
- Lokales Löschen von Aufnahmen und Notizen

## Kostenlose Installation ohne Mac

GitHub Actions baut auf einem gehosteten macOS-Runner eine unsignierte IPA. Die Datei kann unter Windows mit Sideloadly und einer persönlichen kostenlosen Apple-ID auf dem iPod touch installiert werden. Der kostenlose Apple-Signierzeitraum beträgt sieben Tage; danach muss die App erneut signiert werden.

Eine Schritt-für-Schritt-Anleitung steht in [INSTALLATION.md](INSTALLATION.md). Der Build ist im Workflow [build-ios.yml](.github/workflows/build-ios.yml) definiert.

## Wichtiger Stand zur Offline-KI

Die App enthält eine funktionsfähige **lokale Textstrukturierung**. Eine echte Audio-zu-Text-Transkription benötigt zusätzlich eine lokal mitgelieferte Spracherkennungs-Engine plus deutsches Modell. Apple `SFSpeechRecognizer` ist hierfür nicht eingebaut. Die Schnittstelle und die vorbereitete Integrationsnotiz beschreiben Vosk als mögliche Engine. Bis Laufzeit und Modell tatsächlich integriert und auf dem iPod getestet sind, bleibt die Transkriptionsschaltfläche deaktiviert; es gibt keinen Cloud-Fallback.

## Kompatibilität

- Deployment Target: **iOS 12.0**
- UI-Technik: UIKit, kein SwiftUI
- Drittanbieterbibliotheken im MVP: keine
- Unterstützt: iPod touch mit iOS 12.5.8; ausreichend freier Speicher erforderlich

## Projektstruktur

```text
NotizKlar/
├── Models/                 Datenmodell für eine Meetingnotiz
├── Services/               Aufnahme, lokale Speicherung, Textstrukturierung
├── ViewControllers/        UIKit-Oberfläche
├── OptionalIntegration/    Anleitung für eine vollständig lokale STT-Engine
└── Info.plist              Mikrofon-Datenschutzhinweis
```

## Datenschutz

NotizKlar öffnet keine Netzwerkverbindung. Der Mikrofonzugriff wird nur während einer vom Nutzer gestarteten Aufnahme verwendet. Audio- und Textdaten bleiben im App-Speicher des Geräts, bis sie in der App gelöscht oder die App deinstalliert wird. Sie werden von iCloud-/Geräte-Backups ausgeschlossen.

# NotizKlar kostenlos auf iPod touch installieren – ohne eigenen Mac

Das Projekt enthält eine automatische GitHub-Actions-Pipeline. GitHub baut daraus auf einem gehosteten macOS-Runner eine **unsignierte IPA**. Du kannst diese unter Windows mit Sideloadly und deiner eigenen Apple-ID auf den iPod touch installieren. Du brauchst dafür keinen eigenen Mac und kein kostenpflichtiges Apple-Developer-Abonnement.

## 1. IPA vom kostenlosen Cloud-Build herunterladen

1. Öffne das öffentliche Projekt: [GitHub – NotizKlar iOS 12](https://github.com/Paulus123gp/notizklar-ios12).
2. Wähle **Actions** und öffne den neuesten erfolgreichen Lauf **Build NotizKlar IPA**.
3. Lade unter **Artifacts** das Archiv **NotizKlar-unsigned-IPA** herunter.
4. Entpacke es auf deinem Windows-PC. Darin liegt `NotizKlar-unsigned.ipa`.

GitHub startet den Build automatisch bei Änderungen am Branch `main`. Ein Build kann außerdem in **Actions → Build NotizKlar IPA → Run workflow** erneut gestartet werden. Der Build-Download wird nach sieben Tagen automatisch entfernt; bei Bedarf lässt sich ein neuer bauen.

## 2. Sideloadly unter Windows vorbereiten

1. Lade Sideloadly ausschließlich von [sideloadly.io](https://sideloadly.io/) herunter und installiere die Windows-Version.
2. Wenn Sideloadly den iPod nicht erkennt, installiere die **Web-Version von iTunes** von Apples Website (nicht die Microsoft-Store-Version), starte Windows neu und verbinde den iPod erneut.
3. Verbinde den iPod per USB. Entsperre ihn und bestätige **Diesem Computer vertrauen**.

## 3. IPA signieren und installieren

1. Öffne Sideloadly und ziehe `NotizKlar-unsigned.ipa` in das Fenster.
2. Wähle deinen verbundenen iPod aus.
3. Gib deine Apple-ID in Sideloadly ein. **Gib Zugangsdaten niemals hier im Chat ein.** Für zusätzliche Sicherheit kannst du eine separate Apple-ID verwenden. Die Anmeldung und etwaige Zwei-Faktor-Abfrage erledigst du selbst in Sideloadly; diese Zugangsdaten werden nicht in GitHub oder im Workflow gespeichert.
4. Starte **Start** und warte, bis Sideloadly die Installation meldet.
5. Falls iOS die App noch blockiert, öffne **Einstellungen → Allgemein → Profile & Geräteverwaltung** (der Name kann je nach iOS-Version leicht abweichen), wähle das Entwicklerprofil deiner Apple-ID und tippe auf **Vertrauen**.

## Einschränkungen des kostenlosen Wegs

- Apple lässt persönliche Gratisprofile nach **sieben Tagen** ablaufen. Danach musst du die App mit Sideloadly erneut signieren/installieren. Sideloadly kann das Auffrischen teilweise automatisieren, wenn der Windows-PC und der iPod verfügbar sind; verlasse dich nicht darauf, dass die App unbegrenzt gültig bleibt.
- Apple beschränkt persönliche Teams außerdem auf bis zu **drei installierte Apps pro Gerät** und bis zu **drei registrierte Geräte**; die App-IDs und Profile laufen nach sieben Tagen ab. Details stehen in Apples [Dokumentation zum persönlichen Entwicklerteam](https://developer.apple.com/help/account/basics/about-your-developer-account/).
- Lass die installierte App beim erneuten Signieren auf dem Gerät und verwende dieselbe Apple-ID sowie dieselbe Bundle-ID, damit lokale Notizdaten möglichst erhalten bleiben.
- Der öffentliche GitHub-Repository enthält den Quellcode und Build-Workflow, aber keine Apple-Anmeldedaten und keine persönlichen Notizen.

## Was die App derzeit kann

Die App nimmt Audio lokal auf und strukturiert eingegebenes Transkript lokal in Zusammenfassung, Kernpunkte und Aufgaben. Eine echte deutsche Offline-Audio-Transkription ist noch nicht integriert; die Transkriptionsschaltfläche bleibt deaktiviert, bis die lokale Engine samt Modell ergänzt wurde.

## Falls etwas schiefgeht

- **Kein IPA-Artefakt:** Prüfe, ob der GitHub-Actions-Lauf erfolgreich war. Bei einem fehlgeschlagenen Lauf öffne den Build-Log.
- **Gerät wird nicht erkannt:** Prüfe den USB-Vertrauensdialog und installiere Apples Web-iTunes-Treiber.
- **App startet nicht nach einer Woche:** Signiere sie erneut mit derselben Apple-ID und installiere sie über Sideloadly erneut.
- **Build soll wiederholt werden:** In GitHub unter **Actions → Build NotizKlar IPA → Run workflow** starten.

## Quellen

- [GitHub Actions: Abrechnung und kostenlose Nutzung](https://docs.github.com/billing/managing-billing-for-github-actions/about-billing-for-github-actions)
- [Sideloadly: offizieller Download und iOS-Unterstützung](https://sideloadly.io/index.html)
- [Sideloadly FAQ: Windows-Treiber und Geräteerkennung](https://sideloadly.io/faq.html)
- [Apple: persönliches Entwicklerteam und Profil-Laufzeit](https://developer.apple.com/help/account/basics/about-your-developer-account/)

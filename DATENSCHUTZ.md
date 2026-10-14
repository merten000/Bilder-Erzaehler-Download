# Datenschutzerklaerung

Stand: Oktober 2026 (Programmversion 0.12)

Diese Erklaerung beschreibt, welche Daten **Bilder-Erzaehler** verarbeitet
und wohin sie gehen. Sie beschreibt nur, was das Programm tatsaechlich tut.
Sie ist eine Information des Entwicklers und keine rechtliche Beratung.

## Verantwortlicher

Martin Derdula, Ruppinstr. 1, 15749 Mittenwalde,
E-Mail: socialmediaprint.merten@gmail.com ("Merten" ist der Projekt-/Rufname
des Entwicklers). Siehe auch das Impressum (`IMPRESSUM.md`, im Programm
unter "Datenschutz & Rechtliches" -> "Impressum").

## Was der Entwickler selbst erhebt

Nichts. Bilder-Erzaehler laeuft vollstaendig auf deinem Rechner. Es gibt
keinen eigenen Server, kein Benutzerkonto, keine Registrierung, keine
Statistik, kein Tracking und keine Fehlerberichte an den Entwickler. Das
Programm schreibt keine eigene Protokoll- (Log-) Datei und keine
Einstellungsdatei. Die ausgewaehlten Bilder, die Texte und die fertigen
Videos werden vom Entwickler nicht empfangen. Das Programm laedt erzeugte
Videos nirgendwohin hoch; sie liegen nur an dem Ort, den du beim Speichern
auswaehlst.

## Weitergabe an OpenAI oder Google (KI-Anbieter)

Fuer die Sprachausgabe und (optional) die automatische Texterstellung
sendet das Programm Daten **direkt von deinem Rechner** an den Anbieter,
den du im Programm auswaehlst - **OpenAI** oder **Google**. Der Entwickler
ist dazwischen nicht beteiligt und sieht diese Daten nicht.

- **Erzaehltext (immer):** Beim Klick auf "Video erstellen ..." wird der
  Erzaehltext fuer die Sprachausgabe an den gewaehlten Anbieter gesendet.
- **Bilder (nur bei "Text von KI aus den Bildern erstellen lassen"):** Die
  ausgewaehlten Bilder werden dafuer an den gewaehlten Anbieter gesendet.
  Vorher wandelt das Programm jedes Bild in ein neues PNG um (bei sehr
  grossen Bildern auf hoechstens 2048 Pixel an der laengeren Seite
  verkleinert, Transparenz auf weissem Grund, bei animierten GIFs nur das
  erste Einzelbild). Metadaten der Originaldatei (z. B. EXIF-Angaben)
  werden dabei nicht in die gesendeten Bilddaten uebernommen.
- **Dein API-Key:** Er wird bei jeder Anfrage an den jeweiligen Anbieter
  mitgeschickt, um die Anfrage deinem Konto zuzuordnen.
- **Technische Verbindungsdaten:** Wie bei jeder Internetverbindung sieht
  der Anbieter deine IP-Adresse.

**Hinweis vor der ersten Uebertragung:** Bevor das Programm in einer
Sitzung zum ersten Mal Bilder bzw. Text an einen Anbieter sendet, zeigt es
einen Hinweisdialog mit dem Anbieter, dem uebertragenen Inhalt, dem
Hinweis auf moegliche personenbezogene oder vertrauliche Informationen und
auf moegliche Kosten. Erst nach "Fortfahren" wird gesendet; mit
"Abbrechen" (oder Schliessen) wird nichts gesendet. Der Hinweis erscheint
je Sitzung einmal pro Anbieter und Art der Uebertragung (Bilder bzw.
Sprachausgabe). Deine Zustimmung wird nicht gespeichert; nach einem
Neustart des Programms erscheint der Hinweis wieder.

Verwendete Adressen:

- OpenAI: `https://api.openai.com/v1/chat/completions` (Text aus Bildern),
  `https://api.openai.com/v1/audio/speech` (Sprachausgabe)
- Google: `https://generativelanguage.googleapis.com/v1beta/interactions`
  (Text aus Bildern und Sprachausgabe)

Was OpenAI bzw. Google mit den Daten tun (Speicherdauer, Verarbeitung auch
ausserhalb der EU, Nutzung zur Produktverbesserung), bestimmen allein deren
eigene Datenschutz- und Nutzungsbedingungen; sie gelten fuer dein eigenes
Konto beim jeweiligen Anbieter. **Hinweis zum kostenlosen Google-Kontingent:**
Laut Google kann bei der kostenlosen Nutzung der Inhalt zur
Produktverbesserung verwendet werden, beim kostenpflichtigen Kontingent
nicht; massgeblich ist immer der aktuelle Stand auf der Preisseite bzw. den
Bedingungen von Google. Waehle deshalb nur Bilder und Texte aus, die du an
den gewaehlten Anbieter senden darfst und moechtest - insbesondere bei
Bildern mit erkennbaren Personen.

**Fehlermeldungen:** Liefert der Anbieter eine unerwartete Antwort (z. B.
Text statt Ton oder ein unbekanntes Format), zeigt das Programm nur eine
allgemeine Meldung und gibt die Antwort des Anbieters nicht wieder, weil sie
Inhalte aus deinen uebertragenen Bildern oder deinem Text enthalten koennte.
Meldet der Anbieter einen technischen Fehler (z. B. ungueltiger API-Key,
Limit erreicht), zeigt das Programm nur eine eigene allgemeine Meldung mit dem
HTTP-Statuscode und gibt den Fehlertext des Anbieters nicht wieder.
Fehlermeldungen werden nicht gespeichert und nirgends protokolliert.

## API-Key und Windows-Anmeldeinformationsspeicher

Der API-Key gilt standardmaessig nur fuer die laufende Sitzung und ist nach
dem Beenden des Programms weg. Nur wenn du auf "Speichern" klickst, legt
das Programm ihn im Windows-Anmeldeinformationsspeicher (Credential
Manager) deines Windows-Benutzerkontos ab - getrennt fuer OpenAI
(`Bilder-Erzaehler:openai`) und Google (`Bilder-Erzaehler:google`), nie in
einer normalen Datei. Mit "Loeschen" entfernst du den Eintrag wieder. Beim
Deinstallieren wirst du gefragt, ob gespeicherte API-Schluessel ebenfalls
geloescht werden sollen (Standard: Nein). Andere Programme desselben
Windows-Benutzerkontos koennen diesen Speicher grundsaetzlich ebenfalls
auslesen.

## Temporaere Dateien

Waehrend der Video-Erstellung legt das Programm voruebergehende
Arbeitsdateien (z. B. Zwischenbilder und Sprachausgabe) in einem eigenen
temporaeren Ordner deines Windows-Benutzerkontos an. Sie werden am Ende
automatisch wieder entfernt, auch wenn der Export fehlschlaegt. Deine
ausgewaehlten Originalbilder werden nie veraendert oder geloescht.

## Eintraege in der Windows-Registry

Der Installer legt im Bereich deines Benutzerkontos (HKCU, keine
Administratorrechte) den Installationsordner und den Eintrag fuer
"Apps" ab. Nur wenn du es unter "Tools" einschaltest, kommt der optionale
Kontextmenue-Eintrag fuer Bilddateien dazu. Die Deinstallation entfernt
diese eigenen Eintraege. Es werden keine Dateizuordnungen geaendert.

## Download von ffmpeg (nur nach deiner Bestaetigung)

Falls ffmpeg fehlt, fragt das Programm beim ersten Video-Export nach, ob es
heruntergeladen werden soll. Nur dann verbindet es sich mit GitHub
(`github.com`, dabei sind Weiterleitungen zu `githubusercontent.com`
zulaessig) und laedt dort genau den fest hinterlegten ffmpeg-Build
herunter. GitHub sieht dabei, wie bei jedem Download, deine IP-Adresse.
Bilder, Texte oder API-Keys werden dafuer nicht gesendet. Details zum
Build stehen in `THIRD-PARTY-NOTICES.md`.

## Andere Verbindungen

Das Programm stellt keine weiteren Internetverbindungen her als die oben
genannten (OpenAI, Google, GitHub fuer den ffmpeg-Download). Die
Dokumente (README, Impressum, diese Erklaerung usw.) werden lokal aus dem
Installationsordner gelesen, nicht aus dem Internet.

## Kontakt per E-Mail

Wenn du dem Entwickler schreibst, verarbeitet er deine E-Mail-Adresse und
den Inhalt deiner Nachricht nur, um dir zu antworten.

## Deine Rechte

Da der Entwickler durch das Programm keine personenbezogenen Daten von dir
erhaelt, kann er dazu auch keine Auskunft geben oder Daten loeschen. Fuer
Daten, die OpenAI, Google oder GitHub verarbeiten, wende dich an den
jeweiligen Anbieter. Du hast ausserdem das Recht, dich bei einer
Datenschutz-Aufsichtsbehoerde zu beschweren.

*Hinweis: Diese Erklaerung ist eine Information des Autors und kein Ersatz
fuer eine rechtliche Pruefung. Bei Zweifeln hilft ein Fachanwalt fuer
IT-Recht.*

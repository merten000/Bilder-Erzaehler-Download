# Haftungsausschluss & Nutzungshinweise

**Bilder-Erzaehler** ist ein privates, in Eigenregie entwickeltes Programm
von Martin Derdula (Projekt-/Rufname: "Merten", siehe `IMPRESSUM.md`).
Es wird kostenlos zur Verfuegung gestellt.

## Keine Gewaehrleistung

Dieses Programm wird "wie es ist" bereitgestellt, ohne jegliche
Gewaehrleistung oder Garantie - weder fuer die staendige
Funktionsfaehigkeit noch dafuer, dass ein erzeugtes Video oder ein von der
KI vorgeschlagener Text immer wie gewuenscht ausfaellt.

## Nutzung auf eigenes Risiko

Die Nutzung erfolgt auf eigenes Risiko. Fuer Schaeden, die durch die
Nutzung dieses Programms entstehen, wird keine Haftung uebernommen - das
gilt nicht fuer Schaeden, die vorsaetzlich oder grob fahrlaessig verursacht
wurden, sowie nicht fuer Schaeden an Leben, Koerper oder Gesundheit; dort
bleibt die gesetzliche Haftung unberuehrt. Die ausgewaehlten Bilddateien
selbst werden vom Programm nie veraendert oder geloescht. Waehrend der
Video-Erstellung legt das Programm intern voruebergehende Arbeitsdateien
an (z. B. fuer die Sprachausgabe und den Video-Zusammenbau) - diese liegen
in einem eigenen, dafuer angelegten temporaeren Bereich und werden am Ende
automatisch wieder entfernt, unabhaengig davon, ob der Export gelingt. Am
vom Nutzer gewaehlten Speicherort selbst wird die fertige Video-Datei immer
erst nach erfolgreichem Abschluss angelegt bzw. ersetzt: eine dort bereits
vorhandene, gleichnamige Datei bleibt bei einem fehlgeschlagenen Export
unangetastet und wird nie durch eine unvollstaendige/leere Datei ersetzt.

*Hinweis: Dieser Abschnitt ist eine Nutzungsinformation des Autors, kein
Ersatz fuer eine rechtliche Pruefung/Beratung.*

## Zwingende Nutzung einer KI-Funktion

Bei Bilder-Erzaehler ist die Nutzung einer KI-Funktion nicht optional: das
Vorlesen des Erzaehltexts (Sprachausgabe) laeuft in jedem Fall ueber den
gewaehlten Anbieter - **OpenAI** oder **Google** - und braucht dafuer immer
einen eigenen, selbst eingetragenen API-Key der nutzenden Person, nicht
einen Key des Autors. Wird zusaetzlich "Text von KI aus den Bildern
erstellen lassen" genutzt, werden dafuer die ausgewaehlten Bilder an
denselben Anbieter uebermittelt. Fuer die Verarbeitung dieser Daten durch
OpenAI bzw. Google gelten deren eigene Nutzungsbedingungen; Einzelheiten
zum Datenschutz stehen in `DATENSCHUTZ.md`.

Der API-Key gilt standardmaessig nur fuer die laufende Sitzung. Nur nach
ausdruecklichem Klick auf "Speichern" wird er freiwillig im
Windows-Anmeldeinformationsspeicher des eigenen Benutzerkontos abgelegt
(nie in einer normalen Datei), getrennt fuer OpenAI und Google, und kann
jederzeit mit "Loeschen" entfernt werden. Andere Programme desselben
Windows-Benutzerkontos koennen diesen Speicher grundsaetzlich ebenfalls
auslesen; wer das nicht moechte, speichert den Key nicht.

## ffmpeg (wird bei Bedarf aus dem Programm heraus heruntergeladen)

Bilder-Erzaehler laedt bei Bedarf (beim ersten Klick auf "Video
erstellen ...", falls noch nicht vorhanden, nach ausdruecklicher
Bestaetigung) zusaetzlich ffmpeg herunter, um Bilder und Sprachausgabe zu
einem Video zusammenzufuegen. Heruntergeladen wird ein fest im Programm
hinterlegter Windows-Build der oeffentlichen Community-Quelle BtbN
(GitHub); seine Pruefsumme wird vor der Installation geprueft. Die
dazugehoerigen Lizenzhinweise, die genauen Angaben zum hinterlegten Build
sowie die Hinweise zu den mitgelieferten Bestandteilen (Python, Pillow,
OpenSSL, PyInstaller u. a.) stehen in der separaten Datei
`THIRD-PARTY-NOTICES.md` - das betrifft fremden Code und ist deshalb
bewusst getrennt von diesem Disclaimer gehalten, der sich nur auf den
eigenen Code des Autors und die Haftung bezieht.

## Nutzung und Weitergabe

Das Programm darf kostenlos heruntergeladen, installiert und genutzt
werden - sowohl privat als auch geschaeftlich. Die unveraenderte
Weitergabe (z. B. Teilen des Installers bzw. der Programmdateien) ist
erlaubt, solange dieser Text und alle Urheber- und Rechtehinweise
vollstaendig erhalten bleiben.

Veraenderungen am Programm, am Quellcode oder an den mitgelieferten
Dateien (z. B. Weiterentwicklung, Uebersetzung, Einbau in ein anderes
Produkt) sind nur nach vorheriger schriftlicher Ruecksprache mit dem Autor
gestattet; Kontakt ueber die im `IMPRESSUM.md` genannte E-Mail-Adresse. Der
Quellcode ist nicht oeffentlich und wird nicht weitergegeben. Diese
Regelung raeumt keine weiteren Rechte ein als hier ausdruecklich genannt
und betrifft nur den eigenen Code des Autors - Rechte an mitgenutzten
Drittanbieter-Bestandteilen (z. B. ffmpeg, Python, Pillow, OpenSSL) ergeben
sich unabhaengig davon aus deren eigenen Lizenzen, siehe
`THIRD-PARTY-NOTICES.md`.

## Keine offizielle Software

Bilder-Erzaehler ist ein unabhaengiges Hobby-/Privatprojekt und steht in
keiner Verbindung zu Microsoft, OpenAI, Google, der ffmpeg-Entwicklergruppe
oder anderen genannten Unternehmen/Projekten.

---

Copyright © 2026 Martin Derdula. Alle Rechte vorbehalten, soweit nicht anders
angegeben (siehe oben "Nutzung und Weitergabe").

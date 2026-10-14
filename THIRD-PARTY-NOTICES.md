# Drittanbieter-Hinweise

Bilder-Erzaehler besteht aus eigenem Code (Quellcode von Martin Derdula,
nicht oeffentlich) und aus fremden Bestandteilen, die in die `Bilder-Erzaehler.exe`
eingebaut sind oder bei Bedarf separat heruntergeladen werden. Diese Datei
nennt sie mit Quelle, Lizenz und beiliegendem Lizenztext. Bezugsbasis ist
der Release-Build mit **Python 3.12.10 (Windows, 64 Bit)**,
**PyInstaller 6.22.0** und **Pillow 12.3.0**.

## ffmpeg / ffprobe

Bilder-Erzaehler bringt `ffmpeg.exe`/`ffprobe.exe` NICHT im Installer mit,
sondern laedt sie bei Bedarf automatisch aus dem Programm heraus herunter
(einmalig, beim ersten Klick auf "Video erstellen ..." falls noch nicht
vorhanden, und nur nach ausdruecklicher Bestaetigung) - sie werden intern
gebraucht, um aus den ausgewaehlten Bildern und der erzeugten Sprachausgabe
das fertige Video zusammenzubauen. Es handelt sich dabei um unveraenderte
Windows-Builds von ffmpeg selbst. Heruntergeladen wird immer genau ein im
Programm fest hinterlegter Build (kein wechselndes "latest"-Archiv):

- Quelle: BtbN FFmpeg-Builds auf GitHub,
  https://github.com/BtbN/FFmpeg-Builds (ein von ffmpeg.org unter
  "Download" -> "Windows" verlinkter Community-Anbieter fertiger
  Windows-Builds - nicht dasselbe wie ein vom FFmpeg-Projekt selbst
  herausgegebenes Binaerpaket, das FFmpeg-Projekt liefert primaer Quellcode)
- Fest hinterlegter Build: Auto-Build 2026-10-03 18:14, Datei
  `ffmpeg-N-127142-g12b7b9891b-win64-gpl.zip`, Download-Adresse
  `https://github.com/BtbN/FFmpeg-Builds/releases/download/autobuild-2026-10-03-18-14/ffmpeg-N-127142-g12b7b9891b-win64-gpl.zip`
- Pruefung vor der Installation: Das Programm vergleicht SHA-256-Pruefsumme
  (`a885f564dee2b60f69ab866c6c89b96ae531fc2ee1f24ff8b5b1a6d29960a96b`) und
  Dateigroesse des Archivs (200164490 Bytes) mit den fest hinterlegten
  Werten; bei
  Abweichung wird nichts entpackt und nichts installiert. Zulaessig sind
  nur HTTPS-Verbindungen zu github.com bzw. githubusercontent.com.
- Projekt: https://ffmpeg.org/
- Lizenz: Der Build ist ein sogenannter GPL-Build (Dateiname endet auf
  `-gpl.zip`) und steht damit unter der GNU General Public License. Nach
  den Angaben der Build-Quelle ist das die GPL in Version 3; massgeblich
  sind die Lizenzangaben, die dem heruntergeladenen Archiv selbst
  beiliegen, sowie https://ffmpeg.org/legal.html. Quellcode und
  Build-Skripte stehen beim FFmpeg-Projekt (https://ffmpeg.org/) bzw. bei
  BtbN (siehe oben).

> Bilder-Erzaehler laedt bei Bedarf ffmpeg (https://ffmpeg.org)
> unveraendert von der oben genannten Quelle herunter. ffmpeg steht unter
> der GNU GPL; Einzelheiten siehe oben.

ffmpeg ist NICHT Bestandteil dieses Installers oder der `.exe` und wird
von Bilder-Erzaehler nicht selbst weiterverteilt: es wird auf deinen
Wunsch direkt von der Quelle auf deinen Rechner geladen und als
eigenstaendiges Programm (`ffmpeg.exe`/`ffprobe.exe`) in einem eigenen
Prozess aufgerufen. Deshalb liegt hier kein eigener ffmpeg-Lizenztext bei;
er ist beim Archiv und unter dem obigen Link einsehbar. Diese Darstellung
ist eine sachliche Beschreibung, keine rechtliche Bewertung - ob damit alle
Pflichten aus der GPL erfuellt sind, ist nicht anwaltlich geprueft.

Wird die hinterlegte ffmpeg-Version bei einer spaeteren Programmversion
gewechselt, muessen Adresse, Pruefsumme und Dateigroesse im Programm
(`video_logic.py`) gemeinsam mit diesem Abschnitt aktualisiert werden (siehe
`BUILD.md`).

## Vollstaendige Bestandsaufnahme der eingebetteten Bestandteile

Die `.exe` wird mit PyInstaller (Einzeldatei-Modus) aus dem Quellcode und
dem installierten Windows-Python 3.12.10 zusammengestellt. Erwartet
werden: die Python-Laufzeit
(`python312.dll`), die Standardbibliothek-Module mit eigenen Binaerdateien,
die Bibliotheken `libssl-3.dll`/`libcrypto-3.dll` (OpenSSL 3.0.16),
`libffi-8.dll`, `zlib1.dll` (zlib 1.3.1), `tcl86t.dll`/`tk86t.dll`
(Tcl/Tk 8.6), `vcruntime140.dll` und `vcruntime140_1.dll` (Microsoft
Visual C++ 14.42), die Microsoft-Universal-C-Laufzeit (`ucrtbase.dll` sowie
die Weiterleitungs-DLLs `api-ms-win-core-*.dll` und `api-ms-win-crt-*.dll`;
beim Pruefbuild vom 12.10.2026 waren das 29 + 13 + 1 = 43 Dateien) sowie
Pillow mit seinen eigenen `.pyd`-Dateien.
Welche dieser Dateien in der fertigen `.exe` tatsaechlich stecken, wird
nach jedem Build mit dem im `BUILD.md` beschriebenen Schritt gegen die
Bauliste von PyInstaller geprueft; weicht sie von dieser Aufzaehlung ab,
muss diese Datei angepasst werden. Die Versionsangaben stammen aus den
DLL-Dateien der Python-3.12.10-Installation (bei libffi enthaelt die DLL
keine Versionsangabe). Die genaue Zahl der `api-ms-win-*`-Dateien kann je
Build-Rechner leicht abweichen; geprueft wird deshalb nach Namensmuster
(`api-ms-win-core-*.dll`, `api-ms-win-crt-*.dll`, `ucrtbase.dll`), jede
andere DLL muss einzeln aufgefuehrt sein.

## Python-Laufzeit (inkl. Tkinter, bzip2, libffi, Microsoft-Anteile)

Eingebettet ist die Python-3.12.10-Laufzeit, inklusive der Oberflaeche
Tkinter auf Basis von Tcl/Tk 8.6, der Module fuer bzip2/lzma sowie der
Fremdfunktionsbibliothek libffi (`libffi-8.dll`, gebraucht von `ctypes`;
`ctypes` wird vom Programm fuer den Windows-Anmeldeinformationsspeicher
genutzt, siehe `key_store.py`).

- Lizenz: Python Software Foundation License Version 2, siehe
  https://docs.python.org/3/license.html
- Der Lizenztext liegt bei: `LICENSE-Python.txt` - eine unveraenderte Kopie
  der `LICENSE.txt` der beim Bauen verwendeten Python-3.12.10-Installation.
  Sie enthaelt die PSF License samt den historischen Lizenzvereinbarungen,
  die Hinweise zu den von Python mitgelieferten Microsoft-Distributable-
  Code-Anteilen (Visual-C++-Laufzeit), den Lizenztext von bzip2/libbzip2
  1.0.8, den von libffi (Copyright 1996-2022 Anthony Green, Red Hat, Inc
  und andere) sowie die Apache License 2.0 fuer OpenSSL 3.
- Tcl/Tk (`tcl86t.dll`, `tk86t.dll`, Version 8.6.15): freizuegige
  BSD-aehnliche Lizenz. Die Lizenz verlangt, dass ihr Hinweis in jeder
  Weitergabe unveraendert enthalten ist. Der Lizenztext liegt deshalb als
  `LICENSE-Tcl-Tk.txt` bei - eine unveraenderte Kopie der Datei
  `tcl/tk8.6/license.terms` aus der beim Bauen verwendeten
  Python-3.12.10-Installation. PyInstaller packt dieselbe Datei auch selbst
  in die `.exe` (`_tk_data/license.terms`). Eine eigene Lizenzdatei des
  Tcl-Teils liegt in der Python-Installation nicht vor; die genannte Datei
  nennt als Rechteinhaber u. a. auch Scriptics (Tcl) und gilt laut ihrem
  Wortlaut fuer die gesamte zugehoerige Software.
- zlib 1.3.1 (`zlib1.dll`): zlib-Lizenz, https://zlib.net/zlib_license.html
  (freizuegig; Copyright 1995-2024 Jean-loup Gailly und Mark Adler).
- Microsoft Visual C++ Laufzeit (`vcruntime140.dll`,
  `vcruntime140_1.dll`): Microsoft-Distributable-Code; die Bedingungen
  stehen im oben genannten Abschnitt der `LICENSE-Python.txt`.
- Microsoft Universal C Runtime (`ucrtbase.dll`, `api-ms-win-core-*.dll`,
  `api-ms-win-crt-*.dll`): ebenfalls Microsoft-Distributable-Code, der von
  PyInstaller beim Bauen unter Windows mit eingesammelt wird; die
  Weitergabebedingungen stammen von Microsoft (siehe Abschnitt "Additional
  Conditions for this Windows binary build" in `LICENSE-Python.txt`) und
  wurden nicht rechtlich geprueft.

## OpenSSL (verschluesselte Verbindungen)

Fuer HTTPS-Verbindungen (zu OpenAI, Google und beim ffmpeg-Download) bringt
die eingebettete Python-Laufzeit die OpenSSL-Bibliotheken `libssl-3.dll`
und `libcrypto-3.dll` mit (Version 3.0.16).

- Lizenz: Apache License, Version 2.0
- Quelle: https://www.openssl.org/source/license.html
- Der Lizenztext liegt bei: `LICENSE-OpenSSL.txt`.

## PyInstaller (Bootloader)

Die `.exe` wird mit PyInstaller 6.22.0 gebaut und enthaelt dessen
Bootloader und Laufzeitdateien.

- Lizenz: GNU General Public License (Version 2 oder spaeter) mit einer
  Sonderausnahme ("Bootloader Exception"), die ausdruecklich erlaubt, den
  Bootloader in eigene Programme einzubetten und diese ohne Einschraenkung
  durch die GPL weiterzugeben; die Laufzeit-Hooks stehen unter der Apache
  License 2.0.
- Der Lizenztext liegt bei: `LICENSE-PyInstaller.txt` - eine unveraenderte
  Kopie der `COPYING.txt` aus dem PyInstaller-Paket 6.22.0.
- Quelle: https://pyinstaller.org/

## Pillow (Bildverarbeitung) inkl. mitgelieferter Bibliotheken

Bilder-Erzaehler nutzt die Python-Bibliothek **Pillow**
(https://python-pillow.org/), um jedes ausgewaehlte Bild vor der
Weiterverarbeitung einheitlich einzulesen, EXIF-Drehungen anzuwenden und in
ein einzelnes, konsistentes Format umzuwandeln (siehe `image_utils.py`).
Es wird in der Version 12.3.0 mit eingebaut. Das Windows-Paket von Pillow
bringt seinerseits mehrere Bibliotheken fest einkompiliert mit. Laut der
Software-Stueckliste (SBOM) des Pakets und Stichproben in den
`.pyd`-Dateien sind das unter anderem: FreeType 2.14.3, HarfBuzz 14.2.1,
Raqm 0.10.5, FriBiDi 1.0.16, Little CMS 2 (2.19.1), libjpeg-turbo 3.1.4.1,
libtiff 4.7.1, libwebp 1.6.0, libavif 1.4.2 (mit dav1d, AOM und libyuv),
OpenJPEG 2.5.4 und zlib(-ng); die Lizenzdatei nennt ausserdem libpng und
XZ Utils. Die vollstaendige Liste mit Versionen steht im Pillow-Paket und in
der beiliegenden Lizenzdatei.

- Lizenz Pillow selbst: MIT-CMU-Lizenz (eine freizuegige Open-Source-Lizenz)
- Quelle: https://github.com/python-pillow/Pillow/blob/main/LICENSE
- Der Lizenztext liegt bei: `LICENSE-Pillow.txt` - eine unveraenderte Kopie
  der Lizenzdatei aus dem beim Bauen installierten Paket Pillow 12.3.0. Sie
  enthaelt neben der MIT-CMU-Lizenz auch die Lizenztexte der mitgelieferten
  Bibliotheken.
- FriBiDi (LGPL-2.1-or-later): Laut SBOM ist FriBiDi nur "optional" und
  wird von Pillows Schicht fuer komplexen Textsatz erst zur Laufzeit als
  `libfribidi-0` nachgeladen. Weder das Python-Paket noch das Pillow-Paket
  enthalten eine solche DLL (geprueft), und Bilder-Erzaehler liefert keine
  mit. FriBiDi ist damit nicht Bestandteil der ausgelieferten Dateien.
  Das Programm nutzt keinen Textsatz mit Pillow.
- libimagequant (GPL-3.0-or-later): Die SBOM fuehrt es nur als "optional".
  In der konkret verwendeten Windows-Datei `PIL/_imaging.cp312-win_amd64.pyd`
  ist es nicht eingebaut: sie enthaelt keinerlei libimagequant-Code
  (nur den Namen des Merkmal-Schalters `HAVE_LIBIMAGEQUANT`, der immer
  vorhanden ist) und keine Spuren des Rust-Laufzeitcodes, in dem libimagequant
  4 geschrieben ist. Das Programm nutzt diese Funktion ohnehin nicht. Der
  Build-Schritt in `BUILD.md` prueft das mit `PIL.features.check` erneut.

> Copyright (c) 1997-2011 by Secret Labs AB, Copyright (c) 1995-2011 by
> Fredrik Lundh und Mitwirkende; Pillow selbst zusaetzlich Copyright (c)
> 2010 by Jeffrey A. Clark und Mitwirkende. Lizenziert unter der oben
> genannten MIT-CMU-Lizenz, siehe beiliegende Datei fuer die vollstaendigen
> Bedingungen (auch der mitgelieferten Bibliotheken).

## Anbieter-Schnittstellen (OpenAI, Google)

Die Anbindung an OpenAI und Google erfolgt ueber deren oeffentliche
Programmierschnittstellen (REST-APIs) direkt aus eigenem Code, ohne
Software-Pakete dieser Anbieter. Die Nutzung dieser Dienste unterliegt den
Bedingungen der Anbieter, nicht dieser Datei. Mehr dazu in
`DATENSCHUTZ.md`.

## Alle anderen Bestandteile

Der restliche Code von Bilder-Erzaehler (`bilder_erzaehler.py`,
`video_logic.py`, `video_profiles.py`, `ui_helpers.py`, `image_utils.py`,
`text_openai.py`, `text_google.py`, `tts_openai.py`, `tts_google.py`,
`ai_common.py`, `key_store.py`, `context_menu.py`, das Installationsskript)
ist eigener Code ohne weitere Drittanbieter-Abhaengigkeiten ausser der
Python-Standardbibliothek und den oben genannten Bestandteilen. Der Code
steht nicht unter einer Open-Source-Lizenz (siehe `DISCLAIMER.md`).
Der Installer wird mit NSIS gebaut (https://nsis.sourceforge.io/); die
Lizenzbedingungen von NSIS stehen dort.

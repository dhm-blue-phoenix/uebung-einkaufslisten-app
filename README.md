# Übung Einkaufslisten App

Hierbei handelt es sich um ein Übungsprojekt. Keine weiteren Angaben.

## Das muss installiert sein!
| Werkzeug | Zweck                                     | Download / Installation                                     |
| --- |-------------------------------------------|-------------------------------------------------------------|
| Node.js und npm | Angular-Frontend entwickeln und bauen | [Node.js installieren](https://nodejs.org/) |
| Rust inklusive Cargo und rustc | Tauri-Anwendung und Rust-Code kompilieren | [Rust installieren](https://www.rust-lang.org/tools/install) |
| Tauri-Rust-CLI | Tauri-Anwendung starten und bauen | `cargo install tauri-cli --version "^2"` |

Für Tauri sind zusätzlich die nativen Systemvoraussetzungen des jeweiligen
Zielbetriebssystems nötig:

- [Tauri-Voraussetzungen für Windows, macOS und Linux](https://v2.tauri.app/start/prerequisites/)
- Windows: [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) und [WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)
- macOS: [Xcode und Command Line Tools](https://developer.apple.com/xcode/)

## Schnell Start
```bash
   git clone https://github.com/dhm-blue-phoenix/uebung-einkaufslisten-app
   cd uebung-einkaufslisten-app
```

## Entwickeln

Tauri und Rust laufen auf dem Host. Beim Start von `tauri dev` startet der
Tauri-Hook den Angular-Dev-Server lokal.

Frontend-Abhängigkeiten einmalig installieren:

```bash
cd frontend
npm ci
```

Danach Tauri starten:

```bash
cd app
cargo tauri dev
```

Der Dev-Server ist unter `http://localhost:1420` erreichbar. Zum separaten
Starten des Frontends:

```bash
cd frontend
npm start
```

## Release-Build erstellen

`tauri build` installiert die Frontend-Abhängigkeiten, baut Angular lokal und
verpackt danach die erzeugten Dateien mit Tauri auf dem Host:

```bash
cd app
cargo tauri build
```

Der native Tauri-Build muss auf dem Betriebssystem ausgeführt werden, für das
die App gebaut wird.

Das separate Programm unter `backend/` wird durch diese Befehle derzeit nicht
gestartet oder in die Tauri-App eingebunden.

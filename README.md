# Übung Einkaufslisten App

Hierbei handelt es sich um ein Übungsprojekt. Keine weiteren Angaben.

## Das muss installiert sein!
| Werkzeug | Zweck                                     | Download / Installation                                     |
| --- |-------------------------------------------|-------------------------------------------------------------|
| Rust inklusive Cargo und rustc | Tauri-Anwendung und Rust-Code kompilieren | [Rust installieren](https://www.rust-lang.org/tools/install) |
| Podman mit Compose und laufender Podman Machine (macOS) | Angular-Frontend im Container ausführen und bauen | [Podman installieren](https://podman.io/docs/installation) |
| Tauri-Rust-CLI | Zum ausfüren der Tauri-Anwendung | ```cargo install tauri-cli --version "^2"```                |

Node.js und npm müssen auf dem Host nicht installiert sein. Sie werden im
Frontend-Container verwendet. Für Tauri sind zusätzlich die nativen
Systemvoraussetzungen des jeweiligen Zielbetriebssystems nötig:

Auf macOS muss die Podman Machine laufen. Falls sie noch nicht gestartet ist:

```bash
podman machine start
```

Für Tauri können je nach Betriebssystem weitere Systemkomponenten erforderlich sein:
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
Tauri-Hook den Angular-Dev-Server im Podman-Container:

```bash
cd app
cargo tauri dev
```

Der Dev-Hook startet den Frontend-Container. Falls er nach dem Beenden von
Tauri weiterläuft, kannst du ihn im Repository-Hauptverzeichnis stoppen:

```bash
podman compose -f containers/dev/compose.yaml down
```

## Release-Build erstellen

`tauri build` baut zuerst das Angular-Frontend im Container und verpackt danach
die erzeugten Dateien mit Tauri auf dem Host:

```bash
cd app
cargo tauri build
```

Dafür wird npm nur im Container gebraucht. Der native Tauri-Build muss trotzdem
auf dem Betriebssystem ausgeführt werden, für das die App gebaut wird.

Das separate Programm unter `backend/` wird durch diese Befehle derzeit nicht
gestartet oder in die Tauri-App eingebunden.

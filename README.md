# Übung Einaufslisten App

Hierbei handelt es sich um ein Übungsprojekt. Keine weiteren Angaben.

## Frontend starten

Im Repository-Hauptverzeichnis:

```bash
podman compose -f containers/dev/compose.yaml up --build
```

Der Server ist unter `http://localhost:1420` erreichbar. Änderungen im Ordner
`frontend` werden in den Container synchronisiert und von Angular erkannt.

## Tauri-Desktop-App starten

Die Tauri-Rust-CLI einmalig installieren:

```bash
cargo install tauri-cli --version "^2"
```

Den Frontend-Container weiterlaufen lassen und in einem zweiten Terminal
ausführen:

```bash
cd app
cargo tauri dev --config src-tauri/tauri.container.conf.json
```

Die zusätzliche Tauri-Konfiguration deaktiviert den lokalen
`beforeDevCommand`. Tauri startet daher kein zweites Frontend auf dem Host,
sondern verwendet den laufenden Dev-Server unter `http://localhost:1420`.
Rust-Codeänderungen werden weiterhin von Tauri neu gebaut; Änderungen am
Frontend werden vom Container-Dev-Server geladen.

Frontend und Tauri mit `Ctrl+C` in ihren jeweiligen Terminals beenden. Der
Container kann alternativ im Repository-Hauptverzeichnis gestoppt werden:

```bash
podman compose -f containers/dev/compose.yaml down
```

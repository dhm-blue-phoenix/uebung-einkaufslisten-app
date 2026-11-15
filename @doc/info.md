## Frontend-Abhängigkeiten installieren

```bash
cd frontend
npm ci
```

Zum separaten Starten des Frontends im Browser:

```bash
cd frontend
npm start
```

Der Server ist unter `http://localhost:1420` erreichbar. Änderungen im Ordner
`frontend` werden von Angular erkannt.

## Tauri-Desktop-App starten

Die Tauri-Rust-CLI einmalig installieren:

```bash
cargo install tauri-cli --version "^2"
```

```bash
cd app
cargo tauri dev
```

Tauri startet den Frontend-Dev-Server über den lokalen `beforeDevCommand`.
Rust- und Frontend-Codeänderungen werden während der Entwicklung erkannt.
Das Frontend nicht vorher separat mit `npm start` starten.

Tauri und den Frontend-Dev-Server mit `Ctrl+C` beenden.

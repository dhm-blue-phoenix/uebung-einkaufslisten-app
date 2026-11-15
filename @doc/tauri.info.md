# Template created! To get started run:
```cmd
    cd uebung-einkaufslisten-app
    npm install
```

### Init Android and Ios System 
```cmd
    npm run tauri android init
    npm run tauri ios init
```

### For Desktop development, run:
```cmd
    npm run tauri dev
```

### For Android development, run:
```cmd
    npm run tauri android dev
```

### For iOS development, run:
```cmd
    npm run tauri ios dev
```

## Rust
```cmd
    cd src-tauri

    cargo add rusqlite --features bundled
    cargo add serde --features derive
    cargo add serde_json
    cargo add uuid --features v4,serde
    cargo add chrono
```
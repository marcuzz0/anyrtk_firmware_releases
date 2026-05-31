# AnyRTK Firmware Releases

Binari firmware per **AnyRTK** — ricevitore GNSS RTK su ESP32 con auto-rilevamento del modulo
GNSS: **Unicore UM98x** (UM980/981/981S/982) e **u-blox ZED-F9P**.

Codice sorgente: https://github.com/marcuzz0/anyrtk

## Update OTA

Il dispositivo scarica direttamente da questo repo via menu OTA (modalità WIFI-only):

```
+++  → menu  →  [u] OTA update
```

- `[u]` poi `[l]` → scarica e installa l'**ultima** release (auto-discover via
  `/releases/latest/download/firmware.bin`)
- `[u]` poi `[r]` → **lista** release, scegli la versione specifica (API GitHub)
- `[u]` poi `[u]` → URL custom

L'OTA è **dual-bank** con rollback automatico: la nuova immagine viene marcata valida solo dopo
30 s di uptime stabile, altrimenti al boot successivo si torna al banco precedente.

## Asset naming

Ogni release deve avere un asset chiamato esattamente **`firmware.bin`**.

## Versioning

`vX.Y.Z` semver. *Latest* = quella con `published_at` più recente.

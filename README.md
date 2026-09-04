# AnyRTK Firmware Releases

Binari firmware per **AnyRTK**, il firmware unificato dei ricevitori GNSS RTK su ESP32.

Un solo binario per entrambi i prodotti: il modulo GNSS viene **rilevato al boot** e il firmware
carica il driver corrispondente.

| Prodotto | Modulo GNSS | Note |
| --- | --- | --- |
| **TRIG** | Unicore UM98x (UM980 / UM981 / UM981S / UM982) | con unità inerziale e compensazione dell'inclinazione della palina |
| **MS2** | u-blox | senza unità inerziale |

## Aggiornamento via rete

Il dispositivo scarica direttamente da questo repository dal menu di aggiornamento
(modalità WiFi):

```
+++  →  menu  →  [u] OTA update
```

- `[u]` poi `[l]` → scarica e installa l'**ultima** release
  (`/releases/latest/download/firmware.bin`)
- `[u]` poi `[r]` → **elenco** delle release, per scegliere una versione specifica
- `[u]` poi `[u]` → indirizzo personalizzato

L'aggiornamento è **a doppio banco con ripristino automatico**: la nuova immagine viene marcata
come valida solo dopo 30 s di funzionamento stabile, altrimenti al riavvio successivo si torna
al banco precedente.

## Nome dell'asset

Ogni release deve avere un asset chiamato esattamente **`firmware.bin`**: è il nome che il
dispositivo cerca.

## Versioni

Numerazione `vX.Y.Z`. *Latest* è la release con `published_at` più recente.

Si tengono **poche release contemporaneamente**, di norma una versione di riferimento più
l'ultima pubblicata: i firmware installati prima della versione 3.0.5 leggono l'elenco delle
release in un buffer da 16 KB, e un elenco più lungo impedirebbe loro di aggiornarsi.

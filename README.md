# AnyRTK Firmware Releases

Binari firmware per **AnyRTK**, il firmware unificato dei ricevitori GNSS RTK su ESP32.

Un solo firmware per tutti i prodotti: scheda e modulo GNSS vengono **rilevati al boot** e il
firmware carica il driver corrispondente.

| Prodotto | Modulo GNSS | Note |
| --- | --- | --- |
| **MS2** | u-blox | senza unità inerziale |
| **pico** | Quectel LG290P | compensazione dell'inclinazione con l'IMU IM19, se montata |
| **flip** | a innesto: u-blox, Quectel LG290P o Unicore UM980 | IMU IM19 sempre montata |

pico e flip si aggiornano da qui a partire dalle versioni che le comprendono.

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

Le release non si ritirano: il dispositivo legge soltanto le **ultime otto**. I firmware
installati prima della versione 3.0.5 leggono l'elenco in un buffer da 16 KB e si aggiornano con
«installa l'ultima» (`[u]` poi `[l]`), che non passa dall'elenco.

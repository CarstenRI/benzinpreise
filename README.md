# ⛽ Benzinpreise Deutschland

Aktuelle Kraftstoffpreise (E5, E10, Diesel) im einstellbaren Umkreis – als lokale Web-App mit PWA-Unterstützung für iPhone und Android.

## Voraussetzungen

- Python 3.8 oder neuer
- Kostenloser API-Key von [Tankerkönig](https://creativecommons.tankerkoenig.de/)

## Setup

1. `Benzinpreise.html` und `Benzinpreise_starten.py` in denselben Ordner laden
2. In `Benzinpreise.html` den eigenen API-Key eintragen:
   ```javascript
   const API_KEY = "DEIN_API_KEY_HIER";
   ```
3. App starten:
   ```bash
   python Benzinpreise_starten.py
   ```
   Der Browser öffnet sich automatisch unter `http://localhost:8765`.

## PWA-Installation auf iPhone/Android

1. App im Safari/Chrome öffnen (im Heimnetz: `http://DEINE-IP:8765`)
2. Teilen ⬆ → **„Zum Home-Bildschirm"** → Hinzufügen

## Lizenz

[MIT](LICENSE) · Preisdaten: © [Tankerkönig](https://creativecommons.tankerkoenig.de/) – [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

# ⛽ Benzinpreise Deutschland

> Aktuelle Kraftstoffpreise (E5, E10, Diesel) im einstellbaren Umkreis – als lokale Web-App mit PWA-Unterstützung für iPhone und Android.

---

## Features

- **Echtzeitpreise** via [Tankerkönig API](https://creativecommons.tankerkoenig.de/) (Creative Commons)
- **PLZ-Suche** mit einstellbarem Umkreis (1–25 km)
- **Sortierung** nach Preis, Name, Entfernung oder Status
- **Filterung** nach geöffneten / geschlossenen Tankstellen (mit Live-Anzahl)
- **Interaktive Karte** (Leaflet + OpenStreetMap) mit Marker-Clustering
- **Preisfärbung**: günstig grün → teuer rot, relativ zum Durchschnitt
- **Tageszeiten-Anzeige**: Beste Tankzeit-Empfehlung basierend auf historischen Mustern
- **Marken-Logos** über Google Favicon-Service
- **Dunkel-Design** optimiert für mobile Nutzung
- **PWA**: Als App auf iPhone / Android installierbar (funktioniert offline nach erstem Laden)

---

## Voraussetzungen

| Voraussetzung | Hinweis |
|---|---|
| Python 3.8+ | Zum Starten des lokalen Servers |
| Tankerkönig API-Key | Kostenlos unter [tankerkoenig.de](https://creativecommons.tankerkoenig.de/) |
| Internetverbindung | Für Preisabruf und Karte |

---

## Installation & Start

### 1. Dateien herunterladen

```
Benzinpreise.html
Benzinpreise_starten.py
```

Beide Dateien in denselben Ordner legen.

### 2. API-Key eintragen

`Benzinpreise.html` öffnen und den eigenen Tankerkönig-API-Key eintragen:

```javascript
// Zeile ca. 480 in Benzinpreise.html
const API_KEY = "DEIN_API_KEY_HIER";
```

### 3. App starten

```bash
python Benzinpreise_starten.py
```

Der Browser öffnet sich automatisch unter `http://localhost:8765`.

---

## Nutzung

1. **PLZ eingeben** und gewünschten Umkreis wählen
2. **Kraftstoffsorte** auswählen (E5 / E10 / Diesel)
3. **Sortieren** per Klick auf die Spaltenköpfe
4. **Karte** über den Button in der Filterleiste ein-/ausblenden
5. **Tankstelle anklicken** → öffnet Google Maps Navigation

---

## Als PWA auf dem iPhone installieren

1. App im **Safari** öffnen (im Heimnetz: `http://DEINE-IP:8765`)
2. Teilen-Button ⬆ antippen
3. **„Zum Home-Bildschirm"** → **Hinzufügen**

Die App erscheint dann wie eine native App auf dem Home-Bildschirm.

---

## Optionale Erweiterungen

### Preisprotokollierung mit Node-RED + InfluxDB

Im Repository liegt außerdem `Benzinpreise_NodeRED_Flow.json` – ein fertiger Node-RED-Flow, der die Tankerkönig-API periodisch abfragt und Preisänderungen in eine InfluxDB 2.x-Datenbank schreibt (Measurement: `kraftstoffpreise`).

Gespeicherte Felder pro Tankstelle:

| Typ | Felder |
|---|---|
| **Tags** | `station_id`, `brand`, `name`, `city`, `post_code`, `street` |
| **Fields** | `e5`, `e10`, `diesel`, `is_open`, `lat`, `lng`, `dist` |

### Grafana-Dashboard

Auf Basis der InfluxDB-Daten lässt sich ein Grafana-Dashboard aufbauen mit:
- Günstigster Preis (Stat-Panels für E5 / E10 / Diesel)
- Preisverlauf als Zeitreihe
- Geomap mit Tankstellen-Standorten
- Stationsübersicht als Tabelle
- Marken-Vergleich als Balkendiagramm

---

## Technologie

- **Frontend**: Vanilla HTML/CSS/JavaScript, kein Framework
- **Karte**: [Leaflet](https://leafletjs.com/) + [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster)
- **Geocoding**: [Nominatim](https://nominatim.openstreetmap.org/) (OpenStreetMap)
- **Preise**: [Tankerkönig API](https://creativecommons.tankerkoenig.de/)
- **Server**: Python `http.server` (kein externes Framework)

---

## Lizenz

Dieses Projekt steht unter der [MIT-Lizenz](LICENSE).  
Preisdaten: © [Tankerkönig](https://creativecommons.tankerkoenig.de/) – [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

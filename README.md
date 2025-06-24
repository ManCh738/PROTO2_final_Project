# Wetteranzeige mit Node-RED & open-meteo (Luxemburg)

[Zum GitHub-Projektboard](https://github.com/users/ManCh738/projects/2)

---

## Ziel des Projekts

Ziel dieses Projekts ist es, mithilfe von **Node-RED auf einem Raspberry Pi** aktuelle **Temperaturdaten aus Luxemburg** automatisiert über eine Wetter-API abzurufen und auf einem **Display (z. B. LCD)** auszugeben.  

Der Fokus liegt auf einem modularen Aufbau, der einfach verständlich, erweiterbar und zuverlässig läuft – ohne Cloud-Abhängigkeiten außer dem API-Zugriff.

---

##  Projektaufbau in Phasen

### Phase 1 – Grundfunktionalität

**Ziel:** Wetterdaten abrufen und Temperatur extrahieren.

**Schritte:**
- Node-RED auf Raspberry Pi installieren
- HTTP Request Node konfigurieren
- API-Daten von open-meteo für Luxemburg abrufen
- Funktion zur Extraktion der Temperatur schreiben
- Temperatur in `flow.temp` speichern

**Wichtigkeit:** Kritisch – ohne diese Phase funktioniert der Flow nicht.

---

### Phase 2 – Anzeige & Ausgabe

**Ziel:** Temperaturdaten sichtbar machen.

**Schritte:**
- LCD- oder OLED-Display anbinden
- Change Node: `msg.line = "2"` und `msg.payload = flow.temp`
- Ausgabe auf Display (Zeile 2) vorbereiten
- Optional: Test mit Debug Node durchführen

**Wichtigkeit:** Hoch – macht das Projekt sichtbar und erlebbar.

---

### Phase 3 – Optimierung & Erweiterung

**Ziel:** System robuster und informativer machen.

**Schritte:**
- Fehlerbehandlung für API-Ausfall einbauen
- Automatische Aktualisierung alle 5–10 Minuten
- Weitere Wetterinfos anzeigen (z. B. Beschreibung, Wind)
- Projektstruktur auf GitHub pflegen
- Screenshots oder Bilder einfügen

**Wichtigkeit:** Mittel – nice-to-have, nicht zwingend notwendig.

---

## Technologien & Lösungsansätze

### Verwendete Technologien
- **Node-RED**: Visuelles Tool zur Programmierung von Logikabläufen
- **Raspberry Pi**: Lokale Steuerzentrale für das Projekt
- **open-meteo API**: Kostenloser Wetterdaten-Anbieter mit JSON-Ausgabe
- **LCD-Display (I²C oder GPIO)**: Zur Anzeige der Temperatur
- **JavaScript / JSON**: Für Datenverarbeitung in Function-Nodes

---

### Lösungsansätze

- Nutzung von **Flow-Variablen (`flow.temp`)**, um Daten zwischen Nodes zu übertragen  
- Modularer Aufbau mit **klarer Trennung** von API, Logik und Ausgabe  
- Verwendung von **Change-Node**, um gezielt bestimmte Display-Zeilen anzusprechen  
- **Kein proprietäres Backend**: Alles lokal, außer der Wetterdatenquelle

---

## Warum ist dieses Projekt besonders?

- **Einfach nachbaubar**, auch für Einsteiger in Node-RED & Raspberry Pi  
- **Lokal steuerbar**, ohne aufwändige Web-Dashboards oder Drittanbieter  
- **Open-Source API (open-meteo)** – keine API-Schlüssel nötig  
- **Klar strukturiert und dokumentiert** – inkl. GitHub-Projektplan  
- **Echtzeitanzeige** von Wetterdaten auf physischem Display

---

## 📂 Projektstruktur (Dateien)
```bash
.
├── flow.json          # Node-RED Flow-Export
├── README.md          # Projektbeschreibung (diese Datei)
├── PLANNER.md         # Detaillierter Projektplan
└── screenshots/       # Optional: Displayfotos oder GIFs

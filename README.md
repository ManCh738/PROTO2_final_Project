# Finales Proto-Projekt


## Wetteranzeige mit Node-RED & Digilab auf dem LCD Bildschirm

### [Zum Projektplanner](https://github.com/users/ManCh738/projects/2)

### [Zur JSON Datei](./Wetter_NodeRed_Digilab.json)

---

## Ziel des Projekts

Ziel dieses Projekts ist es, mithilfe von **Node-RED auf einem Raspberry Pi** aktuelle **Temperaturdaten aus Luxemburg** automatisiert über meine Wetter-API abzurufen und auf meinem **LCD Display** auszugeben.  

Der Fokus liegt auf einem modularen Aufbau, der einfach verständlich, erweiterbar und zuverlässig läuft und ohne Cloud-Abhängigkeiten außer dem API-Zugriff.

---

##  Projektaufbau in Phasen

### Phase 1 – Grundfunktionalität

**Ziel:** Wetterdaten abrufen und Temperatur extrahieren.

**Schritte:**
- HTTP Request Node konfigurieren
- API-Daten von open-meteo für Luxemburg abrufen
- Funktion zur Extraktion der Temperatur schreiben
- Temperatur in `flow.temp` speichern

**Wichtig:** Dieser Schritt ist sehr wichtig, weil ohne diese Phase funktioniert der Flow nicht.

---

### Phase 2 – Anzeige & Ausgabe

**Ziel:** Temperaturdaten sichtbar machen.

**Schritte:**
- Change Node: `msg.line = "2"` und `msg.payload = flow.temp`
- Ausgabe des °C auf dem Display (Zeile 2) 
- Optional was ich aber gemacht habe: Test mit Debug Node durchführen

**Wichtig:** Dieser schritt ist sehr Wichtig und macht das Projekt sichtbar und erlebbar. 

---

## Technologien & Lösungsansätze

### Verwendete Technologien
- **Node-RED**: Visuelles Tool zur Programmierung von Logikabläufen
- **Raspberry Pi**: Lokale Steuerzentrale für das Projekt
- **open-meteo API**: Kostenloser Wetterdaten-Anbieter mit kostenloser API
- **LCD-Display**: Zur Anzeige der Temperatur von Luxemburg
- **JavaScript / JSON**: Für Datenverarbeitung in Function-Nodes

---

### Lösungsansätze

- Nutzung von **Flow-Variablen (`flow.temp`)**, um Daten zwischen Nodes zu übertragen  
- Modularer Aufbau mit **klarer Trennung** von API, Logik und Ausgabe  
- Verwendung von **Change-Node**, um gezielt bestimmte Display-Zeilen anzusprechen  
---

## Warum ist dieses Projekt besonders?

- **Einfach nachbaubar**, auch für Einsteiger in Node-RED & Raspberry Pi  
- **Lokal steuerbar**, ohne aufwändige Web-Dashboards oder Drittanbieter  
- **Open-Source API (open-meteo)** – keine API-Schlüssel nötig  
- **Klar strukturiert und dokumentiert** 
- **Echtzeitanzeige** von Wetterdaten auf physischem Display


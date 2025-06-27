  # 🌦️ Wetteranzeige mit Node-RED & Digilab (Finales Projekt)


### [Zum Projektplanner (GitHub Planner)](https://github.com/users/ManCh738/projects/2)
### [Zur Flow-Datei (Wetter_NodeRed_Digilab.json)](./wetteranzeige_luxemburg.json)
---

## Ziel des Projekts

Ziel dieses Projekts ist es, **eine automatisierte, lokale Wetteranzeige** zu realisieren, die aktuelle Temperaturdaten von Luxemburg abruft und diese auf meinem LCD-Display vom Digilab ausgibt.
Die gesamte Logik wird mithilfe von **Node-RED** und meinem **Raspberry Pi** umgesetzt. Dabei wird auf Cloud-Abhängigkeiten (außer dem API-Zugriff) bewusst verzichtet, um eine robuste, offline-taugliche Lösung zu schaffen.

Im Vordergrund stehen:
- **Echtzeit-Wettereinsicht**
- **Modularer Aufbau**
- **Praxistauglichkeit und Erweiterbarkeit**
- **Klar dokumentierte Umsetzung**

---

## Projektstruktur & Arbeitsphasen
Das Projekt wurde in klar strukturierte Phasen unterteilt, um einen sauberen Entwicklungsprozess sicherzustellen. Jede Phase ist für den Erfolg des Projekts entscheidend:


### Phase 1: Planung und Konzeption
**Ziel:**
Grundlagen für ein funktionierendes und zielgerichtetes Projekt schaffen.

**Schritte:**

**Projektziel definieren:** Klare Festlegung, was das Projekt leisten soll.

**Struktur und Zeitplan erstellen:** Grobe Planung (Github Planner) der Umsetzung in Phasen und zeitlicher Ablauf.

**Wichtigkeit:**  
Diese Phase ist essenziell. Eine gute Planung reduziert späteren Korrekturaufwand und sorgt für einen reibungslosen Ablauf.


### Phase 2: Wetterdaten abrufen

**Ziel:**  
Abruf und Verarbeitung der Temperaturdaten aus Luxemburg mithilfe der **Open-Meteo API.**

**Arbeitsschritte:**  
- Node-RED Flow erstellen  
- HTTP Request Node konfigurieren  
- Antwort als JSON empfangen und analysieren  
- Function-Node programmieren, um Temperaturwert zu extrahieren  
- Temperaturwert in Flow-Variable `flow.temp` speichern

**Wichtigkeit:**  
Wichtiger Kern des Projekts. Ohne funktionierenden Datenabruf ist die gesamte Anzeige nicht möglich.


### Phase 3: Anzeige & Ausgabe

**Ziel:**  
Temperaturwert auf dem Digilab LCD-Display ausgeben.

**Arbeitsschritte:**  
- LCD Display mit Node-RED verbinden (über entsprechenden Node)  
- `msg.line = "2"` setzen, um Zeile 2 des Displays anzusprechen  
- `msg.payload = flow.temp` setzen, um Temperatur auszugeben  
- Testen mit Debug Node  
- Formatierung implementieren

**Wichtigkeit:**  
Abschluss der Kette. Erst durch diese Phase wird das Projekt sichtbar, greifbar und bewertbar.

---

### Verwendete Technologien
- **Node-RED**: Visuelles Tool zur Programmierung von Logikabläufen
- **Raspberry Pi**: Lokale Steuerzentrale für das Projekt
- **open-meteo API**: Kostenloser Wetterdaten-Anbieter mit kostenloser API
- **LCD-Display**: Zur Anzeige des Wetterwertes von Luxemburg
- **JavaScript / JSON**: Für Datenverarbeitung in Function-Nodes

---

### Lösungsansätze & Besonderheiten

- **Modularer Aufbau:** API, Verarbeitung und Ausgabe sind klar getrennt und können einzelt getestet werden.
- **Verwendung von Flow-Variablen:** Daten wie `flow.temp` ermöglichen sauberen, übergreifenden Datenfluss zwischen Nodes.
- **Change & Function Nodes:** Steuerung der Anzeigezeile und Ausgabeformat durch gezielte Programmierung.
- **Keine API-Schlüssel notwendig:** Open-Meteo erlaubt anonymen Zugriff. Dies ist ideal für mein Projekt.

---

## Warum ist dieses Projekt besonders?

- Es ist **Lokal steuerbar**, ohne aufwändige Web-Dashboards oder Drittanbieter  
- Bei der **Open-Source API** benötigt man keine API-Schlüssel
- Ich habe alles **Klar strukturiert und dokumentiert** 
- **Echtzeitanzeige** von Wetterdaten auf dem LCD-Display


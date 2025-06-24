##  Projektziel

Ziel dieses Projekts ist es, ein Musiksteuerungssystem zu entwickeln, das über physische Buttons (S1–S6) Spotify-Funktionen wie „nächster Titel“, „vorheriger Titel“, „Wiedergabe starten/pausieren“ steuert und gleichzeitig auf einem LCD-Bildschirm den aktuellen Musiktitel anzeigt.  
Die Steuerung erfolgt über ein Raspberry Pi in Verbindung mit einem Digilab-Modul. Die Programmierung und Steuerlogik wird vollständig mit **Node-RED** umgesetzt. Spotify wird über die **offizielle Web API** eingebunden.

--- 

## Projektübersicht
### [Link zu meinem Projekt-Planner](https://github.com/users/ManCh738/projects/2/views/1)
---

##  Projektphasen & Arbeitsschritte

### Phase 1 – Infrastruktur & Verbindungen
**Ziel:** Verbindung zwischen Raspberry Pi, Digilab und Spotify vorbereiten  
**Arbeitsschritte:**
- GPIO-Kommunikation mit Buttons über Node-RED einrichten  
- OAuth-Authentifizierung für Spotify API durchführen  
- Testabfragen aus Node-RED an Spotify senden

---

### Phase 2 – Tastensteuerung
**Ziel:** Spotify-Funktionen über Buttons auslösen  
**Arbeitsschritte:**
- S1: Nächster Titel 
- S2: Vorheriger Titel 
- S5: Wiedergabe pausieren 
- S6: Wiedergabe starten
- Node-RED `http request`-Nodes konfigurieren  
- Zugriffs-Token verwalten

---

### Phase 3 – LCD-Ausgabe
**Ziel:** Anzeige von Songtitel und Interpret auf LCD-Display  
**Arbeitsschritte:**
- Abfrage von aktuell gespieltem Song 
- Ausgabe über I2C-Display 
- Text kürzen/scrollen bei langen Titeln  

---
### Phase 4 - Verwendete Features des Digilab

 **Tastenfeld (S1–S6):**
- S1: Nächster Song  
- S2: Vorheriger Song  
- S5: Wiedergabe pausieren  
- S6: Wiedergabe starten  

Diese Buttons sind direkt über das Digilab angeschlossen und mit **`rpi-gpio in`-Nodes** in Node-RED verbunden.

---

### Phase 5 – Dokumentation
**Ziel:** Technische Dokumentation und Benutzeranleitung  
**Arbeitsschritte:**
- Aufbau der `README.md`  
- Node-RED Flows dokumentieren  
- Authentifizierungsprozess und API-Verwendung erklären  

---

##  Technologien & Tools

- **Raspberry Pi 4** – zentrale Steuerungseinheit  
- **Node-RED** – visuelle Programmierplattform  
- **Spotify Web API** – Steuerung der Musikwiedergabe  
- **OAuth 2.0 (Authorization Code Flow)** – für sichere Spotify-Zugriffe  
- **Digilab Modul** – GPIO-Eingabe über Buttons  
- **LCD 16x2 (I2C)** – für Songanzeige  
- **Node-RED LCD Nodes** – zur Ansteuerung des Displays  

---

##  Lösungsansätze

- **Buttonsteuerung via GPIO:** Node-RED empfängt Tastensignale über `rpi-gpio in` Nodes  
- **Spotify-Steuerung per API:** HTTP-Requests an Spotify mit aktuellen Access-Tokens 
- **Metadaten-Anzeige:** Titel und Interpret werden regelmäßig abgefragt und per I2C-LCD angezeigt  
- **Token-Management:** Access-Token werden mit dem Refresh-Token zyklisch erneuert   
- **Fehlerbehandlung:** Prüfung auf Offline-Geräte, nicht autorisierte Requests oder abgelaufene Tokens  

---

##  Was macht dieses Projekt einzigartig?

Dieses Projekt vereint Hardware-Eingabe (Tasten), Webservice-Steuerung (Spotify API) und visuelles Feedback (LCD) in einem vollständig lokal steuerbaren, grafisch entwickelten Node-RED Flow. Die Integration der Spotify Web API in eine Raspberry-Pi-basierte Hardwarelösung ist nicht nur funktional, sondern auch ein hervorragendes Beispiel für modernes IoT-Prototyping mit Fokus auf Musik und Medien.  
Es ist ein ideales Lernprojekt für Themen wie: API-Nutzung, OAuth2, GPIO, LCD-Steuerung und Node-RED-Visualisierung.

## Hier ist der JSON code:

[
    {
        "id": "spotify-lcd",
        "type": "tab",
        "label": "Spotify Digilab",
        "disabled": false,
        "info": ""
    },
    {
        "id": "btn-play",
        "type": "rpi-gpio in",
        "z": "spotify-lcd",
        "name": "S6 ▶ Play",
        "pin": "24",
        "intype": "tri",
        "debounce": "50",
        "read": false,
        "bcm": true,
        "x": 140,
        "y": 60,
        "wires": [
            [
                "cmd-play"
            ]
        ]
    },
    {
        "id": "btn-stop",
        "type": "rpi-gpio in",
        "z": "spotify-lcd",
        "name": "S5 ■ Pause",
        "pin": "23",
        "intype": "tri",
        "debounce": "50",
        "read": false,
        "bcm": true,
        "x": 140,
        "y": 140,
        "wires": [
            [
                "cmd-pause"
            ]
        ]
    },
    {
        "id": "btn-next",
        "type": "rpi-gpio in",
        "z": "spotify-lcd",
        "name": "S1 ▶▶ Next",
        "pin": "16",
        "intype": "tri",
        "debounce": "50",
        "read": false,
        "bcm": true,
        "x": 140,
        "y": 220,
        "wires": [
            [
                "cmd-next"
            ]
        ]
    },
    {
        "id": "btn-prev",
        "type": "rpi-gpio in",
        "z": "spotify-lcd",
        "name": "S2 ◀◀ Prev",
        "pin": "19",
        "intype": "tri",
        "debounce": "50",
        "read": false,
        "bcm": true,
        "x": 140,
        "y": 300,
        "wires": [
            [
                "cmd-prev"
            ]
        ]
    },
    {
        "id": "cmd-play",
        "type": "change",
        "z": "spotify-lcd",
        "name": "Setze Play",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "play",
                "tot": "str"
            }
        ],
        "x": 360,
        "y": 60,
        "wires": [
            [
                "exec-spotify"
            ]
        ]
    },
    {
        "id": "cmd-pause",
        "type": "change",
        "z": "spotify-lcd",
        "name": "Setze Pause",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "pause",
                "tot": "str"
            }
        ],
        "x": 360,
        "y": 140,
        "wires": [
            [
                "exec-spotify"
            ]
        ]
    },
    {
        "id": "cmd-next",
        "type": "change",
        "z": "spotify-lcd",
        "name": "Setze Next",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "next",
                "tot": "str"
            }
        ],
        "x": 360,
        "y": 220,
        "wires": [
            [
                "exec-spotify"
            ]
        ]
    },
    {
        "id": "cmd-prev",
        "type": "change",
        "z": "spotify-lcd",
        "name": "Setze Prev",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "prev",
                "tot": "str"
            }
        ],
        "x": 360,
        "y": 300,
        "wires": [
            [
                "exec-spotify"
            ]
        ]
    },
    {
        "id": "exec-spotify",
        "type": "exec",
        "z": "spotify-lcd",
        "command": "python3 /home/charly/digilab/spotify_control.py ",
        "addpay": "payload",
        "append": "",
        "useSpawn": "false",
        "timer": "",
        "winHide": false,
        "name": "Spotify Control",
        "x": 600,
        "y": 180,
        "wires": [
            [],
            [
                "debug"
            ],
            []
        ]
    },
    {
        "id": "debug",
        "type": "debug",
        "z": "spotify-lcd",
        "name": "Spotify Debug",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 800,
        "y": 180,
        "wires": []
    },
    {
        "id": "lcd-display",
        "type": "exec",
        "z": "spotify-lcd",
        "command": "python3 /home/charly/digilab/spotify_control.py ",
        "addpay": "payload",
        "append": "",
        "useSpawn": "false",
        "timer": "",
        "winHide": false,
        "name": "LCD ausgabe",
        "x": 600,
        "y": 260,
        "wires": [
            [],
            [],
            []
        ]
    },
    {
        "id": "forward-to-lcd",
        "type": "link in",
        "z": "spotify-lcd",
        "name": "→ Display",
        "links": [],
        "x": 420,
        "y": 340,
        "wires": [
            [
                "lcd-display"
            ]
        ]
    }
]


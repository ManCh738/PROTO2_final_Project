# PROTO2_final_Project

Ziel dieses Projekts ist es, ein Musiksteuerungssystem zu entwickeln, das über physische Buttons (S1–S6) Musikfunktionen wie „nächster Titel“, „vorheriger Titel“, „Musik starten/stoppen“ steuert und gleichzeitig auf einem LCD-Bildschirm den aktuellen Musiktitel sowie den Interpreten anzeigt. Die Steuerung erfolgt über ein Raspberry Pi, das mit einem externen Digilab-Modul verbunden ist. Dies ermöglicht eine intuitive und direkte Musikkontrolle ohne grafische Benutzeroberfläche.

---

##  Projektphasen & Arbeitsschritte

### Phase 1 – Infrastruktur & Verbindungen
**Ziel:** Grundverbindung zwischen Raspberry Pi und Digilab herstellen  
**Arbeitsschritte:**
- Verbindung und Kommunikation testen  
- GPIO-Funktionalität prüfen  

**Wichtigkeit:**  Kritisch – Grundvoraussetzung für alle weiteren Phasen

---

### Phase 2 – Hardware-Logik für Tasten
**Ziel:** Tastenfunktionalität (S1–S6) implementieren  
**Arbeitsschritte:**
- S1: Nächster Song  
- S2: Vorheriger Song  
- S5: Musik pausieren  
- S6: Musik abspielen  

**Wichtigkeit:**  Kritisch – Benutzerinteraktion steht im Zentrum des Projekts

---

### Phase 3 – LCD-Ausgabe
**Ziel:** Songtitel und Interpret auf einem LCD anzeigen  
**Arbeitsschritte:**
- Verbindung mit LCD herstellen  
- Anzeige von Metadaten formatieren  

**Wichtigkeit:**  Wichtig – Visuelle Rückmeldung verbessert die Benutzererfahrung

---

### Phase 4 – Dokumentation
**Ziel:** Technische und Benutzer-Dokumentation erstellen  
**Arbeitsschritte:**
- Diese `README.md` schreiben  
- Quellcode kommentieren  

**Wichtigkeit:**  Moderat – Erhöht Nachvollziehbarkeit und Reproduzierbarkeit

---

##  Technologien & Tools

- **Raspberry Pi 4** – als zentrale Steuerungseinheit  
- **Digilab Modul** – für physische Button-Schnittstelle  
- **Python** – Hauptprogrammiersprache für GPIO-Handling und Musiksteuerung  
- **LCD 16x2 Display (I2C)** – zur Anzeige von Titelinformationen  
- **mpg123 / VLC** – zur Musikwiedergabe über CLI  

---

##  Lösungsansätze

- **GPIO-Tasten-Events:** Die Buttons lösen Interrupts aus, die mit spezifischen Callback-Funktionen verknüpft sind.  
- **LCD-Anzeige:** Mittels I2C-Kommunikation wird der aktuelle Songtitel und Interpret angezeigt.  
- **Modularer Aufbau:** Code wird in logische Module getrennt, z. B. `button_control.py`, `lcd_display.py`, `music_player.py`.  
- **Fehlerbehandlung:** Debouncing der Buttons, Prüfung auf Song-Ende, Fallback bei leeren Metadaten.

---

##  Was macht dieses Projekt einzigartig?

Dieses Projekt kombiniert klassische Embedded-Systeme (Buttonsteuerung und LCD-Ausgabe) mit moderner Software für Musiksteuerung. Es ermöglicht eine einfache, bildschirmlose Bedienung, die besonders für Maker-Projekte, DIY-Jukeboxes oder barrierefreie Bedienkonzepte interessant ist. Die Lösung ist kompakt, nachvollziehbar und modular aufgebaut – ideal als Einstieg in GPIO-Programmierung und Embedded-Prototyping mit Raspberry Pi.

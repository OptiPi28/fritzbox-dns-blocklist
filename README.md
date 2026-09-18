# FRITZ!Box DNS-Blocklist

DNS-Blockliste im Wildcard-Domain-Format für den **DNS-Filter von FRITZ!OS 8.40+**.
Basierend auf der [ppfeufer/adguard-filter-list](https://github.com/ppfeufer/adguard-filter-list) (GPLv3).

## Voraussetzungen

- **FRITZ!OS 8.40 oder neuer** (Labor-Firmware)
  - Download: [FRITZ! Labor](https://fritz.labor.avm.de)
  - Vor der Installation: **Konfigurations-Backup mit Kennwort** anlegen
  - Unterstützte Modelle u.a.: 7690, 7630, 7590 AX, 7590, 7530 AX, 5690 Pro, 5690, 6690, 6670, 6660, 4690, 4050
- Fritzbox muss als **DNS-Server** für das Heimnetz konfiguriert sein

## Einrichtung

1. **Labor-Firmware installieren**
   - FRITZ! Labor → passende Box auswählen → Update herunterladen → entpacken
   - In der Fritzbox: **System → Update → Update aus Datei starten** → Image auswählen

2. **DNS-Filter aktivieren**
   - **Heimnetz → Netzwerk → Netzwerkeinstellungen**
   - Auf **Erweiterte Netzwerkeinstellungen ändern** klicken
   - Reiter **DNS-Filter** → Haken bei *FRITZ!Box als DNS-Filter* setzen

3. **Blockliste hinzufügen**
   - In der DNS-Filter-Ansicht auf **Filterliste hinzufügen** klicken
   - **Name:** z.B. `ppfeufer-wildcard`
   - **URL:**
     ```
     https://raw.githubusercontent.com/OptiPi28/fritzbox-dns-blocklist/main/blocklist-fritz.txt
     ```
   - Speichern

4. **Fertig** — die Fritzbox lädt die Liste automatisch und filtert alle DNS-Anfragen des Heimnetzes.

## Verhalten

- Angefragte Domains aus der Liste werden mit `0.0.0.0` beantwortet → Verbindung läuft ins Leere
- Gilt für **alle Geräte** im Heimnetz, die die Fritzbox als DNS-Server nutzen
- Die Fritzbox aktualisiert die Liste automatisch (Intervall einstellbar)

## False-Positives / Ausnahmen

Wenn eine Website oder App nicht mehr funktioniert:

1. In der Fritzbox: **Heimnetz → Netzwerk → Netzwerkeinstellungen → Erweiterte Netzwerkeinstellungen → DNS-Filter**
2. Im Bereich **Ausnahmen** die betroffene Domain eintragen
3. Speichern

## Listen-Format

- Eine Domain pro Zeile, ohne Präfix
- Beispiel: `doublepimp.com` blockt die Domain **und alle Subdomains**
- Keine AdGuard-/Pi-hole-Syntax (`||`, `^`, `$`, Regex)
- Kommentare (`!` oder `#`) werden ignoriert


## Quelle & Lizenz

- **Quelle:** [ppfeufer/adguard-filter-list](https://github.com/ppfeufer/adguard-filter-list) (GPLv3)
- **Lizenz:** [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)

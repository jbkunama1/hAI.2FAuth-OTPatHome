# hAI.2FAuth-OTPatHome

Docker Compose Stack für **2FAuth** – eigene 2FA-Token-Verwaltung, gehostet zuhause.

## Setup

```bash
# 1. Stack klonen
git clone https://github.com/jbkunama1/hAI.2FAuth-OTPatHome.git
cd hAI.2FAuth-OTPatHome

# 2. Externes Netzwerk erstellen (einmalig)
docker network create highfishNetwork

# 3. Umgebungsvariablen anlegen und individuell anpassen
cp .env.example .env

# 4. Stack starten
docker compose up -d
```

2FAuth ist danach erreichbar unter: `http://<deine-IP>:4444`

## Wichtige Variablen

| Variable | Beschreibung |
| --- | --- |
| `APP_KEY` | 32-Zeichen-Sicherheitsschlüssel – erzeugen mit `openssl rand -base64 32` |
| `APP_URL` | Öffentliche URL der Instanz (z.B. `http://otp.arbeitermili.eu`) |
| `HTTP_PORT` | Host-Port, unter dem 2FAuth erreichbar ist |
| `DATA_DIR` | Verzeichnis mit den Daten (SQLite-DB liegt darunter) |

## Netzwerk

Der Stack nutzt das externe Netzwerk `highfishNetwork`, damit weitere Stacks
(z.B. ein Reverse-Proxy) mit 2FAuth kommunizieren können.
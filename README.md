# hAI.2FAuth-OTPatHome
[![Status](https://img.shields.io/badge/status-active-brightgreen?style=for-the-badge)](https://github.com/jbkunama1/hAI.2FAuth-OTPatHome)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://github.com/jbkunama1/hAI.2FAuth-OTPatHome)
[![2FA](https://img.shields.io/badge/2FA-TOTP-6f42c1?style=for-the-badge&logo=lock&logoColor=white)](https://github.com/jbkunama1/hAI.2FAuth-OTPatHome)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)


[![Buy me a coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://www.buymeacoffee.com/highfish)

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


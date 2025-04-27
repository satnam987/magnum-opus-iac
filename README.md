# Uptime Kuma Monitoring System - Ansible Deployment

Dit project is ontwikkeld als onderdeel van de Infrastructure-as-code Magnum Opus opdracht voor AP Hogeschool.

## Project Specificaties

### Basis Vereisten

- Draait op Rocky Linux 9 (verplicht)
- Volledig geautomatiseerde installatie via Ansible
- Configureerbaar via één YAML configuratiebestand
- Beveiligd met Let's Encrypt certificaten
- Docker-gebaseerde deployment met:
  - Docker Compose configuratie
  - Automatische opstart
  - Volume management
  - Netwerk configuratie
- Firewall beveiliging:
  - Alleen noodzakelijke poorten open
  - SSH (poort 22) toegang
  - Logging van geblokkeerde toegang

### Beveiligingsmaatregelen

- Firewall configuratie met alleen essentiële poorten
- Automatische Let's Encrypt certificaat vernieuwing
- Docker security best practices
- Systeem hardening
- Secure volume permissions

### Voorwaarden voor Deployment

De rol verwacht een minimale Rocky Linux 9 installatie met:

- Geconfigureerd IP-adres
- SSH key-pair authenticatie voor root toegang
- Minimale systeemvereisten:
  - 2GB RAM
  - 2 CPU cores
  - 20GB schijfruimte

## Configuratie

Alle configuratie gebeurt via één YAML bestand: `inventory/group_vars/all.yml`

Belangrijke configuratie variabelen:

```yaml
# Systeem configuratie
hostname: "uptime.example.com"
timezone: "Europe/Brussels"

# Uptime Kuma configuratie
uptime_kuma_port: 3001
uptime_kuma_version: "latest"

# SSL/TLS configuratie
enable_ssl: true
ssl_email: "admin@example.com"

# Firewall configuratie
allowed_ssh_networks:
  - "192.168.1.0/24"
```

## Installatie

1. Clone deze repository
2. Pas de configuratie aan in `inventory/group_vars/all.yml`
3. Voer het playbook uit:

```bash
ansible-playbook -i inventory/hosts.yml site.yml
```

## Componenten

- Uptime Kuma monitoring systeem
- Docker & Docker Compose
- Nginx reverse proxy (optioneel)
- Let's Encrypt certificaten
- Firewall configuratie
- Systeem hardening

## Bronvermeldingen

Dit project maakt gebruik van de volgende bronnen:

- Uptime Kuma: [https://github.com/louislam/uptime-kuma](https://github.com/louislam/uptime-kuma)
- Let's Encrypt: [https://letsencrypt.org/](https://letsencrypt.org/)

## Ontwikkeling

- Auteur: [Jouw Naam]
- Versie: 1.0.0
- Datum: [Datum]

## Licentie

MIT License

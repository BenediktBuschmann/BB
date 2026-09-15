# Docker Grundlagen

Dieses Repository enthält Docker-Compose-Dateien für Pi-hole, Portainer, Watchtower und Nginx.

Die Inhalte basieren auf dem c't-3003-Video und dem dazugehörigen GitHub-Gist:

https://gist.github.com/jamct/2e6c03f60319423bc4bc6c23fc0aa359

## Mit Docker arbeiten

Laufende Container anzeigen:

```bash
docker ps
```

Alle Container anzeigen, einschließlich gestoppter Container:

```bash
docker ps -a
```

Einen Container anhalten:

```bash
docker stop <Containername>
```

Einen gestoppten Container löschen:

```bash
docker rm <Containername>
```

## Einen einfachen Webserver starten

Ein Nginx-Container kann mit folgendem Befehl gestartet werden:

```bash
docker run -p 80:80 nginx
```

## Mit Docker Compose arbeiten

Eine Compose-Anwendung im Hintergrund starten:

```bash
docker compose up -d
```

Eine Compose-Anwendung beenden:

```bash
docker compose down
```

Neue Versionen der verwendeten Images herunterladen:

```bash
docker compose pull
```

## Projektstruktur

```text
Docker_basics_Buschmann/
├── README.md
├── .gitignore
├── pihole/
│   └── pihole.yml
├── portainer/
│   └── portainer.yml
├── watchtower/
│   └── watchtower.yml
└── nginx/
    └── nginx.yml
```

## Anwendungen starten

### Pi-hole

```bash
docker compose -f pihole/pihole.yml up -d
```

Weboberfläche:

```text
http://localhost/admin
```

Pi-hole beenden:

```bash
docker compose -f pihole/pihole.yml down
```

### Portainer

```bash
docker compose -f portainer/portainer.yml up -d
```

Weboberfläche:

```text
http://localhost:9000
```

Portainer beenden:

```bash
docker compose -f portainer/portainer.yml down
```

### Watchtower

```bash
docker compose -f watchtower/watchtower.yml up -d
```

Watchtower beenden:

```bash
docker compose -f watchtower/watchtower.yml down
```

### Nginx

```bash
docker compose -f nginx/nginx.yml up -d
```

Webseite:

```text
http://localhost:8080
```

Nginx beenden:

```bash
docker compose -f nginx/nginx.yml down
```

## Sicherheit

Passwörter und andere Zugangsdaten dürfen nicht im GitHub-Repository gespeichert werden.
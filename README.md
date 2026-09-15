# Docker Grundlagen

In diesem Projekt habe ich mich mit Docker und verschiedenen Docker-Containern beschäftigt. Dafür habe ich Pi-hole, Portainer, Watchtower und Nginx eingerichtet und getestet.


## Pi-hole

### Aufgabe und Zweck

Pi-hole ist ein DNS-Server, der Werbung und Trackinganfragen im Netzwerk blockieren kann. Weitere Informationen gibt es auf der [Pi-hole-Webseite](https://pi-hole.net/).

### Docker-Image

```text
pihole/pihole:latest
```


### Pi-hole starten

```powershell
docker compose -f pihole/pihole.yml up -d
```

### Pi-hole beenden

```powershell
docker compose -f pihole/pihole.yml down
```

## Portainer

### Aufgabe und Zweck

Portainer bietet eine Weboberfläche, über die Docker-Container, Images, Netzwerke und Volumes verwaltet werden können. Weitere Informationen gibt es auf der [Portainer-Webseite](https://www.portainer.io/).

### Docker-Image

```text
portainer/portainer-ce
```

### Verwendete Ports

Portainer verwendet den Port `9000/TCP` für die Weboberfläche.

Die Weboberfläche kann über diese Adresse geöffnet werden:

```text
http://localhost:9000
```

### Portainer starten

```powershell
docker compose -f portainer/portainer.yml up -d
```

### Portainer beenden

```powershell
docker compose -f portainer/portainer.yml down
```

## Watchtower

### Aufgabe und Zweck

Watchtower überprüft die Images von Docker-Containern auf neue Versionen. Wenn eine neue Version verfügbar ist, kann Watchtower das neue Image herunterladen und den Container aktualisieren. Weitere Informationen gibt es in der [Watchtower-Dokumentation](https://containrrr.dev/watchtower/).

### Docker-Image

```text
containrrr/watchtower
```

### Ports und Weboberfläche

Watchtower hat in dieser Konfiguration keine eigene Weboberfläche. Deshalb wird kein Port für eine Weboberfläche benötigt.

Die Funktion kann über den Containerstatus und die Logs kontrolliert werden:

```powershell
docker compose -f watchtower/watchtower.yml logs
```

### Watchtower starten

```powershell
docker compose -f watchtower/watchtower.yml up -d
```

### Watchtower beenden

```powershell
docker compose -f watchtower/watchtower.yml down
```

## Nginx

### Aufgabe und Zweck

Nginx ist ein Webserver. In diesem Projekt habe ich Nginx verwendet, um eine einfache Webseite über einen Docker-Container bereitzustellen. Weitere Informationen gibt es auf der [Nginx-Webseite](https://nginx.org/).

### Docker-Image

```text
nginx:latest
```

### Verwendete Ports

Der Host-Port `8080` wird an den Container-Port `80` weitergeleitet:

```text
8080:80
```

Die Webseite kann über diese Adresse geöffnet werden:

```text
http://localhost:8080
```

### Nginx starten

```powershell
docker compose -f nginx/nginx.yml up -d
```

### Nginx beenden

```powershell
docker compose -f nginx/nginx.yml down
```

## Container kontrollieren

```powershell
docker ps
```

Mit diesem Befehl werden auch gestoppte Container angezeigt:

```powershell
docker ps -a
```

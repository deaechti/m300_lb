# Dokumentation LB3 - Docker-Compose MariaDB+phpMyAdmin

## Inhaltsverzeichnis
1. [Einleitung](#introduction)
1. [Tutorial](#tutorial)
1. [Der Code im Detail](#codeexplained)
1. [Testing der Lösung](#testing)
1. [Verwendete Quellen](#sources)

## Einleitung <a name="introduction"></a>
Dieses Projekt wurde im Rahmen der LB3 im Modul 300 in der Teschnischen Berufsschule Zürich erstellt.

Da ich am Tag der Einführung zum Projekt krank war, hatte ich Probleme ins Projekt zu starten, am Ende konnte ich es jedoch gut durchführen.

Einbegriffen in den Container sind 2 VMs, eine MariaDB und ein phpMyAdmin zur Verwaltung.

## Tutorial <a="tutorial"></a>
1. Git Bash im Ordner mit docker-compose.yml öffnen
1. In Git Bash `docker-compose up`
1. In beliebigem Webbrowser `http://localhost:8080` aufrufen
1. Mit Username "root" und Passwort "root" anmelden
1. Wenn man die Container nicht mehr braucht, mit `docker-compose down` herunterfahren

## Der Code im Detail <a name="codeexplained"></a>
> `version: "2"`  
  
Hier wird die Version des docker-compose files festgelegt.

> ```
>    networks:
>       v_net:
>           ipam:
>               driver: default
>               config:
>                   - subnet: 192.168.60.0/24
>```

Hier wird das Netzwerk mit dem Subnetz `192.168.60.0/24` definiert

> `services:`

Hiernach werden die verschiedenen Services im Container beschrieben

> 

## Testing der Lösung <a name="testing"></a>

## Verwendete Quellen <a name="sources"></a>
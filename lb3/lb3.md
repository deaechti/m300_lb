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

> ```
>   db:
>          image: mariadb
>          environment:
>               - MYSQL_ROOT_PASSWORD=root
>               - MYSQL_DATABASE=defaultdb
>          volumes:
>               - ./database:/var/lib/mysql
>          networks:
>           v_net:
>               ipv4_address: 192.168.60.100
>```

Hier wird der db-Service definiert, als image wird das mariadb image von docker genommen, in `environment:` werden Passwort und Datenbankname festgelegt.
In `volumes` werden gesyncte Ordner definiert, hier ist er im Unterordner "database".
In `networks` wird die IP-Adresse im oben erwähnten Netzwerk definiert.

> ```
>  phpmyadmin:
>      image: phpmyadmin/phpmyadmin
>      container_name: phpmyadmin
>      environment:
>          - PMA_HOST=db
>      restart: always
>      ports:
>          - 8080:80
>      volumes:
>          - /sessions
>      links:
>          - db
>      networks:
>        v_net:
>            ipv4_address: 192.168.60.101
> ```

Dann wird der phpMyAdmin Service definiert. In `environment:` wird unter der Variable `PMA_HOST` der Service, den man mit phpMyAdmin administriert definiert, in diesem Fall der db-Service.
Unter `ports:` wird die Portweiterleitung von 80 auf 8080 definiert.
Auch hier wird zuletzt die IP-Adresse im v_net festgelegt.

## Testing der Lösung <a name="testing"></a>
|Nr.   |Eingabe   |Erwartetes Resultat   |Erhaltenes Resultat   |OK/NOK   |
|:-:|---|---|---|:-:|
|1   |in Git Bash `docker-compose up` machen   |Container startet   |Container startet   |OK   |
|2   |Nach dem Starten auf "http://localhost:8080" gehen   |phpMyAdmin Loginfenster öffnet sich   |phpMyAdmin Loginfenster öffnet sich   |OK   |
|3   |Auf phpMyAdmin mit Username `root` Passwort `root` anmelden  |Login funktioniert   |Login funktioniert   |OK   |
|4   |Nach dem Gebrauch mit `docker-compose down` Container löschen  |Container werden aus Docker Desktop gelöscht  | Container werden aus Docker Desktop gelöscht  |OK  |
## Verwendete Quellen <a name="sources"></a>
- Docker Compose Tutorial [docs.docker.com](https://docs.docker.com/compose/gettingstarted/)
![Coversheet README](https://github.com/deaechti/m300_lb/blob/2d8c26848118fa98897fe05db46cf9568ca595a5/img/cover.png)

## Inhaltsverzeichnis
1. [Einleitung](#introduction)
1. [Visio zur Vagrantbox](#visio)
1. [Der Code im Detail](#codeexplained)
1. [Testing der Lösung](#testing)
1. [Verwendete Quellen](#sources)

## Einleitung <a name="introduction"></a>
Dieses Projekt wurde im Rahmen der LB2 im Modul 300 in der Teschnischen Berufsschule Zürich erstellt.

Ich wollte als Projekt nicht all zu grosses machen und habe in Vagrant eher auf eine simple aber effektive Lösung gesetzt.  

Die Lösung startet automatisch eine Ubuntu VM und installiert einen Apache Webserver. Danach wird ein simples Skript zum darstellen des Datums und der aktuellen Systemprozessen in einem Textfile erstellt und mit executable-Rechten vergeben. Das Skript wird initial ausgeführt. Zuletzt wird noch ein automatisierter Cronjob ausgeführt, damit die Daten immer aktuell bleiben.

## Visio zur Vagrantbox <a name="visio"></a>
![Visio Umgebung](https://github.com/deaechti/m300_lb/blob/0b60e5cdc9acc233afdbb2f939b506df52693e93/img/visio.png)

## Der Code im Detail <a name="codeexplained"></a>
>`Vagrant.configure(2) do |config|`  

Hier wird die Konfiguration von der Vagrantbox gestartet. die `2` legt fest, dass die neuste Version von Vagrant verwendet wird.

>`config.vm.box = "ubuntu/xenial64"`  

Hier wird das Betriebssystem der VM festgelegt, in diesem Falle eine Ubuntu/Xenial 64-bit Maschine.

>`config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true`  

Hier wird die Portweiterleitung konfiguriert. Der Port 80 der VM wird auf den Port 8080 auf dem Hostsystem weitergeleitet. `auto_correct: true` legt fest, dass allfällige Kollisionen (z.B. falls Port 8080 auf dem Host bereits belegt ist) automatisch korrigiert werden.

>`config.vm.synced_folder ".", "/var/www/html"`  

Die Synchronisierten Ordner werden direkt mit dem Hostsystem synchronisiert, also sind die Files aus `/var/www/html` auch auf dem Hostsystem im Ordner mit dem Vagrantfile gespeichert werden.

>`config.vm.provider "virtualbox" do |vb|`  

Hier wird der Hypervisor definiert, in diesem Fall VirtualBox. Hier wird auch direkt die Konfiguration in VirtualBox gestartet.

>`vb.memory = "512"`  

Der RAM wird in MB definiert.

>`config.vm.provision "shell", inline: <<-SHELL`  

Die konfiguration in der Linux-Konsole wird gestartet.

>`sudo apt-get update`  
>`sudo apt-get -y install apache2`  

Der Appkatalog wird aktualisiert und der Apache-Webservice wird installiert.



## Testing der Lösung <a name="testing"></a>


## Verwendete Quellen <a name="sources"></a>
- Template für Vagrantfile [M300 Github von Marco Berger](https://github.com/mc-b/M300/tree/master/vagrant/web)
- Neuen Cronjob als Einzeiler [StackOverflow](https://stackoverflow.com/questions/878600/how-to-create-a-cron-job-using-bash-automatically-without-the-interactive-editor)
- Zeitzone für `date` Command ändern [StackOverflow](https://unix.stackexchange.com/questions/48101/how-can-i-have-date-output-the-time-from-a-different-timezone)
- Cheat Sheets für Markdown [Mgitarkdown.org](https://www.markdownguide.org/basic-syntax/) ; [Markdownguide.org](https://www.markdownguide.org/extended-syntax/)
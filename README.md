![Coversheet README](https://github.com/deaechti/m300_lb/blob/2d8c26848118fa98897fe05db46cf9568ca595a5/img/cover.png)

## Inhaltsverzeichnis
1. [Einleitung](#introduction)
1. [Visio zur Vagrantbox](#visio)
1. [Informationen zu der Vagrantbox](#vagrantinfo)
1. [Der Code im Detail](#codeexplained)
1. [Testing der Lösung](#testing)
1. [Verwendete Quellen](#sources)

## Einleitung <a name="introduction"></a>
Dieses Projekt wurde im Rahmen der LB2 im Modul 300 in der Teschnischen Berufsschule Zürich erstellt.

Ich wollte als Projekt nicht all zu grosses machen und habe in Vagrant eher auf eine simple aber effektive Lösung gesetzt.  

Die Lösung startet automatisch eine Ubuntu VM und installiert einen Apache Webserver. Danach wird ein simples Skript zum darstellen des Datums und der aktuellen Systemprozessen in einem Textfile erstellt und mit executable-Rechten vergeben. Das Skript wird initial ausgeführt. Zuletzt wird noch ein automatisierter Cronjob ausgeführt, damit die Daten immer aktuell bleiben.

## Visio zur Vagrantbox <a name="visio"></a>


## Informationen zu der Vagrantbox <a name="vagrantinfo"></a>
Login ubuntu:vagrant
vagrant

## Der Code im Detail <a name="codeexplained"></a>


## Testing der Lösung <a name="testing"></a>


## Verwendete Quellen <a name="sources"></a>
- Template für Vagrantfile [M300 Github von Marco Berger](https://github.com/mc-b/M300/tree/master/vagrant/web)
- Neuen Cronjob als Einzeiler [StackOverflow](https://stackoverflow.com/questions/878600/how-to-create-a-cron-job-using-bash-automatically-without-the-interactive-editor)
- Zeitzone für `date` Command ändern [StackOverflow](https://unix.stackexchange.com/questions/48101/how-can-i-have-date-output-the-time-from-a-different-timezone)
- Cheat Sheets für Markdown [Markdown.org](https://www.markdownguide.org/basic-syntax/) ; [Markdownguide.org](https://www.markdownguide.org/extended-syntax/)
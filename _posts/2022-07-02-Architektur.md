---
toc: true
layout: post
description: Dieser Post beschreibt angewandte Architekturen und Tools für Frunch Infinity 2.0
categories: [markdown]
title: 02 Architektur
---

# Systemarchitektur
<p style="text-align: justify;">Die Systemarchitektur für Frunch Infinity 2.0 stellt eine Client-Server-Architektur dar. Dabei soll der User entsprechend über den Client die Applikation im Browser öffnen und dort dessen Datensatz importieren und die Ergebnisse entsprechend lesen können. Das Trainieren der Modelle läuft im Backend auf der Server-Seite. Deshalb ist es notwendig hier den Server entsprechend für hohe Rechenleistungen auszulegen, damit auch große Datensätze verarbeitet werden können. Das Backend wird in Python implementiert und die Daten werden entsprechend in einem Data-Warehouse abgelegt. Das Frontend wird in React umgesetzt, um flexibel in der Implementierung der Web-App zu sein und auf spezifische User-Anforderungen reagieren zu können. Das Frontend benötigt die Daten vom Backend im .json Format, damit es diese in der Web-App verarbeiten kann. Hierzu wird FastAPI implementiert, da es Flexibilität im Datenaustausch bietet, sehr performant ist und automatisch eine Dokumentation generiert. Eine mobile App ist für Frunch Infinity 2.0 nicht erforderlich, da die Datensätze vom User nicht auf einem iPhone liegen. </p>

## Schnittstellen nach außen
<p style="text-align: justify;">Da Frunch Infinity 2.0 eine Enterprise Solution ist, soll das System im firmeneigenen Intranet aufgesetzt werden, damit die Kunden die Daten nicht nach außen vergeben müssen. Deshalb muss auch die Verwaltung und das Management der Server-Hardware von der IT-Abteilung des Kunden erfolgen. Somit sind folgende Schnittstellen nicht anwendbar:</p>
<p style="text-align: justify;">- Schnittstellen zu Internet-Webseiten und Web-Scraper</p>
<p style="text-align: justify;">- Schnittstellen zu Cloud-Services (Datawarehouse liegt beim Kunden)</p>
<p style="text-align: justify;">- Schnittstelle zu Softwareentwickler, da kein Transfer-Learning mit geteilten Daten angewendet wird</p>

<p style="text-align: justify;">Für das ablegen der Docker-Registry auf Dockerhub ist entsprechend die Schnittstelle vom Intranet nach außen erforderlich. Außerdem müssen entsprechende Downloads von Packages gewährleistet werden. Hierbei sollen die Packages nur mit Hashes installiert werden, um keine "gefälschten" Open-Source Packages zu installieren.</p>


# Datawarehouse 
<p style="text-align: justify;">Als Datawarehouse für Frunch Infinity ist ein Enterprise Data Warehouse erforderlich, damit die Daten zentralisiert gelagert werden. Für die Architektur der untersten Ebene im Datawarehouse können keine besonderen Anforderungen außer der Konsistenz der Daten abgeleitet werden. Die Zeit für das Schreiben und Lesen der Daten im Datawarehouse ist im Vergleich zur Trainingszeit der Modelle marginal und somit besteht keine Echtzeitanforderung. Es ist aber wichtig, dass die Daten konsistent sind, damit die Integrität der Daten über den gesamten Lebenszyklus gegeben ist. Deshalb wird als Architektur ein relationales DBS (MySQL) gewählt. Der Zugriff auf das Datawarehouse kann über SQLAlchemy (ORM) erfolgen und für die Verwaltung der importierten Datensätze wird DVC (Data Version Control) verwendet (bevor sie in das Datawarehouse abgelegt werden). </p>

# Systemarchitektur Modell

<p style="text-align: justify;">Die nachfolgende Grafik zeigt eine Übersicht der Architektur. Die gelb markierten Blöcke befinden sich im Frontend und die blau markierten Blöcke im Backend.</p>

![]({{ site.baseurl }}/diagrams/Systemarchitektur.svg "Systemarchitektur und Tools")

<p style="text-align: justify;">Der User soll dabei die Daten aus dem lokalen Speicher in einem .csv Format über die Web-App (Client) hochladen. Über die Web-App soll der User dann die Feature-Bezeichnungen definieren und entsprechend als numerisch oder kategorisch markieren, sowie die Zielvariable auswählen. Sobald die Funktion gestartet wird, werden die Daten entsprechend über eine Pipeline preprocessed und im Datawarehouse abgelegt (Server). Von dort aus werden die preprocessed Daten geladen, die Modelle trainiert und die Ergebnisse entsprechend gespeichert und ausgegeben.</p>

# CI/CD Pipeline

Die CI/CD Pipeline für Frunch Infinity 2.0 enthält folgende Stages:
- <p style="text-align: justify;">Test: Ausführen der unit-tests (run pytest)</p>
- <p style="text-align: justify;">Pages: Ausführen von pdoc, um Dokumentation der Klassen zu erstellen.</p>
- <p style="text-align: justify;">Build: Erstellen eines Docker-Images und speicher in einer Registry auf Gitlab. Die Build-Stage soll nur beim Tag (neuer Software Release) ausgeführt werden.</p>
- <p style="text-align: justify;">Deploy: Die Applikation soll deployed werden, wenn ein Release erfolgreich gebuilded wurde. </p>

<p style="text-align: justify;">Beispiel: Entwicklung des Features "import Data", mit dem der User eigene .csv-Files über die Web-App hochladen kann. </p>

1) <p style="text-align: justify;">pytest wird um eine Klasse "test_file_format" erweitert. Dabei wird ein assert error eingefügt, der die File-Extension "*.csv" überprüft und entsprechend einen Fehler "Please import only files in .csv file format" ausgibt.</p>
2) <p style="text-align: justify;">Implementierung in Web-App durchführen und importierte Daten als .json an Backend übergeben.</p>
3) <p style="text-align: justify;">Commit durchführen</p>
4) <p style="text-align: justify;">Pytest in CI wird durchgeführt. Wenn Test bestanden hat, dann weiter mit Schritt 5. </p>
5) <p style="text-align: justify;">Doc-String von Klassen "test_file_format" und "import_data" wird mit pdoc erstellt und als html abgelegt.</p>
6) <p style="text-align: justify;">Feature releasen in Gitlab. </p>
7) <p style="text-align: justify;">Build wird durchgeführt (siehe oben)</p>
8) <p style="text-align: justify;">App wird deployed.</p>

# Data-Science Architektur
<p style="text-align: justify;">Nachfolgendes Diagramm zeigt eine eigens entwickelte Data-Science Architektur für Frunch-Infinity 2.0 auf Basis des CRISP-DM Ansatzes. </p>

![]({{ site.baseurl }}/diagrams/DS_Architektur.png "Data Science Architektur")

<p style="text-align: justify;">Da Frunch-Infinity eine Auto-ML Lösung darstellt, liegt der Business Understanding (Domänenwissen) auf der User-Seite. Der User soll durch die Anwendung von Frunch-Infinity 2.0 einen Einblick in die Qualität der verwendeten Daten kriegen und somit das Verständnis der Daten verbessern. Damit das System flexibel ist muss die Data-Preparation und das Modelling ein Netzwerk darstellen, wodurch alle möglichen Szenarien durchberechnet werden. Der Evaluation-Teil vergleicht die Ergebnisse der Modelle und schaltet mit jeder Iteration durch alle Pipelines. Wenn alle Iterationen durchgelaufen sind, vergleicht der Evaluation-Teil die besten Ergebnisse der Iterationen mit einander und gibt das Modell mit dem besten Ergebnis aus. Am meisten Entwicklungsaufwand für Frunch-Infinity 2.0 wird der Teil Data Preprocessing sein, da die Pipeline unterschiedlichste Datensätze und Edge-Cases verarbeiten muss. Die Architektur soll die Möglichkeit bieten, dem User die Data Preparation sowie das beste Modell ausgeben, wodurch das Data Understanding durch die Anwendung von Frunch Infinity 2.0 erreicht wird.</p>


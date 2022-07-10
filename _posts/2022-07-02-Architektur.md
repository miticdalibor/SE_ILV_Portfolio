---
toc: true
layout: post
description: Dieser Post beschreibt angewandte Architekturen und Tools für Frunch Infinity 2.0
categories: [markdown]
title: 03 Architektur
---

# Systemarchitektur
<p style="text-align: justify;">Die Systemarchitektur für Frunch Infinity 2.0 stellt eine Client-Server-Architektur dar. Dabei soll der User entsprechend über den Client die Applikation im Browser öffnen und dort dessen Datensatz importieren und die Ergebnisse entsprechend lesen können. Das Trainieren der Modelle läuft im Backend auf der Server-Seite. Deshalb ist es notwendig hier den Server entsprechend für hohe Rechenleistungen auszulegen, damit auch große Datensätze verarbeitet werden können. Das Backend wird in Python implementiert und die Daten werden entsprechend in einem Data-Warehouse abgelegt. Das Frontend wird in React umgesetzt, um flexibel in der Implementierung der Web-App zu sein und auf spezifische User-Anforderungen reagieren zu können. Das Frontend benötigt die Daten vom Backend im .json Format, damit es diese in der Web-App verarbeiten kann. Hierzu wird FastAPI implementiert, da dieses sehr einfach implementiert werden kann und entsprechende Flexibilität im Datenaustausch bietet. Außerdem ist FastAPI sehr performant und generiert automatisch eine Dokumentation. Eine mobile App ist für Frunch Infinity 2.0 nicht erforderlich, da die Datensätze auf Rechnern abgespeichert werden. Schnittstellen zu anderen Webseiten und Web-Scraper sind hier auch nicht erforderlich. Die Daten werden hauptsächlich im Data-Warehouse, welches im Backend liegt, gespeichert. Da Frunch Infinity 2.0 eine Enterprise Solution ist, soll das System im firmeneigenen Intranet aufgesetzt werden, damit die Kunden die Daten nicht nach außen über Cloud-Solutions vergeben müssen. Außerdem ist für Frunch-Infinity kein vortrainiertes Modell oder Transfer-Learning von geteilten Daten erforderlich. Deshalb muss auch die Verwaltung und das Management der Server-Hardware vom Kunden erfolgen. Für das Datawarehouse können keine besonderen Anforderungen außer der Konsistenz der Daten abgeleitet werden. Die Zeit für das Schreiben und Lesen der Daten im Datawarehouse ist im Vergleich zur Trainingszeit der Modelle marginal. Es ist aber wichtig, dass die Daten konsistent sind, damit die Integrität der Daten über den gesamten Lebenszyklus gegeben ist. Deshalb wird als Datawarehouse eine SQL-Datenbank definiert. Der Zugriff auf das Datawarehouse kann über SQLAlchemy erfolgen und für die Verwaltung der Datensätze wird DVC (Data Version Control) verwendet. Die nachfolgende Grafik zeigt eine Übersicht des Datenflusses. Die gelb markierten Blöcke befinden sich im Frontend und die blau markierten Blöcke im Backend.</p>

![]({{ site.baseurl }}/diagrams/Systemarchitektur.svg "Systemarchitektur und Tools")

<p style="text-align: justify;">Der User soll dabei die Daten aus dem lokalen Speicher in einem .csv Format über die Web-App (Client) hochladen. Über die Web-App soll der User dann die Feature-Bezeichnungen definieren und entsprechend als numerisch oder kategorisch markieren, sowie die Zielvariable auswählen. Sobald die Funktion gestartet wird, werden die Daten entsprechend über eine Pipeline preprocessed und im Datawarehouse abgelegt (Server). Von dort aus werden die preprocessed Daten geladen, die Modelle trainiert und die Ergebnisse entsprechend gespeichert und ausgegeben.</p>

# CI/CD Pipeline

Die CI/CD Pipeline für Frunch Infinity 2.0 enthält folgende Stages:
- Test: 
- Build:
- Deploy:


# Diskussion
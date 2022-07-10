---
toc: true
layout: post
description: Dieser Post beschreibt angewandte Architektur für Frunch Infinity 2.0
categories: [markdown]
title: 04 Architektur
---

# Web Technologien
<p style="text-align: justify;">Die Web-Architektur für Frunch Infinity 2.0 stellt eine Client-Server dar. Dabei soll der User entsprechend über den Client die Applikation im Browser öffnen und dort dessen Datensatz importieren und die Ergebnisse entsprechend lesen können. Das Trainieren der Modelle läuft im Backend auf der Server-Seite. Deshalb ist es notwendig hier den Server entsprechend für hohe Rechenleistungen auszulegen, damti auch große Datensätze verarbeitet werden können. Das Backend wird in Python implementiert und die Daten werden entsprechend in einem Data-Warehouse abgelegt. Das Frontend wird in React umgesetzt, um flexibel in der Implementierung der Web-APP zu sein und auf spezifische User-Anforderungen reagieren zu können. Das Frontend benötigt die Daten vom Backend im .json Format, damit es diese in der Web-APP verarbeiten kann. Hierzu wird FastAPI implementiert, da dieses sehr einfach implementiert werden kann und entsprechende Flexibilität im Datenaustausch bietet. Außerdem ist FastAPI sehr performant. Eine APP ist für Frunch Infinity 2.0 nicht erforderlich, da die Datensätze statt auf Handys auf Rechnern abgespeichert werden. Schnittstellen zu anderen Webseiten und Web-Scraper sind hier auch nicht erforderlich, da das Ziel von Frunch Infinity 2.0 ist, einen schnellen Einblick in die Datenqualität und -verwendbarkeit ohne hohen Programmieraufwand zu geben. Die Daten werden hauptsächlich im Data-Warehouse, welches im Backend liegt gespeichert. Da Frunch Infinity 2.0 eine Enterprise Solution ist, soll das System im firmeneigenen Intranet aufgesetzt werden, damit die Kunden die Daten nicht nach außen über Cloud-Solutions vergeben müssen. Deshalb muss auch die Verwaltung und das Management der Server-Hardware vom Kunden erfolgen oder entsprechende Service Level Agreements mit Frunch Infinity aufgesetzt werden, die die Wartung des Systems übernehmen. 
Basierend auf den Anforderungen und dem geplanten Einsatz von Frunch Infinity 2.0 können daraus folgende Anforderungen für das Datawarehouse abgeleitet werden:
- 
</p>
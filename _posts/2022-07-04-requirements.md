---
toc: true
layout: post
description: Requirements von Frunch Infinity 2.0 nach den SOPHISTEN Regeln.
categories: [markdown]
title: 01 Requirements
---

# Requirements
Folgende Requirements wurden nach den SOPHISTEN Regeln für Frunch Infinity 2.0 definiert.

## Funktionale Requirements:
- Unter der Bedingung, dass der User alle Features des importierten Datensatzes über das UI kategorisiert hat und die Funktion "Free Lunch" gestartet hat, muss die Pipeline des Systems in der Lage sein, den Datensatz eigenständiig für das Modelltraining vorzubereiten.
- Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, Spalten mit nur fehlenden Daten abzufragen und aus dem Datensatz zu löschen. 
- Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, fehlende numerische Daten in einer Zeitserie durch einen Extremwert zu ersetzen.
- Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, fehlende kategorische Daten aus dem Datensatz zu entfernen.
- Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, entsprechend die numerischen Features zu skalieren zwischen 0 und 1 (MinMaxScaler).
- Wenn der vom User importierte Datensatz durch das Starten der "Frunch Infinity 2.0" Funktion vorverarbeitet wurde, sollen unterschiedliche konventionelle Modelle trainiert werden.

## User Interface

- Wenn der User die App startet, soll das System fähig sein, individuelle Datensätze zu importieren.
- Wenn der User einen beliebigen Datensatz über das UI importiert, muss die App "Frunch Infinity 2.0" die Möglichkeit bieten, die Feature-Bezeichnungen dem User anzuzeigen und der User soll entsprechend jedes Feature als numerisch oder kategorisch sowie die Zielvariable auswählen.
- Unter der Bedingung, dass der User alle Features des importierten Datensatzes über das UI kategorisiert hat und die Zielvariable kategorisch ist, soll die Applikation die Anzahl der unterschiedlichen Klassen in der Zielvariable sowie die Klassenbalance anzeigen.
- Wenn der User die Funktion "Frunch Infinity 2.0" gestartet hat, soll die Applikation fähig sein, dem User eine Auswahl von Metriken zum Vergleich der trainierten Modelle anbieten.
- Wenn das Training mit unterschiedlichen Modellen abgeschlossen ist, sollen die Ergebnisse mit den ausgewählten Metriken in einer Tabelle dem User über das UI angezeigt werden. 
- Wenn der User die Applikation startet, soll das System die Möglichkeit anbieten, den Log einzusehen und zu exportieren von der APP.

## UML Diagramm der zentralen Requirements
![]({{ site.baseurl }}/diagrams/UML_requirements.svg "UML Requirements")


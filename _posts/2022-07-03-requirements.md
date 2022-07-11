---
toc: true
layout: post
description: Requirements von Frunch Infinity 2.0 nach den SOPHISTEN Regeln.
categories: [markdown]
title: 01 Requirements
---

# Funktionale Requirements
- <p style="text-align: justify;">Unter der Bedingung, dass der User alle Features des importierten Datensatzes über das UI kategorisiert hat und die Funktion "Free Lunch" gestartet hat, muss die Pipeline des Systems in der Lage sein, den Datensatz eigenständiig für das Modelltraining vorzubereiten. </p>
- <p style="text-align: justify;">Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, Spalten mit nur fehlenden Daten abzufragen und aus dem Datensatz zu löschen. </p>
- <p style="text-align: justify;">Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, fehlende numerische Daten in einer Zeitserie durch einen Extremwert zu ersetzen. </p>
- <p style="text-align: justify;">Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, fehlende kategorische Daten aus dem Datensatz zu entfernen.</p>
- <p style="text-align: justify;">Wenn der importierte Datensatz der Pipeline übergeben wurde, soll die Pipeline fähig sein, entsprechend die numerischen Features zu skalieren zwischen 0 und 1 (MinMaxScaler).</p>
- <p style="text-align: justify;">Wenn der vom User importierte Datensatz durch das Starten der "Frunch Infinity 2.0" Funktion vorverarbeitet wurde, sollen unterschiedliche konventionelle Modelle trainiert werden.</p>

# User Interface
- <p style="text-align: justify;">Wenn der User die App startet, soll das System fähig sein, individuelle Datensätze zu importieren.</p>
- <p style="text-align: justify;">Wenn der User einen beliebigen Datensatz über das UI importiert, muss die App "Frunch Infinity 2.0" die Möglichkeit bieten, die Feature-Bezeichnungen dem User anzuzeigen und der User soll entsprechend jedes Feature als numerisch oder kategorisch sowie die Zielvariable auswählen.</p>
- <p style="text-align: justify;">Unter der Bedingung, dass der User alle Features des importierten Datensatzes über das UI kategorisiert hat und die Zielvariable kategorisch ist, soll die Applikation die Anzahl der unterschiedlichen Klassen in der Zielvariable sowie die Klassenbalance anzeigen.</p>
- <p style="text-align: justify;">Wenn der User die Funktion "Frunch Infinity 2.0" gestartet hat, soll die Applikation fähig sein, dem User eine Auswahl von Metriken zum Vergleich der trainierten Modelle anbieten.</p>
- <p style="text-align: justify;">Wenn das Training mit unterschiedlichen Modellen abgeschlossen ist, sollen die Ergebnisse mit den ausgewählten Metriken in einer Tabelle dem User über das UI angezeigt werden. </p>
- <p style="text-align: justify;">Wenn der User die Applikation startet, soll das System die Möglichkeit anbieten, den Log einzusehen und zu exportieren von der APP.</p>

# UML Diagramm der zentralen Requirements
![]({{ site.baseurl }}/diagrams/UML_requirements.svg "UML Requirements")

# Änderungen von Requirements
<p style="text-align: justify;">Da die gesamte Implementierung nach dem Agile-Prinzip  über das Kanban-Board von Gitlab erfolgt (siehe Beispiel in der nachfolgenden Abbildung), können entsprechende Änderungen von Requirements über dieses Board eingefangen und koordiniert werden. </p>

![]({{ site.baseurl }}/images/kanban_board.png "Kanban Board")

<p style="text-align: justify;">Dabei kann das neue Requirement oder geänderte Requirement als neues Issue im Produkt-Backlog aufgenommen werden. Um dieses Issue von den anderen zu unterscheiden, soll in der Beschreibung des Issues eine Change-Request ID hinzugefügt werden (z.B. CR-001). Im nächsten Sprint soll entsprechend der Impact bewertet werden. Ist der Impact zu groß, muss entsprechend mit dem Kunden Rücksprache gehalten werden. Wenn der Implementierungsplan aus dem geänderten Requirement aufegesetzt ist, dann werden daraus ableitend entsprechend neues Issues für das Projektteam angelegt. Jedes der Issues welche aus dem CR-001 erstellt wurden, werden entsprechend mit einem Flag markiert, um nach der fertigen Umsetzung erkennen zu können, wann der CR-001 abgeschlossen wurde und die Dokumentation der Requirements wird abschließend angepasst. </p>

Mögliche Veränderungen von Requirements wären beispielsweise:

- <p style="text-align: justify;"> Neue Edge-Cases in den zu importierenden Datensätzen, die die Pipeline verarbeiten muss. </p>
- <p style="text-align: justify;">Model-Explanation: Der User will das Training der Modelle überwachen und dies muss entsprechend über das UI ausgegeben oder in einem Log-File gespeichert werden. </p>
- <p style="text-align: justify;">Das beste Modell soll gespeichert werden, damit der User dies auf einem ähnlichen Datensatz anwendet. </p>


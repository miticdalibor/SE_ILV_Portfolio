---
toc: true
layout: post
description: Dieser Post beschreibt das angewandten Data Science Methodik-Konzept für Frunch Infinity 2.0
categories: [markdown]
title: 02 Data Science Methodik-Konzept
---

# CRISP-DM
<p style="text-align: justify;">Als Data-Science Konzept kann hier CRISP-DM angewendet werden (siehe Abbildung). Da Frunch-Infinity jedoch eine Auto-ML Lösung darstellt, ist der Business Understanding Teil nicht prioritär. Der Data Understanding Teil bleibt bei Frunch Infinity 2.0 auf der User Seite, da dieser über das UI entsprechend die Features sowie die Zielvariable im Datensatz definieren muss. Außerdem soll der User durch die Anwendung von Frunch-Infinity 2.0 einen Einblick in die Qualität der verwendeten Daten kriegen und somit das Verständnis der Daten gewährleisten. Am meisten Entwicklungsaufwand für Frunch-Infinity 2.0 wird der Teil "Data Preprocessing" sein, da die Pipeline unterschiedlichste Datensätze und Edge-Cases verarbeiten muss.</p>

![]({{ site.baseurl }}/images/CRISP-DM.png "CRISP-DM")

# Konzept Datenfluss
<p style="text-align: justify;">Die nachfolgende Grafik zeigt eine Übersicht des Datenflusses. Die gelb markierten Blöcke befinden sich im Frontend und die blau markierten Blöcke im Backend.</p>

![]({{ site.baseurl }}/diagrams/Prozess.svg "Datenfluss")

<p style="text-align: justify;">Der User soll dabei die Daten aus dem lokalen Speicher in einem .csv Format über die Web-App hochladen. Über die Web-App soll der User dann die Feature-Bezeichnungen definieren und entsprechend als numerisch oder kategorisch markieren sowie die Zielvariable. Sobald die Funktion gestartet wird, werden die Daten entsprechend über eine Pipeline preprocessed und im Datawarehouse abgelegt. Von dort aus werden die preprocessed Daten geladen, die Modelle trainiert und die Ergebnisse entsprechend gespeichert und ausgegeben.</p>



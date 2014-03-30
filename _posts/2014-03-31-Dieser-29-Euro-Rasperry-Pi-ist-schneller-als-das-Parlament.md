---
layout: post
title: Dieser 29 Euro Mini Rechner ist 48 schneller als die Parlamentsserver
categories:
- Politik
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
---

![Geralds Raspberry Pi](/assets/img/raspberry_690.jpg "Geralds Raspberry Pi")

Derzeit läuft die sogenannte Hypo Petition so erfolgreich, dass die Webserver des Parlaments dem "Ansturm" nicht standhalten und immer wieder ausfallen, in Timeouts laufen oder schlicht zu langsam sind. Das Parlament selbst hat [bekannt gegeben](http://www.parlament.gv.at/PAKT/AKT/SCHLTHEM/THEMA/J2014/2014_03_25_Hypo_Petition.shtml), dass die Server alle zwei bis vier Sekunden eine weitere Zustimmung zum zur Petition registrieren. Aus [diepresse.com ist zu entnehmen](http://diepresse.com/home/politik/innenpolitik/1583252/HypoPetition_ParlamentsServer-extrem-uberlastet), dass allein am 25.3.2014 20.113 Personen die Petition online unterzeichnet hätten. Politisch mögen das imposante Zahlen sein, aus technischer Sicht sind diese aber kaum beeindruckend.

Mich haben diese Zahlen stutzig gemacht, besonders als jemand, der die letzten drei Jahre mit der Skalierung von Datenbanken und Webservern verbracht hat. Denn das Problem Übertragung von Daten mittels Webformular in eine Datenbank, kann man eigentlich als gelöst betrachten. Deswegen habe ich einen Test auf einem [Raspberry Pi](http://www.raspberrypi.org/), das ist ein kleiner PC den man um [29,- Euro](http://www.reichelt.at/RASPBERRY-PI-B/3/index.html?&ACTION=3&LA=446&ARTICLE=133474&artnr=RASPBERRY+PI+B&SEARCH=raspberry) kaufen kann, erstellt. Bei dem Test wurde unter Linux (Raspian OS), ein Webserver (NGINX+https) und eine Datenbank (mySQL) aufgestzt. Als nächstes habe ich das Webformular des Parlaments nachgebaut und bei jeden Aufruf Dummy Daten ind die Datenbank eingetragen. Nachdem ich annehme, dass das Parlment etwas stärkere Rechner im Einsatz hat, müsste bei einem Last test mein Billigrechner eigentlich sehr schnell schlapp machen. Ich habe dazu das Tool Siege gestartet und die Seite 100000 mal mit 100 gleichzeitigen Verbindungen aufgerufen.

IMAGE

Das Ergebnis ist toll für den Raspberry Pi und erschütternd für die IT des Parlaments. Im Schnitt konnte ich die Seite 24 mal pro Sekunde aufrufen, also mindestens 48 mal so schnell wie die Server des Parlaments. Das heißt jetzt nicht, dass man die Parlamentsinfrastruktur auf einem Raspberry Pi betreiben könnte, aber es zeigt sehr schön wie lächerlich die Argumentation des Parlaments ist. Meiner Meinung nach sind die Server des Parlaments ein immer wichtigerer Teil unseres demokratischen Lebens und damit eine Sache der zivilen Landesverteidigung. Wenn man aber davon ausgeht, dass die Server des Parlaments schon bei einer durchschnittlichen Anwendung in die Knie geht, wie sieht das dann erst bei sogenannten Denial of Service Attacken aus, wo tausende Anfragen pro Sekunde eingehen? Vielleicht nimmt man auch an, das Server eines neutralen Landes niemals attackiert werden?

Die Homepage des Parlaments hat übrigens 2 Mio Euro gekostet und einmal abgesehen von einer UI die dem Look and Feel einer Behörde zu 100% gerecht wird, stellt sich hier die Frage, warum davon kein einziger Euro für automatische Skalierung ausgegeben wurde?

Als Bürger, dem die technische Infrastruktur unserer Volksvertretung ein wichitges Anliegen ist, habe ich als erstes beim Parlament angerufen, um zu erfahren, wie denn die Inrastruktur dort aussehe und was genau zur automatierten Skalierung dieser Infrastruktur unternommen werde. Nach mehreren Anrufen und Rückrufen wurde ich allerdings mit dem Hinweis abgespeist, dass das natürlich eine Sache der nationalen IT-Sicherheit sei und deswegen leider keine Auskünfte erteilt werden könnten. Wir lernen also daraus IT-Sicherheit besteht im Parlament vor allem daraus, die Server vor den Bürgern zu schützen.

Meiner Meinung nach lässt die Situation rund um die Petition nur zwei mögliche Rückschlüsse zu. Entweder die IT des Parlments ist extrem inkompetent oder es wurden die Zugriffe tatsächlich künstlich gedrosselt. Es kann nur gemutmaßt werden, wie viele Unterschriften mehr die Petitionen bereits haben könnten.


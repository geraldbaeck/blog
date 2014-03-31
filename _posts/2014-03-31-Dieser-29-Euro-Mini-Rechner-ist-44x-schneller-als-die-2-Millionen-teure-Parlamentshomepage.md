---
layout: post
title: Dieser 29 Euro Mini Rechner ist 44x schneller als die 2 Millionen teure Parlamentshomepage
categories:
- Politik
tags: []
status: publish
type: post
published: true
image: /assets/img/raspberry_690.jpg
description: Ein klitzekleiner Rechner schlägt die IT des österreichischen Parlaments und ist dabei 24 mal schneller.
meta:
  _edit_last: '1'
---

![Geralds Raspberry Pi]({{ page.image }} "Geralds Raspberry Pi")

ÖVP und SPÖ haben ein Problem namens Hypo. Aber anstatt das Problem selbst zu bekämpfen wird wiedermal in die Kiste mit den dreckigen Tricks gegriffen. Versuch eins war ein 6 monatiges Kommunikationsverbot über das Thema zu verhängen. Versuch zwei sollte verschiedene Petitionen für einen Untersuchungsausschuss einfach abwürgen.

Der gescheiterte Anschlag auf demokratische Grundrechte führte aber nur dazu, dass die Webserver des Parlaments dem "Ansturm" nicht standhalten und immer wieder ausfallen, in Timeouts laufen oder schlicht zu langsam sind. Das Parlament selbst hat [bekannt gegeben](http://www.parlament.gv.at/PAKT/AKT/SCHLTHEM/THEMA/J2014/2014_03_25_Hypo_Petition.shtml), dass die Server alle zwei bis vier Sekunden eine weitere Zustimmung zur Petition registrieren. Aus [diepresse.com ist zu entnehmen](http://diepresse.com/home/politik/innenpolitik/1583252/HypoPetition_ParlamentsServer-extrem-uberlastet) ist zu entnehmen, dass allein am 25.3.2014 20.113 Personen die Petition online unterzeichnet hätten. Politisch mögen das imposante Zahlen sein, aus technischer Sicht sind diese aber kaum beeindruckend.

![Service anavailable](/assets/img/Oesterreichisches-Parlament---Service-Unavailable--503-.png "Service unavailable")

Mich haben diese Zahlen stutzig gemacht, besonders als jemand, der die letzten drei Jahre mit der Skalierung von Datenbanken und Webservern verbracht hat. Denn das Problem "Übertragung von Daten mittels Webformular in eine Datenbank" kann man eigentlich als gelöst betrachten. Deswegen habe ich einen Test auf einem [Raspberry Pi](http://www.raspberrypi.org/) - das ist ein kleiner PC, den man um [29,- Euro](http://www.reichelt.at/RASPBERRY-PI-B/3/index.html?&ACTION=3&LA=446&ARTICLE=133474&artnr=RASPBERRY+PI+B&SEARCH=raspberry) kaufen kann - erstellt. Bei dem Test wurde unter Linux (Raspian OS) ein Webserver (NGINX+https+iptables) und eine Datenbank (mySQL) aufgesetzt. Als nächstes habe ich das Webformular des Parlaments nachgebaut und bei jeden Aufruf Dummy Daten in die Datenbank eingetragen. Nachdem ich annehme, dass das Parlment etwas stärkere Rechner im Einsatz hat, müsste bei einem Lasttest mein Billigrechner sehr schnell schlapp machen. Ich habe dazu das Tool Siege gestartet und die Seite 100000 mal mit 100 gleichzeitigen Verbindungen aufgerufen.

![Test Ergebnis](/assets/img/raspberry_result.png "Test Ergebnis")

Das Ergebnis ist toll für den Raspberry Pi und erschütternd für die IT des Parlaments. Im Schnitt konnte ich die Formulardaten 22 mal pro Sekunde übertragen, also mindestens 44 mal so schnell wie die Server des Parlaments. Mein Raspberry Pi könnte also die gesamten Unterschriften zur aktuellen Petition in zwei Stunden verarbeiten. Das heißt jetzt nicht, dass man die Parlamentsinfrastruktur auf einem Raspberry Pi betreiben könnte, aber es zeigt sehr schön wie lächerlich die Argumentation des Parlaments ist. Meiner Meinung nach sind die Server des Parlaments ein immer wichtigerer Teil unseres demokratischen Lebens und damit ein Objekt der zivilen Landesverteidigung. Wenn man aber davon ausgeht, dass die Server des Parlaments schon bei einer unterdurchschnittlichen Anwendung in die Knie gehen, wie sieht das dann erst bei sogenannten Denial of Service Attacken aus, wo tausende Anfragen pro Sekunde eingehen? Vielleicht sollte unsere Nationalratspräsidentin diesbezüglich mal in [Estland](https://en.wikipedia.org/wiki/2007_cyberattacks_on_Estonia) nachfragen.

Die Homepage des Parlaments hat übrigens [2 Mio Euro](http://www.unzensuriert.at/content/005858-Prammers-Homepage-Flop-kostet-zwei-Millionen-Euro) gekostet und einmal abgesehen von einer UI, die dem Look and Feel einer Behörde zu 100% gerecht wird, stellt sich hier die Frage, warum davon kein einziger Euro für automatische Skalierung ausgegeben wurde? Um 2 Millionen Euro könnte man übrigens 68.965 Rasperry PIs kaufen, die sollten dann auch reichen, um die Homepage des Parlaments zu betreiben.

Als Bürger, dem die technische Infrastruktur unserer Volksvertretung ein wichtiges Anliegen ist, habe ich als erstes beim Parlament angerufen, um zu erfahren, wie denn die Infrastruktur dort aussehe und was genau zur automatisierten Skalierung dieser Infrastruktur unternommen werde. Nach mehreren Anrufen und Rückrufen wurde ich allerdings mit dem Hinweis abgespeist, dass das natürlich eine Sache der nationalen IT-Sicherheit sei und deswegen leider keine Auskünfte erteilt werden könnten. Wir lernen also daraus: IT-Sicherheit besteht im Parlament vor allem daraus, die Server vor den Bürgern zu schützen.

Meiner Meinung nach lässt die Situation rund um die Petition nur zwei mögliche Rückschlüsse zu. Entweder die IT des Parlments ist extrem inkompetent oder es wurden die Zugriffe tatsächlich künstlich gedrosselt. Es kann nur gemutmaßt werden, wie viele Unterschriften mehr die Petitionen bereits haben könnten.


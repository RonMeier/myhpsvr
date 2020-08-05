# myhpsvr
kleiner Webserver für Raspberry

Installation: 
Datei myhpsvr auf Rasperry kopieren und die nötigen ausführbaren Rechte erteilen.

1.	myhpsvr nach /home/pi kopieren (mit winscp)
2.	sudo mv myhpsvr /usr/local/bin
3.	sudo chmod +x /usr/local/bin/myhpsvr
4.	Statren mit: 	sudo myhpsvr & 

myhpsvr kann auch in autostart eingetragen werden (siehe unten)
Aufruf der Webseite mit: RapyIP:Port 1190 (standard)/Befehl
z.B.   192.168.1.50:1190/help

Befehle:
cmd= mit cmd können alle internen Befehle des Raspberry ausgeführt werden (die Ausgabe der Console wird auf der Webseite angezeigt)
192.168.1.50:1190/cmd=ls -la /home/pi     listet das Verzeichnis von /home/pi auf
Weitere Beispiele:
192.168.1.50:1190/lesen=/var/log/syslog   listet das syslog auf
lesen=[file] z.b. lesen=/var/log/syslog, lesen=/var/log/kern.log, lesen=/var/log/messages
Eintrag in Log: cmd=logger -t myhpsvr -p daemon.info Server laeuft
UDP senden: udp=[port=9000] [ip=][Text=] (default-port ist 7777) 
Beispiel: udp=returnstring oder udp=port=5000 ip=192.168.1.1 returnstring
Datei-Download 1: dl=/var/log/syslog   	(mit Dialog-Box)
Datei-Download 2: rb=[/pfad/]file  z.B. IP:Port/rb=/home/pi/Doku.pdf  
Datei-Download 3: xl=[/pfad/]file
Logwerte in csv-Datei schreiben: logdatacsv=[file=/home/pi/dateiname.csv] 192.168.1.50:1190/logdatacsv=wert=12.2 oder logdatacsv=wert=Text in csv schreiben
csv-Datei anzeigen: 192.168.1.50:1190/lesen=/home/pi/dateiname.csv
Letzte Zeile von csv auslesen: 192.168.1.50:1190/letztezeile=/home/pi/dateiname.csv

In autostart eintragen:
sudo nano /etc/rc.local
Zeile vor exit 0 eintragen:     /usr/local/bin/myhpsvr

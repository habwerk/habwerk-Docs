---
id: solaredge
title: SolarEdge PV Wechselrichter
sidebar_label: SolarEdge
---


Hinzufügen über API:


API öffentlich (max 300 abfragen pro Tag!)

      Anleitung muss noch erstellt werden



API private (mit Modbuszähler unendlich abfragen pro Tag!)

      Anleitung muss noch erstellt werden


Hinzufügen über Modbus TCP (LAN only):

      1. Solaredge SE mit Display aktivieren von Modbus TCP
            CPU Version muss höher als 3.xxx sein! 
            Schalter auf Stellung aus
            Warten bis DC Spannung unter grenzwert fällt
            Abdeckung des WR Abmontieren
            Rechten knopf über Display für 10 sec drücken
            Passwort 12312312 eintippen und enter  (1 Knopf = ESC, 2Knopf =1, 3Knopf=2, 4Knopf=3)
            Navigieren mit 1 Knopf = ESC, 2 Knopf = OBEN, 3 Knopf = Unten, 4 Knopf = Enter

            im Menü Navigieren auf 
                  Kommunikation
                        LAN-Konfiguration
                              Modbus TCP -> Aktivieren und Port auf 502 einstellen
                                    Falls die Einstellmöglichkeit Modbus TCP trotz passender Firmware Version nicht vorhanden ist:
                                          über die SolarEdge SET APP den Chat support Kontaktieren!
                              ESC
                        ESC
                        
                  RS485-1 Konf <S> ->auswählen
                        Gerätetyp auf LGR (kein SE Logger) stellen
                        Geräte ID auf 1 stellen (bei mehereren Geräten freie ID wählen)

            
      
      1. Solaredge SE ohne Display aktivieren von Modbus TCP

            Ein/AUS/P Schalter 2s lang auf P halten und danach auf stellung Ein (WLAN Acces Point vom WR gestartet)
            Handy in den Wlan Einstellungen mit dem Solaredge Wlan verbinden
            SolarEdge Set App öffnen
            im Menü Navigieren
                  Anlagenkommunikation
                        Ethernet
                              Statische IP
                                    auswahl einer statischen IP
                              Speichern
                        RS485-1
                              Protokoll -> SunSpec wählen
                              Geräte ID: Geräte ID auf 1 stellen (bei mehereren Geräten freie ID wählen)       
                              Speichern
                        Modbus TCP Port
                              Modbus TCP -> Aktivieren 
                              Port: auf 502 einstellen
                              
      2. Hinzufügen des Modbus TCP (LAN only) Gerät im Openhab
            Als Admin Anmelden
                  Einstellungen
                        andere Add ons -> Suche (rechts unten)
                              Java -> Install JavaScript Scripting und Javascript Transformation
                              Modbus -> Install Modbus
                        Things
                              + (rechts unten)
                                    Modbus Binding
                                          Modbus TCP Slave
                                                IP Adresse (am Wechselrichter eingestellte IP)
                                                Port 502 (am Wechselrichter eingestellter Port)
                                                ID 1 (am Wechselrichter eingestellte ID)
                                                Discovery Enabled : true
                                                Create Thing
                                                Zurück

                              + (rechts unten)
                                    Modbus Binding
                                          Scan
                                                gefundenes gerät auswählen
                                                Save 
                                                Tap Channels
                                                (Channels entsprechend einrichten: Labels laut Datenbank Excel Liste) Anleitung muss noch erstellt werden
            

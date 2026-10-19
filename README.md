Alle bilder/diagrammer ligger i "Bilder" mappen


Del 1 - Fysisk nettverk
Logisk struktur:

Ruter - Switch - [SERVER01, CLIENT01]

SERVER01 - desktop PC
CLIENT01 - laptop

Krav: 
SERVER01, CLIENT01 - kan kommunisere med hverandre
SERVER01 - fast IP addresse
CLIENT01 - IP addresse fra DHCP
CLIENT01 - bruker minst en tjeneste fra SERVER01


Oppgaven er å lage en fysisk nettverk som består av to PC enheter (SERVER01, CLIENT01) som er koblet til ruter (R1) gjennom en switch (SW1)
Strukturen og IP configer er vist in en diagram "DEL1-fysisk nettverk"

SW1 porter: 1->R1 (ruter), 3->SERVER01, 4->CLIENT01
R1 porter: 1->SW1 (switch)

R1 (se i "R1 status LAN" og "R1 DHCP Settings"):
	IP adressen- 10.15.50.100
	Subnet- 255.255.255.0
	DHCP:
		IP range- 10.15.50.1-10.15.50.50
		Default Gateway 10.15.50.100

CLIENT01 (se i "DHCP clients list" og i "CLIENT01 ipconfig") - DYNAMISK IP config (verdiene er hentet fra ruter R1):
	IP adressen- DHCP 
	
SERVER01 (se i "SERVER01 ipconfig") - STATISK IP config (verdiene er satt manuaelt):
	IP adressen- 10.15.50.51
	Subnet- 255.255.255.0
	Gateway- 10.15.50.100

Resultater til ping tester ligger i "Bilder" mappen: "ping CLIENT01 til SERVER01", "ping SERVER01 til CLIENT01"
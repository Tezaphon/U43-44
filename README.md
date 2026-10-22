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


=======================
DEL 1 - FYSISK NETTVERK
=======================

Oppgaven er å lage en fysisk nettverk som består av to PC enheter (SERVER01, CLIENT01) som er koblet til ruter (R1) gjennom en switch (SW1).
Enhetene i nettverket skal: ha kommunikasjon med hverandre, det blir delt en mappe fra SERVER01.
Strukturen og IP configer er vist in en diagram "DEL1-fysisk nettverk"
Veiledning om nettverkets oppsett er i "DEL1 - fysisk nett - oppsettets veiledning.txt" filen

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

Mappen SERVER01 - C:\U4344  er delt til CLIENT01 og lenken er laget i CLIENT01 C:\u4344shared
(Det er noe problemet med å bare gå gjennom "Network\DC01 (SERVER01)". Man kan koble til mappen med å taste "\\10.15.50.51\u4344shared" men ikke med bruk av SERVER01 sin navn. DNS problemet? Sjekket services.msc, instillingene hos SERVE01. Funnet at noe ble slått av, med det hjulpet ikke)

==========================
DEL 2 - PACKET TRACER NETT
==========================

Nettverket skal minst ha to rutere, fire switcher, tre klientnett, eget servernett, minst én server, forbindelse mellom ruterne, DHCP, DNS og HTTP. 

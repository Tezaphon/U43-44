Alle bilder/diagrammer ligger i "Bilder" mappen

=======================
DEL 1 - FYSISK NETTVERK
=======================

Logisk struktur:

Ruter - Switch - [SERVER01, CLIENT01]

SERVER01 - desktop PC
CLIENT01 - laptop

Krav: 
SERVER01, CLIENT01 - kan kommunisere med hverandre
SERVER01 - fast IP addresse
CLIENT01 - IP addresse fra DHCP
CLIENT01 - bruker minst en tjeneste fra SERVER01

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
Den trenger login/passord. Det laget en "Guest" på Server01. Bruk: Login - guest; Passord - <ingenting>
==========================
DEL 2 - PACKET TRACER NETT
==========================

Nettverket skal minst ha to rutere, fire switcher, tre klientnett, eget servernett, minst én server, forbindelse mellom ruterne, DHCP, DNS og HTTP. 

Min nettverk inneholder: 12 PCer, 4 switcher, 3 servere, 2 rutere, 1 printer. Se i "Bilder" mappen -> "DEL2 Struktur"
	Ruter HOVEDKON-R2, DHCP = ON (se i "HOVEDKON-R2 DHCP" bildet):
		ADMINIST-SW -> PC5-7 har automatiske IPconfig ON.		Nettverk: 192.168.2.0/24 Gateway: 192.168.2.1 DNS: 192.168.1.2 (Pool ADM)
		SUPPORT-SW -> PC0-4 har automatiske IPconfig ON. 		Nettverk: 192.168.3.0/24 Gateway: 192.168.3.1 DNS: 192.168.1.2 (Pool SUP)
		SERVERE-SW -> Server0-2 har automatiske IPconfig ON.	Nettverk: 192.168.1.0/24 Gateway: 192.168.1.1 DNS: 192.168.1.2 (Pool SEV)
		
	Ruter SALGSAVD-R1, DHCP = ON (se i "SALGSAVD-R1 DHCP" bildet):
		SALGSAVD-SW -> PC8-11 har automatisk IPconfig ON. 		Nettverk: 192.168.255.0/24 Gateway: 192.168.255.1 DNS: 192.168.1.2 (Pool SAL)
		
Kobling mellom HOVEDKON-R2 og SALGSAVD-R1 skjer gjennom nettverket 192.168.50.0/24.

OSPF er configurert på begge ruterne. OSPF gjør det mulig for ruterne å vite hvor ligger nettverk bak andre ruterne.
Se i "Bilder" mappe for instillingene: "HOVEDKON-R2 IP og OSPF", "SALGSAVD-R1 IP og OSPF".

På "Server0" configurert DNS og HTTP. Den har statisk IP (i motsetning til resten av servere). IP addressen til "Server0" derfor brukes for DHCP configurering hos R1 og R2.
Man kan skrive "192.168.1.2" eller "localnett.fjordkraft.local" for å nå nettsiden som ligger på "Server0".

Tracert tester ligger i "Bilder/DEL2" mappen.

Det ble også opprettet en telnet kobling fra PC1 til R2. Se i "Bilder/DEL2" for "HOVEDKON-R2 vty telnet setup", "HOVEDKON-R2 vty telnet password".
Telnet ble videre brukt for å vise info fra R2 på PC1. Se i "PC1 telnet connection", "PC1 telnet R2 dhcp info"
Telnet også funker gjennom adre rutere (f.eks. info om R2 kan sees på PC10).
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
Strukturen og IP configer er vist in en diagram

SW1 porter: 1->R1 (ruter), 3->SERVER01, 4->CLIENT01
R1 porter: 1->SW1 (switch)
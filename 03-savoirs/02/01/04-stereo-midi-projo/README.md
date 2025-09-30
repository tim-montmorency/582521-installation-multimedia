# Installation Stéréo + midi + projecteur + micro

## Audio

```mermaid
graph LR
	M[Contrôleur MIDI - USB]
	A[Ordinateur]
	Mic[Microphone dynamique - XLR]
	B[Interface - Carte son USB]
	L[Haut-parleur amplifié - Gauche]
	R[Haut-parleur amplifié - Droite]

	M -->|USB MIDI| A
	Mic -->|XLR - preamp| B
	A -->|USB| B
	B -->|L - TRS or XLR| L
	B -->|R - TRS or XLR| R

	class A,L,R device;
	class B interface;
```

## Video

## Branchement d'un projecteur vidéo en studio

```mermaid
graph LR
	Power_A(Électricité)
    Internet

    subgraph Chariot
    	PC[Ordinateur]
        Internet --> PC
        PC -- HDMI --> Transmitter[Transmeteur Cat6] 
        Monitor[Moniteur de contrôle]
        PC -->|Display Port | Monitor
    end

	Power_A --> PC
	Power_A --> Monitor
    Power_A --ac/dc--> Transmitter

    subgraph Plafond
        Power_B(Électricité)
        Projector(Projecteur)
    	Power_B --> Projector
        Power_B --ac/dc--> Receiver
        Transmitter --Câble Ethernet--> Receiver[Recepteur Cat6]  -- HDMI --> Projector
        Internet --> Projector
    end


```

### Description

L’installation permet de piloter une projection vidéo interactive synchronisée au son : le contrôleur MIDI et le micro alimentent l’ordinateur (centre de production), l’ordinateur produit l’audio via l’interface vers deux enceintes amplifiées, et envoie la vidéo au projecteur via un émetteur/récepteur HDMI-over-Cat6. L’interactivité est réalisée dans le logiciel sur l’ordinateur qui reçoit MIDI et audio, et déclenche visuels et sons en temps réel.


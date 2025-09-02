<!-- %: BLOC1_SAVOIR1  -->
# Branchement d’une installation de projection architecturale
<!-- %; -->


<!-- start-replace-subnav -->
* [Epson PowerLite 535W (grand angle)](/03-savoirs/01/01/EPSON_PowerLite_535W/)
* [Epson PowerLite 700U (Ultra grand angle)](/03-savoirs/01/01/EPSON_PowerLite_700U/)
* [Epson PowerLite 990U (Téléphoto)](/03-savoirs/01/01/EPSON_PowerLite_990U/)
<!-- end-replace-subnav -->


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

> [!IMPORTANT]
> Brancher les cables vidéo HDMI et DISPLAY port sur la carte graphique de l'ordinateur, pas sur la carte mère.




## Branchement de deux projecteurs vidéo en studio

```mermaid
graph LR
	Power_A(Électricité)
    Internet_a(Internet)

    subgraph Chariot
        Internet_a --> PC
    	PC[Ordinateur]
        PC -- HDMI --> Transmitter_1[Transmeteur_1 Cat6] 
        PC -- HDMI --> Transmitter_2[Transmeteur_2 Cat6] 
        Monitor[Moniteur de contrôle]
        PC -->|Display Port | Monitor
    end

	Power_A --> PC
	Power_A --> Monitor
    Power_A --ac/dc--> Transmitter_1
    Power_A --ac/dc--> Transmitter_2

    subgraph Plafond
        Internet_b 
        Internet_b--> Projector_2
        Internet_b --> Projector_1
        Power_B(Électricité)
        Projector_1(Projecteur_1)
        Projector_1(Projecteur_2)
    	Power_B --> Projector_1
        Power_B --> Projector_2
        Power_B --ac/dc--> Receiver_1
        Power_B --ac/dc--> Receiver_2
        Transmitter_1 --Câble Ethernet--> Receiver_1[Recepteur_1 Cat6]  -- HDMI --> Projector_1
        Transmitter_2 --Câble Ethernet--> Receiver_2[Recepteur_2 Cat6]  -- HDMI --> Projector_2
    end


```


## Edge-Blending deux projecteur

* Théorie https://paulbourke.net/miscellaneous/edgeblend/
* Implémentation dans touchdesigner https://derivative.ca/UserGuide/Palette:projectorBlend






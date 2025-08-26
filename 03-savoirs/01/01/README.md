<!-- %: BLOC1_SAVOIR1  -->
# Branchement d’une installation de projection architecturale
<!-- %; -->


<!-- start-replace-subnav -->

<!-- end-replace-subnav -->


## Branchement d'un projecteur vidéo en studio

```mermaid
graph LR
	Power_A(Électricité)

    subgraph Chariot
    	PC[Ordinateur]
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
    end



```

> [!IMPORTANT]
> Brancher les cables vidéo HDMI et DISPLAY port sur la carte graphique de l'ordinateur, pas sur la carte mère.





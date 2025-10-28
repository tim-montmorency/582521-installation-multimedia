# Assignation Midi

## QLC midi mapping

### Spécifique à Windows 

#### Drivers Midi Virtuel

* Utiliser [loopmidi](https://www.tobias-erichsen.de/software/loopmidi.html)
* Démarrer loop midi 


### Plugdata 

* [Plugdata](https://plugdata.org/)

#### Configuration MIDI plugdata 


![alt text](image-5.png)

* réglage (menu hamburger)

![alt text](image-3.png)

* output Loopmidi (sur pc ) ou plugdata (sur mac)
![alt text](image-4.png)

#### Lien vers des patchs PlugData

[Patch Plugdata LFO](https://raw.githubusercontent.com/tim-montmorency/582513-conception/main/activites/lx_midi_map/plugdata-lfo-ctl.pd.zip) 

[Patch Plugdata Analyse](https://raw.githubusercontent.com/tim-montmorency/582513-conception/main/activites/lx_midi_map/analyse_audio.pd.zip) 

#### Lien relatifs

[Patch Plugdata lfo](plugdata-lfo-ctl.pd)

[Patch Plugdata Analyse](analyse_audio.pd)


### Configuration QLC 

#### Entrée midi

![alt text](image-2.png)

#### midi mapping 

![alt text](image-1.png)


### Reaper

Créer des courbe d'automation MIDI et les envoyer à QLC

#### Créer un élément MIDI 

![alt text](image-6.png)

![alt text](image-7.png)

#### Double cliquer l'élément midi pour éditer

![alt text](image-8.png)

#### Ajouter des piste de CC via le petit +

![alt text](image-9.png)

#### Dessiner des courbes expressives

![alt text](image-10.png)

#### Via le bouton *Route*

![alt text](image-11.png)

#### Sélectionner un *Midi Hardware output* sortie midi 

![alt text](image-12.png)
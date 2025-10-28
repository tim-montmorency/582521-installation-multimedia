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

[Patch Plugdata LFO](./plugdata-lfo-ctl.pd) 

[Patch Plugdata Analyse](./analyse_audio.pd) 


### Configuration QLC 

#### Entrée midi

![Entrée Midi dans QLC](image-2.png)

#### midi mapping 

![Assignation Midi dans QLC](image-1.png)


### Reaper

Créer des courbe d'automation MIDI et les envoyer à QLC

#### Créer un élément MIDI 

* ![Créer en élément midi dans REAPER](image-6.png)

* ![Résultat de la création d'un élément midi dans REAPER](image-7.png)

#### Double cliquer l'élément midi pour éditer

![Éditer l'élément midi](image-8.png)

#### Ajouter des piste de CC via le petit +

![Ajouter des CC dans le clip midi](image-9.png)

#### Dessiner des courbes expressives

![Dessiner des courbes expressives](image-10.png)

#### Via le bouton *Route*

![Appuyer sur Route](image-11.png)

#### Sélectionner un *Midi Hardware output* sortie midi 

![Sortir le midi dans la sortie adéquate](image-12.png)
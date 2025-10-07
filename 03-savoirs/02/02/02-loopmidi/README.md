# Loopmidi

## loopMIDI + REAPER → (ex.) TouchDesigner

*Acheminer du MIDI entre applications sous Windows, sans câble.*

## Qu’est-ce que loopMIDI ?

**loopMIDI** (Tobias Erichsen) crée des **ports MIDI virtuels** sur Windows. Chaque port apparaît simultanément comme **sortie** dans une appli A et **entrée** dans une appli B — pratique pour router du MIDI entre logiciels (DAW, VJ, etc.).

> Équivalent macOS : **IAC Driver** (Audio MIDI Setup, intégré dans le système).

---

## Scénario

* **REAPER** capte le MIDI (clavier/pad, contrôle, clip, script).
* REAPER **redirige** ce MIDI vers un port **loopMIDI**.
* **TouchDesigner** le **reçoit** via **MIDI In CHOP/DAT**.

---

## Mise en place 

### 1) Créer un port virtuel

1. Lancer **loopMIDI**.
2. Cliquer **+** → nommer le port (ex. `REAPER_to_TD`).

   * Un seul port suffit la plupart du temps; créez-en d’autres si vous voulez séparer « Notes », « Contrôleurs », « Horloge », etc.

### 2) Configurer REAPER (sortie)

1. **Options → Preferences → MIDI Devices**

   * Dans **MIDI outputs**, clic droit sur `REAPER_to_TD` → **Enable output**.
   * (Optionnel) **Send clock/SPP to this device** pour envoyer l’**horloge MIDI** (tempo) et la position.
2. Sur la **piste** qui doit émettre :

   * **Arm** (enregistrement) et **Input: MIDI** → choisir votre contrôleur (ou « All channels »).
   * **Monitoring ON** si vous voulez relayer en direct sans enregistrer.
   * **Route** (bouton *I/O*) → **MIDI Hardware Output** → sélectionner `REAPER_to_TD`.
   * (Optionnel) Filtrer les **canaux** (ex. « Send to channel 1 ») ou n’envoyer que **CC/Notes** via JSFX/MIDI filter si besoin.

### 3) Configurer TouchDesigner (entrée)

1. Ajouter un **MIDI In CHOP** (ou **MIDI In DAT** si vous voulez du texte d’événements).
2. **Device** → choisir `REAPER_to_TD`.
3. Vérifier que **Active** est coché et que le **MIDI Map** (notes/CC) correspond à votre usage.
4. Tester : jouer des notes/CC dans REAPER → courbes dans le CHOP.

---

## Variantes utiles

* **Distribution multi-apps** : créez plusieurs ports loopMIDI (`REAPER_to_TD`, `REAPER_to_Light`, etc.) et ajoutez plusieurs **MIDI Hardware Output** dans la fenêtre *I/O* de la piste.
* **Horloge & Start/Stop** : activez *Send clock/SPP* sur la **sortie** correspondante; côté TD, utilisez **MIDI In CHOP** (paramètre *Use Beat/Bar*).
* **Automations REAPER → CC** : utilisez **Parameter Modulation/MIDI Link** ou un **JSFX** pour transformer des enveloppes en CC.

---

## Bonnes pratiques & dépannage

* **Boucle MIDI (Larsen)** : si TD renvoie vers REAPER sur le même port, vous créez une boucle. Utilisez **des ports distincts** pour aller/retour (ex. `REAPER_to_TD` et `TD_to_REAPER`).
* **Ports occupés** : Windows ne partage pas toujours bien un port ouvert; fermez l’appli qui retient le port puis relancez.
* **Latence/Timing** : dans REAPER **Preferences → Audio → MIDI Devices**, essayez **Use MIDI clock for output** / **Allow feedback** avec parcimonie; gardez la **taille de buffer audio** raisonnable (128–256).
* **Canaux** : alignez les canaux (ex. canal 1) entre REAPER (*send channel*) et TD (*Channel Mask* du CHOP).
* **Nommer clairement** vos ports dans loopMIDI : plus simple à repérer dans les menus de chaque logiciel.

---

## Schéma mental

**Contrôleur/Clip** → *(REAPER piste)* → **MIDI Hardware Output: `REAPER_to_TD`** → *(loopMIDI)* → **TouchDesigner: MIDI In CHOP** → *opérations/trigger*

---

## Check-list 

* [ ] Port loopMIDI créé (`REAPER_to_TD`)
* [ ] REAPER : output **Enabled** (+ **Send clock** si requis)
* [ ] Piste REAPER : **I/O → MIDI Hardware Output** sur ce port
* [ ] TD : **MIDI In CHOP** sur le même port, actif
* [ ] Pas de boucle (ports aller/retour séparés)


## Ressources 

* https://derivative.ca/UserGuide/MIDI_Mapper_Dialog
* https://derivative.ca/UserGuide/MIDI
* https://matthewragan.com/2019/05/25/touchdesigner-virtual-midi-devices/

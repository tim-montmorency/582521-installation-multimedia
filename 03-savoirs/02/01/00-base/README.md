
# Diffusion sonore 

## Pilotes audio sous Windows

Les pilotes définissent comment le système d’exploitation communique avec la carte de son.

* **WDM (Windows Driver Model)**

  * *Forces* : support natif, compatibilité universelle.
  * *Faiblesses* : latence élevée, qualité limitée.

* **DirectSound**

  * *Forces* : large compatibilité avec les logiciels multimédia.
  * *Faiblesses* : ajoute de la latence.

* **WASAPI (Windows Audio Session API)**

  * *Forces* : accès en mode exclusif, réduction de la latence.
  * *Faiblesses* : dépend encore des couches Windows.

* **ASIO (Audio Stream Input/Output)**

  * *Forces* : faible latence, accès direct au matériel, précision.
  * *Faiblesses* : nécessite un pilote fourni par le fabricant.

👉 **Recommandation** : toujours prioriser **ASIO** lorsqu’il est disponible.

### Sélection driver audio ASIO

* Carte de son Behringer = ASIO UMC audio driver   


---

## Audio numérique et analogique

* **Audio analogique**

  * Signal continu, sensible aux interférences.
  * Avantage : simplicité.
  * Inconvénient : pertes sur longues distances.

* **Audio numérique**

  * Signal encodé en données binaires.
  * Avantage : résistance aux parasites, transmission longue distance.
  * Inconvénient : nécessite des conversions (latence possible).

---

## Entrées, sorties et monitoring direct

* **Entrées audio** : micros, instruments, sources externes.
* **Sorties audio** : haut-parleurs, casques, systèmes de diffusion.
* **Monitoring direct** : écoute en temps réel du signal entrant sans passer par l’ordinateur.

  * Avantage : latence quasi nulle.
  * Limite : signal brut, sans effets logiciels.

---

## Signal audio balancé vs non-balancé

* **Non-balancé (unbalanced)**

  * 2 conducteurs : signal + masse.
  * Exemple : RCA, jack TS.
  * Sensible aux interférences.

* **Balancé (balanced)**

  * 3 conducteurs : signal +, signal inversé, masse.
  * Exemple : XLR, jack TRS.
  * Avantage : élimine le bruit, idéal longues distances.

---

## La boîte de direct (DI) passive

Une **DI passive** permet :

* De convertir un signal haute impédance non-balancé en signal faible impédance balancé.
* D’envoyer un signal sur de longues distances sans perte.
* D’isoler électriquement pour éviter les boucles de masse.

👉 Outil incontournable pour relier instruments ou lecteurs multimédia à une console.

---

## Types de connecteurs audio

* **XLR** : standard professionnel (micro, console, haut-parleurs actifs).
* **Jack 6,35 mm (TRS / TS)** :

  * TRS : balancé ou stéréo.
  * TS : non-balancé, mono.
* **Jack 3,5 mm** : grand public (ordinateurs, téléphones).
* **RCA** : hi-fi, DJ, non-balancé.
* **AES/EBU (XLR 110 Ω)** : numérique professionnel.
* **S/PDIF (RCA ou Toslink)** : numérique grand public.
* **Speakon** : connexion haut-parleurs, forte puissance.

---

## Gestion de la latence

* **Sources** : conversion A/N et N/A, traitement logiciel, réseau.
* **Criticité** : >20 ms devient perceptible.
* **Solutions** :

  * Utiliser ASIO ou CoreAudio (macOS).
  * Monitoring direct.
  * Buffers faibles.
  * Synchronisation via horloge maître ou timecode.

---

## Gain staging et niveaux de signal

* Objectif : rapport signal/bruit optimal sans distorsion.
* Repères :

  * Micro ≈ –50 dBu à –20 dBu.
  * Ligne pro ≈ +4 dBu.
  * Ligne grand public ≈ –10 dBV.
* Règle : ajuster les gains en amont plutôt qu’en aval.

---

## Gestion de l’alimentation et boucles de masse

* **Boucles de masse** = ronflements et parasites.
* Solutions :

  * DI avec isolation.
  * Tout brancher sur la même phase électrique.
  * Conditionneurs d’alimentation / UPS.

---

## Sécurité et normes

* **Électrique** : câbles isolés, éviter les surcharges.
* **SPL** : respecter 85 dB max en exposition prolongée.
* **Scène** : câbles fixés, traction évitée, codage couleur.

---

## Acoustique de la salle

* **Réverbération** : influence la clarté.
* **Traitements** : panneaux absorbants, diffuseurs, bass traps.
* **Placement des haut-parleurs** : couverture homogène, éviter les interférences de phase.

---

## Protocoles et transmission audio en réseau

* **Dante** : multi-canaux via IP, faible latence.
* **AVB / TSN** : transmission déterministe (standard IEEE).
* **AES67** : compatibilité entre réseaux audio sur IP.

👉 Incontournables dans les installations multi-salles.

---

## Traitements du signal

* **EQ** : correction timbre, adaptation au lieu.
* **Compression / Limiteur** : homogénéité, protection contre les crêtes.
* **Réverbération / Delay** : effets, cohérence spatio-temporelle.
* **Filtres HP/LP** : élimination des graves ou aigus indésirables.

---

## Microphones et techniques de captation

* **Types** : dynamiques, condensateur, ruban.
* **Directivités** : cardioïde, omni, hypercardioïde.
* **Placement** : impact majeur sur la qualité et le risque de larsen.

---

## Haut-parleurs et systèmes de diffusion

* **Types** : large bande, deux voies, line-array, subwoofer.
* **Actifs** (amplification intégrée) vs **passifs** (ampli externe).
* **Couverture** : angle d’ouverture, SPL max, gestion des zones.

---

## Normes et formats audio

* **Fréquences d’échantillonnage** :

  * 44,1 kHz (CD),
  * 48 kHz (vidéo),
  * 96 kHz (HD).
* **Résolution** : 16 bits, 24 bits, 32 bits float.
* **Formats** :

  * Non compressés : WAV, AIFF.
  * Compressés sans perte : FLAC.
  * Compressés avec perte : MP3, AAC.



## Références

* https://ehomerecordingstudio.com/audio-cable-types/

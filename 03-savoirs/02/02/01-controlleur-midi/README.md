# Protocole MIDI 

Ce document résume le fonctionnement du protocole MIDI (Musical Instrument Digital Interface), les types de messages principaux, les limites pratiques (résolution, canaux, timing) et des conseils pour l'utiliser dans une installation ou un DAW (ex. REAPER).

## Principes de base

- MIDI n'est pas de l'audio : c'est une série de messages numériques qui décrivent des événements musicaux (Note On, Note Off, contrôleurs, changements de programme, etc.).
- Les messages MIDI sont envoyés sur un canal (1–16). Un seul câble/port MIDI peut transporter jusqu'à 16 canaux indépendants.
- Les messages classiques sont codés sur 8 bits par octet; beaucoup d'événements courants utilisent des valeurs sur 7 bits (0–127).

## Messages essentiels

- Note On / Note Off : indique le lancement et l'arrêt d'une note. Contient le numéro de note (0–127, 60 = Do central) et la vélocité (0–127). Certains appareils envoient Note On avec vélocité 0 pour signifier Note Off.
- Velocity : indique la force de l'attaque (0–127). Utilisé pour moduler le volume ou le timbre selon le synthé.
- Control Change (CC) : messages pour contrôler des paramètres (CC1 = Modulation Wheel, CC7 = Main Volume, CC64 = Sustain Pedal, etc.). Valeurs 0–127.
- Program Change : change le preset/instrument sur le canal (valeur 0–127).
- Pitch Bend : valeur qui contrôle la hauteur glissante. Habituellement codée sur 14 bits (two 7-bit bytes), offrant une résolution plus fine que CC.
- Aftertouch / Channel Pressure : pression après l'attaque sur la touche (channel or polyphonic aftertouch).
- System Exclusive (SysEx) : messages propriétaires/étendus, envoyés pour configurer un appareil ou transférer des données (patches, firmware). Leur taille est variable.

## Canaux et routage

- Il y a 16 canaux MIDI par port. Chaque canal peut être adressé indépendamment par les messages Note/CC/Program.
- Dans un DAW, on route généralement une entrée MIDI vers une piste instrument (VSTi) ; le VSTi écoute le canal MIDI configuré.

## Résolution et limites

- Valeurs 7 bits pour la plupart des CC et velocities : 128 pas (0–127). Cela peut être limitant pour des paramètres nécessitant une grande précision.
- Pitch Bend : souvent 14 bits (16384 pas), plus fin pour le contrôle de hauteur.
- Contrôleurs 14-bit : certains contrôle utilisent deux CCs (MSB/LSB) pour obtenir 14-bit sur certains paramètres.
- Latence : MIDI lui‑même est léger, mais la latence perçue dépend du driver audio, buffer de la carte son, traitement dans le DAW et load CPU. Pour jeu en temps réel, maintenir une faible latence audio est crucial.
- Bande passante : le flux MIDI standard (MIDI 1.0 over DIN/USB) a une capacité limitée ; envoi massif de messages (ex. gros SysEx ou grands nombres de messages polyphoniques) peut entraîner un retard.

## MIDI 1.0 vs MIDI 2.0 (brève)

- MIDI 1.0 : protocol historique, 31.25 kbaud pour le DIN, messages 7-bit classiques. Standard largement répandu.
- MIDI 2.0 : introduit des améliorations (résolution plus élevée, profilage d'appareils, capacités bidirectionnelles), mais l'adoption est progressive et dépend des appareils/logiciels.

## Messages système et timing

- Clock / Start / Stop : messages pour synchroniser tempo et transport entre appareils (MIDI Clock est tempo-synchronous, 24 ppqn).
- Timestamping : pour un timing précis, les implémentations USB/MIDI et DAW utilisent des timestamps, mais le jitter peut apparaître selon la pile USB et le système.

## Exemples utiles

- CC64 (Sustain) : 0 = off, 127 = on. Utile pour pédales de sustain.
- CC1 (Mod Wheel) : souvent mappé à vibrato ou filter cutoff.
- Pitch Bend : message composé de LSB puis MSB pour 14-bit (valeur centrée = 8192).

## Bonnes pratiques et conseils

- Utilisez les canaux MIDI pour séparer instruments (ex. piano sur canal 1, bass sur canal 2) si vous ne voulez pas multiplier les ports.
- Pour les contrôles nécessitant haute précision, privilégiez les messages 14-bit (LSB/MSB) ou les protocoles complémentaires (MIDI 2.0 quand disponibles).
- Évitez d'envoyer des CC non nécessaires en continu (envoi de mêmes valeurs) pour réduire la charge sur la chaîne MIDI/USB.
- Dans un DAW, mappez explicitement les contrôles et sauvegardez les presets ; utilisez ReaLearn pour mappings dynamiques dans REAPER.
- Attention aux SysEx : certains routeurs/logiciels peuvent bloquer ou passer lentement de gros SysEx.

## Limitations pratiques dans une installation

- Nombre de canaux : 16 par port (utilisez plusieurs ports/USB-MIDI interfaces si besoin).
- Résolution : 7-bit pour la plupart des CC; peut manquer de finesse pour paramètres lents/fins.
- Latence : dépends surtout de l'audio driver, pas du MIDI lui-même, mais les deux interagissent.
- Support matériel : certains contrôleurs n'exposent pas tous les messages (par ex. pas d'aftertouch polyphonique).

## Ressources et références

- Spécification MIDI officielle (MIDI Manufacturers Association)  
- Tutoriels REAPER pour routage MIDI et mapping  


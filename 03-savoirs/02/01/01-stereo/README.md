# Installation Stéréo simple

```mermaid
graph LR
	A[Ordinateur]
	B[Interface - Carte son USB]
	L[Haut-parleur amplifié - Gauche]
	R[Haut-parleur amplifié - Droite]

	A -->|USB| B
	B -->|L - TRS or XLR| L
	B -->|R - TRS or XLR| R

	class A,L,R device;
	class B interface;
```

Remarques:

- Le PC envoie l'audio numérique via USB vers l'interface audio (carte son).
- L'interface convertit le signal en sorties analogiques gauche/droite (L/R).
- Utilisez des câbles symétriques (XLR ou TRS) si vos équipements le permettent.
- Réglez le volume principal sur l'interface et les volumes individuels des haut-parleurs pour éviter les saturations.
## DMX

Le protocole DMX512 (Digital Multiplex) est une norme de communication série utilisée principalement dans le domaine de l'éclairage de scène, des spectacles en direct, des installations artistiques et autres environnements multimédias pour contrôler des appareils tels que les projecteurs, les variateurs de lumière, les machines à effets, et bien plus encore. Ce protocole permet aux techniciens en multimédia de centraliser le contrôle de l'éclairage et des effets, garantissant ainsi des performances visuelles synchronisées et dynamiques.
Fonctionnement du DMX

Le protocole DMX512 fonctionne en transmettant des données sous forme de signaux numériques sur une ligne de données unique à un ensemble d'appareils connectés en série. Voici les aspects essentiels de son fonctionnement :

### Signal DMX :
Le DMX utilise une communication série pour envoyer des valeurs numériques (allant de 0 à 255) sur des canaux spécifiques. Chaque valeur contrôle une fonction précise d'un appareil, comme l'intensité lumineuse ou la couleur.
Les données sont envoyées sous forme de trames, chaque trame contenant jusqu'à 512 valeurs (un "univers" DMX), correspondant chacune à un canal.

### Univers DMX :
Un univers DMX est une série de 512 canaux, chacun étant capable de contrôler un paramètre d’un appareil. Par exemple, un projecteur RGB peut nécessiter trois canaux : un pour le rouge, un pour le vert, et un pour le bleu.

Un contrôleur DMX envoie les données pour tous les canaux d’un univers en continu, environ 44 fois par seconde, garantissant une réponse rapide des appareils.

### Câblage et Connexion :

Les appareils DMX sont connectés en série à l'aide de câbles DMX, souvent des câbles XLR à 3 ou 5 broches. Le signal passe d'un appareil à l'autre, et il est crucial de terminer la chaîne avec un terminateur DMX (une résistance de 120 ohms) pour éviter les réflexions de signal qui peuvent causer des dysfonctionnements.

### Adressage des Appareils DMX

L'adressage DMX est une étape cruciale pour permettre à un contrôleur de gérer plusieurs appareils sur le même univers DMX. Voici comment cela fonctionne :

#### Adresse DMX :

Chaque appareil DMX doit être configuré avec une adresse de départ, qui est le premier canal que l'appareil écoutera dans l'univers DMX. Cette adresse est définie manuellement sur l'appareil, souvent à l'aide de commutateurs DIP, d'un écran LCD, ou via une interface de configuration numérique.

Par exemple, si un projecteur RGB est configuré avec l’adresse 001, il utilisera les canaux 1, 2, et 3 pour le contrôle du rouge, du vert et du bleu, respectivement. Un deuxième projecteur configuré avec l’adresse 004 utilisera les canaux 4, 5, et 6.

#### Planification de l'Adresse :

Il est important de planifier l'adresse de chaque appareil pour éviter les conflits. Deux appareils ne doivent pas partager la même adresse DMX, sauf si l'intention est qu'ils se comportent de manière identique.

Les adresses doivent être attribuées en tenant compte du nombre de canaux que chaque appareil utilise. Par exemple, si un appareil utilise 5 canaux, le prochain appareil doit être configuré pour commencer à un canal suivant qui n'est pas déjà utilisé (par exemple, si le premier appareil commence à l’adresse 001, le suivant pourrait commencer à 006).

#### Mode d’Appareil :

Certains appareils offrent des "modes" DMX qui déterminent combien de canaux ils utilisent. Par exemple, un projecteur LED pourrait avoir un mode 3 canaux (RGB uniquement) et un mode 7 canaux (incluant RGB, dimmer, strobe, etc.). Le mode choisi affecte l'adresse que l'appareil peut utiliser.

#### Multi-Univers :

Si un seul univers DMX (512 canaux) ne suffit pas pour le nombre d'appareils ou la complexité d'un spectacle, plusieurs univers peuvent être utilisés. Chaque univers est traité indépendamment, avec ses propres adresses de canaux.

### Usage du DMX en Multimédia

Le DMX512 est un outil incontournable pour les techniciens en multimédia, notamment dans les contextes suivants :

#### Éclairage de Scène :

Le DMX permet de contrôler l'intensité, la couleur, la direction et le mouvement des projecteurs, créant ainsi des ambiances lumineuses cohérentes et synchronisées avec d'autres éléments visuels et sonores.

#### Effets Spéciaux :

Il est utilisé pour gérer des dispositifs d'effets tels que les machines à brouillard, les stroboscopes, et les systèmes LED, permettant des effets dynamiques et interactifs.

#### Intégration Multimédia :

Dans les installations multimédia, le DMX peut être utilisé pour synchroniser l'éclairage avec des éléments sonores, visuels, ou même interactifs, en utilisant des systèmes intégrés où le DMX est contrôlé par un logiciel central.

#### Programmation et Automatisation :

Les séquences d'éclairage peuvent être préprogrammées et automatisées, permettant des transitions fluides et synchronisées avec la musique ou d'autres événements scénographiques.

### Conclusion

Le protocole DMX512 est essentiel pour tout technicien en multimédia travaillant avec l'éclairage et les effets visuels. La maîtrise de l'adressage DMX, de la configuration des appareils, et de la gestion des univers DMX permet une flexibilité et un contrôle total sur les installations d'éclairage complexes, garantissant ainsi des performances visuelles impressionnantes et parfaitement synchronisées.
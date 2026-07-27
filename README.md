# 3-axis-robot-simulator
## Simulateur de Bras Manipulateur 3 Axes (STM32)

Ce projet simule le comportement physique d'un bras robotisé à 3 axes en mesurant les commandes de position du contrôleur et en renvoyant des données télémétriques.

## Fonctionnalités principales
* **Capture PWM (Input Capture) :** Mesure la largeur d'impulsion envoyée par le contrôleur sur 3 canaux (`TIM1`, `TIM2`, `TIM15`) et la convertit en angles (0°–180°).
* **Communication SPI (Slave/Master) :** Transmet au contrôleur la position angulaire réelle des axes en réponse aux signaux d'interruption.
* **Simulation de Capteur de Force :** Génère un signal analogique via DAC1 pour simuler la force de préhension lors de la saisie d'un objet.
* **Injection d'Erreurs :** Utilise des broches d'E/S (`PA9`, `PA10`) pour simuler des défaillances matérielles ou du bruit de mesure.

## Connexions Matérielles
* **Commandes PWM :** Entrées capture de temporisateur (`TIM1_CH1`, `TIM2_CH1`, `TIM15_CH2`).
* **Bus SPI :** Transmission des octets de télémétrie (`SPI1`).
* **Retour Force :** Sortie DAC (`DAC1_OUT1`).

# 3-axis-robot-simulator
## STM32 PWM Angle Processor & Analog Control

Système d'acquisition et de traitement de signal sur STM32 (série L4). Le projet mesure la durée d'impulsion de 3 signaux PWM, les convertit en angles ($0^\circ \text{ à } 180^\circ$) transmis par SPI, et contrôle une sortie analogique DAC.

## Fonctionnalités

* **Mesure PWM (Input Capture)** : Capture de la largeur d'impulsion sur 3 timers (`TIM1`, `TIM2`, `TIM15`) avec calibration de $-5\%$.
* **Conversion en Angle** : Cartographie des valeurs $1000\text{–}2000\text{ µs}$ vers une plage de $0\text{ à }180^\circ$.
* **Bus SPI** : Envoi d'un paquet de 3 octets (`tx_bytes`) sur demande (`PA11`).
* **Offset Dynamique** : Ajout d'un décalage aléatoire ($10\text{ à }20^\circ$) activable via `PA10`.
* **Sortie DAC** : Génération d'une tension analogique (0 ou 1024/4095) pilotée par l'entrée `PA6` et sécurisée par interruptions (`PA0`, `PA9`).

## Configuration des Broches

| Peripheral / Broche | Mode | Rôle |
| :--- | :--- | :--- |
| **TIM1_CH1 / TIM2_CH1 / TIM15_CH2** | Input Capture | Entrées signaux PWM |
| **SPI1** | Master (8-bit) | Transmission des angles calculés |
| **DAC1_OUT1** | 12-bit Right | Sortie analogique |
| **PA0 / PA9 / PA10 / PA11** | EXTI | Contrôle des modes et d'envoi SPI |
| **PA6** | Digital Input | Déclencheur principal du DAC |

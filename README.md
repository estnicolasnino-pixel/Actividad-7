# Actividad-7
# Gemelo Digital Híbrido para Robótica de Enjambre (ACO + ESP32)

Este proyecto implementa una arquitectura **HIL (Hardware-in-the-Loop)** y un **Gemelo Digital Híbrido** para simular un sistema de robótica de enjambre basado en el algoritmo de **Optimización por Colonia de Hormigas (ACO)**.

El sistema combina el procesamiento embebido en hardware real (**ESP32**) con la simulación física 3D en tiempo real (**PyBullet**).

---

##  Arquitectura del Sistema

* **Capa Física (Robot 1):** Un microcontrolador ESP32 procesa las probabilidades del algoritmo ACO para determinar rutas dentro de un mapa de 6 nodos y transmite su telemetría mediante paquetes UDP.
* **Capa Virtual (Robots 2 y 3):** Un script en Python ejecuta hilos independientes (*multithreading*) para simular los movimientos de los robots virtuales 2 y 3.
* **Gemelo Digital (PyBullet):** Renderiza en tiempo real el comportamiento coordinado del enjambre (1 nodo físico + 2 nodos virtuales).

---

##  Protocolo de Comunicación UDP

* **Puerto UDP:** `8888`
* **Direccionamiento:** Wi-Fi local (red 2.4 GHz)
* **Estructura del Mensaje:** `POS,<ROBOT_ID>,<NODO_ID>` (Ejemplo: `POS,1,3`)

---

## Requisitos e Instalación

### Hardware
* ESP32 Dev Module
* Cable USB para programación y alimentación
* Red Wi-Fi local (2.4 GHz / Punto de acceso móvil)

### Software
* Python 3.8+
* Arduino IDE (con soporte para ESP32 instalado)

### Instalación de dependencias de Python
```bash
pip install -r requirements.txt

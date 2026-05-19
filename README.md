# Diseño y Optimización de Vehículo RC para Motor DC RS550 y Batería LiPo 4S

Este repositorio contiene el modelado de primer orden, la estructura jerárquica y los cálculos de ingeniería para el diseño y optimización de un vehículo a control remoto (RC). El proyecto integra el diseño mecánico con simulaciones avanzadas, enfocándose en maximizar la relación potencia/masa, garantizando la integridad estructural y la estabilidad dinámica bajo condiciones críticas de operación.

## Integrantes y Contacto
* **Integrante 1:** [Catalina Grandón] (cagrandon2022@udec.cl)
* **Integrante 2:** [Joaquín Otárola] (jootarola2023@udec.cl)
* **Integrante 3:** José Miguel Venegas Alvarado (jvenegas2023@udec.cl)

*Departamento de Ingeniería Mecánica, Facultad de Ingeniería, Universidad de Concepción.*

---

## Misión General del Sistema (Nivel 0)
La función principal del sistema es **transportar la masa propia del vehículo RC** (chasis, electrónica, motor y batería) **más una carga útil determinada (TBD kg), de manera terrestre por una pista, optimizando la eficiencia estructural y la relación potencia/masa**. El objetivo de este modelo es validar que el diseño soporte las exigencias mecánicas del torque del motor y las cargas de inercia, alcanzando la velocidad máxima operacional de diseño de $7.6 \text{ m/s}$.

---

## Descomposición Jerárquica (Heurística $7 \pm 2$)
Para gestionar la complejidad del vehículo de manera eficiente, el sistema se descompone en **5 subsistemas principales**:

1. **Subsistema Estructural y Chasis:** Chasis principal optimizado e impreso en filamento PLA, encargado de soportar estructuralmente el torque del motor y alojar los componentes.
2. **Subsistema de Propulsión (Planta Motriz):** Motor DC RS550 y el sistema de transmisión mecánica (piñón/corona) para transferir el torque a las ruedas.
3. **Subsistema de Gestión de Energía:** Batería LiPo 4S y el circuito regulador de voltaje (RV).
4. **Subsistema de Control y Electrónica:** Microcontrolador Arduino, puente H / receptor de potencia (RP), módulo Bluetooth (Bt) y la placa de circuito impreso (PCB) personalizada.
5. **Subsistema de Dirección y Actuación:** Servoactuador y varillajes mecánicos para el control del eje de dirección delantero.

---

## Modelo Input-Process-Output (IPO)
El flujo matemático y lógico de los cálculos de primer orden sigue la estructura IPO detallada a continuación:

* **Inputs (Entradas):**
    * Masa total del vehículo ($m$) [$\text{kg}$]
    * Torque máximo del motor DC RS550 ($\tau \approx 300 \text{ mNm}$) [$\text{Nm}$]
    * Voltaje nominal de la batería LiPo 4S ($V$) [$\text{V}$]
    * Radio efectivo de la rueda motriz ($r$) [$\text{m}$]
    * Relación de transmisión del reductor ($N$)
* **Process (Procesamiento):**
    1. Cálculo de la fuerza de tracción en las ruedas: $F_{trac} = \frac{\tau \cdot N}{r}$
    2. Aplicación de dinámica vehicular (DCL) y Segunda Ley de Newton para calcular la aceleración máxima: $a = \frac{F_{trac}}{m}$
    3. Evaluación de las condiciones estáticas y curvas de rendimiento del motor para determinar el consumo de corriente ($I$).
* **Outputs (Salidas):**
    * Fuerza de tracción disponible ($F_{trac}$) [$\text{N}$]
    * Aceleración inicial estimada ($a$) [$\text{m/s}^2$]
    * Consumo de corriente del sistema ($I$) [$\text{A}$]

---

## Estructura del Repositorio
* `/images`: Carpeta que contiene los diagramas y esquemas del proyecto.
* `Diseño_Vehiculo_RC.ipynb`: Jupyter Notebook principal con el código ejecutable y ecuaciones detalladas.
* `diagrama_logica.vsdx`: Archivo fuente editable en Microsoft Visio con el diagrama de flujo del modelo.

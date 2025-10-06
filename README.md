# Lab1_Robotica_David_Ariadna
Proyecto de laboratorio de Robótica Industrial (UNAL 2025-II): programación de un robot ABB IRB140 en RAPID con control de entradas/salidas digitales, simulación en RobotStudio y ejecución en robot real.

# 🤖 Laboratorio No. 01 – Robótica Industrial 2025-II
**Autores:** Ariadna Contreras Nossa y David Santiago Nagles Barajas 
**Universidad Nacional de Colombia**  
**Asignatura:** Robótica Industrial  

---

## 🎥 Video del proceso
![Vista previa del laboratorio](Media/preview_lab.gif)

🎥 [Ver video completo en YouTube](https://youtu.be/Cc66QLF5waU)

---

## 🧱 Descripción del Proyecto
Este laboratorio consiste en la programación y control de un **robot ABB IRB 140** para simular la **decoración de una torta**, donde el robot escribe los nombres *Ariadna* y *David* junto con un logo de búho.  
El proyecto incluye:
- Programación en **RAPID** para tres trayectorias (`Path_10`, `Path_20`, `Path_30`).
- Control de una **banda transportadora** con lógica I/O.
- Implementación de **dos botones físicos** (inicio y mantenimiento).
- Señales digitales de **luces indicadoras** y rutina de retorno a home con verificación articular a 0°.
- Simulación en **RobotStudio** y ejecución en robot real.

---

## ⚙️ Lógica y señales digitales

El sistema se controla Mediante dos entradas digitales y dos salidas:

- **DI_01:** Botón de inicio de rutina de decoración  
- **DI_02:** Botón de rutina de mantenimiento  
- **DO_01:** Luz indicadora de proceso activo  
- **DO_02:** Luz indicadora de mantenimiento  

Además, se controló la **banda transportadora** a través de la salida `Conveyor_INV`.

La lógica completa fue programada en RAPID usando condicionales `IF–ELSEIF–ENDIF` y bucles `WHILE TRUE`.

<img src="Media/Botones Lógica.png" alt="Diagrama de botones y lógica I/O" width="60%">
<img src="Media/Rutina Banda.png" alt="Rutina de control de la banda transportadora" width="60%">

**Resumen del funcionamiento:**
1. Al presionar **Botón 1**, se activa la banda, se realiza la decoración (Paths 10, 20, 30) y se vuelve a home.  
2. Al presionar **Botón 2**, el robot entra en modo mantenimiento, encendiendo la luz DO_02.  
3. Al finalizar, ambas rutinas devuelven el robot a la posición `GoHome` con verificación de 0° en cada eje.

---

## 🧩 Código principal (`Module3_final.mod`)
El código incluye:
- Ciclo principal con condicionales `IF ... ELSEIF ... ENDIF`
- Función `GoHome()` que valida si todas las articulaciones están a 0°.
- Rutinas `Path_10`, `Path_20`, `Path_30` para escribir los nombres y logo.
- Señales digitales y control de banda.

📄 Ver el archivo completo aquí: [simulation/Module3_final.mod](simulation/Module3_final.mod)

---

## 🧰 Herramienta
La herramienta fue diseñada para sostener un marcador fijo al flange del robot.  
Se calibró su **Tool Center Point (TCP)** y se importó el modelo CAD a RobotStudio para comparar el tooldata real y virtual.

La herramienta se compone de tres partes principales modeladas en CAD y exportadas en formato `.SAT` para su importación a RobotStudio:

📷  
<img src="Media/Brazo con Tool Simulado.jpg" alt="Brazo con herramienta simulada" width="60%">


- [📎 Herramienta_Soporte_Marcador](Docs/Herramienta_Soporte_Marcador.pdf) — estructura principal que sostiene el marcador.
- [📎 Herramienta_Tapa_Marcador](Docs/Herramienta_Tapa_Marcador.pdf) — tapa de sujeción del plumón.
- [📎 Herramienta_Despiece](Docs/Herramienta_Despiece.pdf) — vista general con medidas y ensamble.
- [📎 Herramienta_Soporte.sat](Docs/Herramienta_Soporte.sat) — modelo 3D exportado para RobotStudio.
📷  
<img src="Media/Tool_real.jpg" alt="Herramienta del robot" width="50%">

### 🎯 Calibración del TCP

Se realizaron **dos procedimientos de calibración física** y una **verificación en RobotStudio**:

1. **Calibración TCP (1):**  
   Se utilizó el método de **tres puntos** con el marcador fijo, permitiendo estimar el TCP manualmente.

   <img src="Media/Calibración TCP.jpg" alt="Primera calibración TCP" width="50%">

2. **Calibración TCP (2):**  
   Se aplicó el método de **cuatro puntos**, logrando una mayor precisión al determinar el offset de la herramienta.

   <img src="Media/Calibración 2 TCP.jpg" alt="Segunda calibración TCP" width="50%">

3. **Calibración en RobotStudio:**  
   El resultado fue validado en el entorno virtual. El error promedio entre el TCP real y simulado fue **inferior a 1.5 mm**, lo cual se considera aceptable para aplicaciones de trazado y escritura.

   <img src="Media/Calibración TCP en RobotStudio.png" alt="Calibración en RobotStudio" width="55%">

**Comparación técnica:**  
- El método de **1 punto** tiende a tener errores por orientación del marcador.  
- El método de **2 o 4 puntos** reduce significativamente los errores de posición angular.  
- La validación en RobotStudio confirmó que la orientación y el desplazamiento de la herramienta estaban correctamente parametrizados.

---

## 🗺️ Plano de planta
Incluye:
- Posición del robot ABB IRB140  
- Banda transportadora  
- Caja de cartón paja (2×18×35 cm)  
- Zona de trabajo delimitada con el workobject.

📄 Ver imagen:

<img src="Docs/Plano_de_planta.png" alt="Plano_de_planta" width="50%">

---

## 🔁 Diagrama de flujo
Representa la secuencia de eventos del programa principal, manejo de entradas, salidas y rutinas de mantenimiento.  
📄 Ver: 

![Docs/Diagrama_de_flujo.png](Docs/Diagrama_de_flujo.png)

---

## 🧩 Archivos incluidos
| Archivo | Descripción |
|----------|-------------|
| `Module3_final.mod` | Código RAPID completo |
| `Plano_de_planta.png` | Distribución de elementos |
| `Diagrama_de_flujo.png` | Flujo de acciones del robot |
| `video_lab.mp4` | Video de simulación + robot real |
| `Laboratorio_No_1.pdf` | Enunciado del laboratorio |
| `resultado_fisico.jpg` | Decorado final sobre la caja |

---

## 🏁 Conclusiones

- Se logró integrar exitosamente el control de **entradas y salidas digitales** en un robot ABB IRB 140.  
- El sistema replica un entorno industrial básico de decoración automatizada con control de banda y luces.  
- La calibración del TCP fue validada en RobotStudio, garantizando precisión en los trazos.  
- La simulación coincidió con la implementación física, mostrando coherencia entre el entorno virtual y real.

<img src="Media/Resultado Final.jpg" alt="Caja decorada con nombres y logo" width="65%">


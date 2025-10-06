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

## ⚙️ Funcionamiento general
- **Botón 1:** Inicia la rutina de decoración (enciende banda, escribe nombres y logo, regresa a home).  
- **Botón 2:** Activa la rutina de mantenimiento (posiciona el robot para cambio de herramienta).  
- **Luces DO_01 / DO_02:** Indican en qué modo está el robot.  
- **Conveyor_INV:** Activa la banda transportadora de salida.

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

📷  
<img src="Media/Tool_real.jpg" alt="Herramienta del robot" width="50%">

## 🧰 Diseño de la herramienta

La herramienta se compone de tres partes principales modeladas en CAD y exportadas en formato `.SAT` para su importación a RobotStudio:

- [📎 Herramienta_Soporte_Marcador](docs/Herramienta_Soporte_Marcador.pdf) — estructura principal que sostiene el marcador.
- [📎 Herramienta_Tapa_Marcador](docs/Herramienta_Tapa_Marcador.pdf) — tapa de sujeción del plumón.
- [📎 Herramienta_Despiece](docs/Herramienta_Despiece.pdf) — vista general con medidas y ensamble.
- [📎 Herramienta_Soporte.sat](docs/Herramienta_Soporte.sat) — modelo 3D exportado para RobotStudio.

<img src="media/herramienta_real.jpg" alt="Herramienta del robot" width="50%">

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
- Se logró la integración de hardware y software con señales I/O.  
- La rutina de decoración cumple las condiciones del laboratorio (home, luces, mantenimiento).  
- La simulación fue validada con RobotStudio y ejecutada con éxito en el robot ABB real.

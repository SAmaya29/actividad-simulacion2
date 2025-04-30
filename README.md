# 📌 Actividad de Seguimiento - Simulación 2

## 👥 Integrantes
| Nombre | Correo | Usuario GitHub |
|--------|--------|---------------|
| Sebastian Amaya Perez | sebastian.amaya1@udea.edu.co | SAmaya29 |
| Emmanuel Bustamante Valbuena | Emmanuel.bustamante@udea.edu.co | Emma-Ok |

---

# 🏗️ Homework (Simulation)
Este programa, (`mlfq.py`) permite ver cómo se comporta el programador MLFQ.

---

## 🔎 Preguntas y Análisis

### 🚀 Pregunta 1
Ejecute:
```bash
./mlfq.py -n 2 -q 10 20 -l 0,50,0:5,30,0 -s 2
```
📌 **Ejecutar algunos problemas con 2 trabajos y 2 colas; sin E/S.**

🧑‍💻 Resumen de la configuración:
- Trabajo 0:
  - startTime: 0 (El trabajo llega en el tiempo 0)
  - runTime: 50 (El trabajo necesita 50 unidades de CPU para completarse)
  - ioFreq: 0 (Este trabajo no realiza operaciones de I/O)

- Trabajo 1:
  - startTime: 5 (Este trabajo llega al sistema en el tiempo 5)
  - runTime: 30 (Este trabajo necesita 30 unidades de CPU para completarse)
  - ioFreq: 0 (Este trabajo no realiza operaciones de I/O)

🧠 ¿Qué significa cada parámetro?

- -n 2: Estás trabajando con dos trabajos.
- -q 10 20: Se tienen dos colas con tamaños de cuántum 10 y 20, respectivamente.
- -l 0,50,0:5,30,0: Estás indicando que tienes dos trabajos:
  - Trabajo 0: Comienza en el tiempo 0, necesita 50 unidades de CPU y no hace I/O.
  - Trabajo 1: Comienza en el tiempo 5, necesita 30 unidades de CPU y tampoco hace I/O.
- -s 2: Este parámetro te va a permitir obtener el seguimiento de ejecución (trace).

🔎 ¿Qué podemos esperar del trace?
1. Trabajo 0 (0,50,0): Inicia en el tiempo 0, y debe ejecutarse hasta completar 50 unidades de CPU. Como no hace I/O, no se interrumpe y el tiempo de ejecución solo dependerá del cuántum de CPU.
2. Trabajo 1 (5,30,0): Inicia en el tiempo 5, pero el trabajo 0 puede estar ejecutándose primero. Como no hace I/O, también ejecutará su CPU sin interrupciones.

Aqui podemos ver la ejecucion del script:
```
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 2
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  50 - ioFreq   0
  Job  1: startTime   5 - runTime  30 - ioFreq   0

Compute the execution trace for the given workloads.
If you would like, also compute the response and turnaround
times for each of the jobs.

Use the -c flag to get the exact results when you are finished.

```

Ahora que tenemos esta información básica, el próximo paso es ejecutar el trace, que nos mostrará cómo se distribuye el tiempo de ejecución entre los trabajos.

```
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 2
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  50 - ioFreq   0
  Job  1: startTime   5 - runTime  30 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 49 (of 50) ]
[ time 1 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 48 (of 50) ]
[ time 2 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 47 (of 50) ]
[ time 3 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 46 (of 50) ]
[ time 4 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 45 (of 50) ]
[ time 5 ] JOB BEGINS by JOB 1
[ time 5 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 44 (of 50) ]
[ time 6 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 43 (of 50) ]
[ time 7 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 42 (of 50) ]
[ time 8 ] Run JOB 0 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 41 (of 50) ]
[ time 9 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 40 (of 50) ]
[ time 10 ] Run JOB 1 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 29 (of 30) ]
[ time 11 ] Run JOB 1 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 28 (of 30) ]
[ time 12 ] Run JOB 1 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 27 (of 30) ]
[ time 13 ] Run JOB 1 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 26 (of 30) ]
[ time 14 ] Run JOB 1 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 25 (of 30) ]
[ time 15 ] Run JOB 1 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 24 (of 30) ]
[ time 16 ] Run JOB 1 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 23 (of 30) ]
[ time 17 ] Run JOB 1 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 22 (of 30) ]
[ time 18 ] Run JOB 1 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 21 (of 30) ]
[ time 19 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 20 (of 30) ]
[ time 20 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 39 (of 50) ]
[ time 21 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 38 (of 50) ]
[ time 22 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 37 (of 50) ]
[ time 23 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 36 (of 50) ]
[ time 24 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 35 (of 50) ]
[ time 25 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 34 (of 50) ]
[ time 26 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 33 (of 50) ]
[ time 27 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 32 (of 50) ]
[ time 28 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 31 (of 50) ]
[ time 29 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 30 (of 50) ]
[ time 30 ] Run JOB 1 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 19 (of 30) ]
[ time 31 ] Run JOB 1 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 18 (of 30) ]
[ time 32 ] Run JOB 1 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 17 (of 30) ]
[ time 33 ] Run JOB 1 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 16 (of 30) ]
[ time 34 ] Run JOB 1 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 15 (of 30) ]
[ time 35 ] Run JOB 1 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 14 (of 30) ]
[ time 36 ] Run JOB 1 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 13 (of 30) ]
[ time 37 ] Run JOB 1 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 12 (of 30) ]
[ time 38 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 11 (of 30) ]
[ time 39 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 10 (of 30) ]
[ time 40 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 29 (of 50) ]
[ time 41 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 28 (of 50) ]
[ time 42 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 27 (of 50) ]
[ time 43 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 26 (of 50) ]
[ time 44 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 25 (of 50) ]
[ time 45 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 24 (of 50) ]
[ time 46 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 23 (of 50) ]
[ time 47 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 22 (of 50) ]
[ time 48 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 21 (of 50) ]
[ time 49 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 20 (of 50) ]
[ time 50 ] Run JOB 1 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 9 (of 30) ]
[ time 51 ] Run JOB 1 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 8 (of 30) ]
[ time 52 ] Run JOB 1 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 7 (of 30) ]
[ time 53 ] Run JOB 1 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 6 (of 30) ]
[ time 54 ] Run JOB 1 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 5 (of 30) ]
[ time 55 ] Run JOB 1 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 4 (of 30) ]
[ time 56 ] Run JOB 1 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 3 (of 30) ]
[ time 57 ] Run JOB 1 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 2 (of 30) ]
[ time 58 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 1 (of 30) ]
[ time 59 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 0 (of 30) ]
[ time 60 ] FINISHED JOB 1
[ time 60 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 19 (of 50) ]
[ time 61 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 18 (of 50) ]
[ time 62 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 17 (of 50) ]
[ time 63 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 16 (of 50) ]
[ time 64 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 15 (of 50) ]
[ time 65 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 14 (of 50) ]
[ time 66 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 13 (of 50) ]
[ time 67 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 12 (of 50) ]
[ time 68 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 11 (of 50) ]
[ time 69 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 10 (of 50) ]
[ time 70 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 9 (of 50) ]
[ time 71 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 8 (of 50) ]
[ time 72 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 7 (of 50) ]
[ time 73 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 6 (of 50) ]
[ time 74 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 5 (of 50) ]
[ time 75 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 4 (of 50) ]
[ time 76 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 3 (of 50) ]
[ time 77 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 2 (of 50) ]
[ time 78 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 1 (of 50) ]
[ time 79 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 0 (of 50) ]
[ time 80 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround  80
  Job  1: startTime   5 - response   5 - turnaround  55

  Avg  1: startTime n/a - response 2.50 - turnaround 67.50
```

📅 Resumen del Execution Trace:
- Trabajo 0 comienza en el tiempo 0 y utiliza el cuántum de la cola de prioridad 1 durante 10 unidades de tiempo antes de pasar a la cola de prioridad 0. Continúa ejecutándose hasta que termina en el tiempo 80.
- Trabajo 1 comienza en el tiempo 5 y sigue una ejecución similar, pero termina antes, en el tiempo 60.

🕒 Tiempos de Respuesta y Turnaround:
1. Trabajo 0:
  - Tiempo de Respuesta: 0 (Este trabajo comienza de inmediato).
  - Tiempo de Turnaround: 80 (Tiempo total desde que llega hasta que termina).
2. Trabajo 1:
  - Tiempo de Respuesta: 5 (Este trabajo comienza en el tiempo 5).
  - Tiempo de Turnaround: 55 (Tiempo total desde que llega hasta que termina).

📊 Promedios:
- Promedio de Respuesta: 2.50
- Promedio de Turnaround: 67.50

🔑 Conclusiones:
- El trabajo 0 empezó inmediatamente, mientras que el trabajo 1 tuvo que esperar hasta que el primero usara su tiempo de CPU en la primera cola.
- El turnaround del trabajo 1 es más corto que el del trabajo 0, lo cual es esperable, ya que terminó antes (en el tiempo 60).

### 🚀 Pregunta 2
Ejecute:
```bash
./mlfq.py -n 3 -q 5,10,15 -l 0,20,5 -l 2,30,7 -l 5,10,3 -s 2
```
📌 **¿Cómo ejecutarías el programador para reproducir ejemplos del capítulo?**

Para este proposito usaremos la siguiente configuracion: 

🛠️ **Configuración:**
- Número de trabajos: -n 2 → Hay 2 trabajos en la simulación (Job 0 y Job 1).
- Número de colas: -q 10 20 → Se están utilizando 2 colas, la primera con una longitud de cuántum de 10 y la segunda con 20.
- Alotamiento de tiempo por cola:
   - Cola 0: allotment de 1 (trabajo tendrá un allotment de 1 unidad de tiempo en esta cola).
   - Cola 1: allotment de 1 también.
- Longitud de cuántum por cola:
   - Cola 0: cuántum de 10 unidades de tiempo.
   - Cola 1: cuántum de 10 unidades de tiempo.
- Boost de prioridad: -b 0 → No hay boost de prioridad, lo que significa que las colas no cambian de prioridad durante la ejecución.
- Tiempo de I/O: -l 0,50,0:5,30,0 → Definición de trabajos:
   - Job 0: entra en el sistema en el tiempo 0, necesita 50 unidades de CPU, sin realizar I/O.
   - Job 1: entra en el sistema en el tiempo 5, necesita 30 unidades de CPU, sin realizar I/O.
- Otros parámetros:
   - StayAfterIO: False (los trabajos no permanecen después de realizar I/O).
   - IO Bump: False (no se aumenta la prioridad cuando un trabajo realiza una operación I/O).

Ahora veamos la ejecucion del script

```
Here is the list of inputs:
OPTIONS jobs 1
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  15
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  15
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  15
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   5 - runTime  10 - ioFreq   3

Compute the execution trace for the given workloads.
If you would like, also compute the response and turnaround
times for each of the jobs.
```
En la ejecución del script tenemos los siguientes parámetros y resultados:

⚙️ **Parámetros de Entrada:**
- Trabajo 0:
   - startTime (tiempo de inicio): 5
   - runTime (tiempo de ejecución): 10
   - ioFreq (frecuencia de I/O): 3 (el trabajo realiza operaciones de entrada/salida cada 3 unidades de tiempo)
- Quantum para las colas:
   - Cola 0: 5 unidades
   - Cola 1: 10 unidades
   - Cola 2: 15 unidades

🔎 **Análisis de los Resultados:**

Los resultados del script te darán la traza de ejecución de tu trabajo dentro del sistema de planificación MLFQ (Multiple Level Feedback Queue). De acuerdo con las simulaciones de MLFQ, los trabajos se ejecutan en diferentes colas con distintos tiempos de quantum.
Al ejecutar un trabajo, el planificador MLFQ evalúa si el trabajo necesita cambiar de cola según su comportamiento (por ejemplo, si se bloquea por I/O o termina su tiempo de quantum). Aquí están los pasos claves para el análisis:

1. Inicio del Trabajo:
   - El trabajo 0 comienza en el sistema en el tiempo t = 5. Se ejecutará durante su primer quantum de tiempo (5 unidades) en la primera 
    cola, si es necesario, pasa a la siguiente cola con un quantum mayor.

2. Ejecución de Trabajo:
   - Cada vez que el trabajo agota su quantum de tiempo en una cola (por ejemplo, 5 unidades en la cola 0), pasa a la siguiente cola con 
    un quantum mayor.

3. Interrupciones por I/O:

   - Dado que ioFreq es 3, el trabajo realiza una operación de I/O después de cada 3 unidades de tiempo. Esto afectará la ejecución porque 
    cada vez que se realiza un I/O, el trabajo puede ser bloqueado por el tiempo necesario para completar esa operación (5 unidades de        tiempo según ioTime).

4. Tiempos de Respuesta y Turnaround:
   - Tiempo de respuesta: El tiempo que tarda el trabajo en comenzar a ejecutarse después de que entra en el sistema. Esto depende de 
    cuántas veces el trabajo debe esperar en las colas antes de poder ejecutarse.
   - Tiempo de turnaround: El tiempo total que tarda un trabajo desde que entra al sistema hasta que termina, incluyendo tanto los 
    períodos de espera como de ejecución.

  
### 🚀 Pregunta 3
Ejecute:
```bash
./mlfq.py -n 1 -q 5 -l 0,20,5 -l 2,30,7 -l 5,10,3 -s 0
```
📌 **¿Cómo configurar MLFQ como un Round-Robin?**
  
Configurar un planificador MLFQ como si fuera un Round-Robin (RR) implica ajustar los parámetros de MLFQ para que todos los trabajos se comporten como si estuvieran en una sola cola con rotación fija.

✅ **¿Qué es Round-Robin?**
Round-Robin (RR) es un algoritmo de planificación donde:
- Todos los trabajos están en una sola cola.
- Cada trabajo recibe un cuanto de tiempo fijo (quantum).
- Si un trabajo no termina en su cuanto, vuelve al final de la cola.

🛠️ **Cómo configurar MLFQ como Round-Robin**
Para lograrlo, se debe:
- Usar una sola cola (-n 1).
- Asignar un quantum (por ejemplo -q 5).
- No usar degradación ni boosting.

Ahora veamos la ejecucion del script
```
Here is the list of inputs:
OPTIONS jobs 1
OPTIONS queues 1
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is   5
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   5 - runTime  10 - ioFreq   3

Compute the execution trace for the given workloads.
If you would like, also compute the response and turnaround
times for each of the jobs.

```
| Parámetro                   | Valor          | ¿Es lo esperado para RR? | ✅ |
|----------------------------|----------------|---------------------------|----|
| `OPTIONS queues`           | `1`            | Sí, solo una cola         | ✅ |
| `OPTIONS quantum length`   | `5`            | Quantum fijo de 5         | ✅ |
| `OPTIONS allotments`       | `1`            | No importa aquí, es solo una cola | ✅ |
| `OPTIONS boost`            | `0`            | Sin boosting              | ✅ |
| `OPTIONS stayAfterIO`      | `False`        | No afecta Round-Robin     | ✅ |
| `OPTIONS iobump`           | `False`        | No afecta Round-Robin     | ✅ |

🧠 **¿Qué significa esto en la práctica?**
   - El trabajo 0 empezará en el tiempo 5.
   - Recibirá 5 unidades de CPU.
   - Si no termina, se reencola (como en RR).
   - Emitirá I/O cada 3 unidades → se irá a I/O, luego vuelve.

Ahora veamos a detalle el comportamiento del sistema:

```
Here is the list of inputs:
OPTIONS jobs 1
OPTIONS queues 1
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is   5
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   5 - runTime  10 - ioFreq   3


Execution Trace:

[ time 0 ] IDLE
[ time 1 ] IDLE
[ time 2 ] IDLE
[ time 3 ] IDLE
[ time 4 ] IDLE
[ time 5 ] JOB BEGINS by JOB 0
[ time 5 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 9 (of 10) ]
[ time 6 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 8 (of 10) ]
[ time 7 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 7 (of 10) ]
[ time 8 ] IO_START by JOB 0
IO DONE
[ time 8 ] IDLE
[ time 9 ] IDLE
[ time 10 ] IDLE
[ time 11 ] IDLE
[ time 12 ] IDLE
[ time 13 ] IO_DONE by JOB 0
[ time 13 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 6 (of 10) ]
[ time 14 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 5 (of 10) ]
[ time 15 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 4 (of 10) ]
[ time 16 ] IO_START by JOB 0
IO DONE
[ time 16 ] IDLE
[ time 17 ] IDLE
[ time 18 ] IDLE
[ time 19 ] IDLE
[ time 20 ] IDLE
[ time 21 ] IO_DONE by JOB 0
[ time 21 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 3 (of 10) ]
[ time 22 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 2 (of 10) ]
[ time 23 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 1 (of 10) ]
[ time 24 ] IO_START by JOB 0
IO DONE
[ time 24 ] IDLE
[ time 25 ] IDLE
[ time 26 ] IDLE
[ time 27 ] IDLE
[ time 28 ] IDLE
[ time 29 ] IO_DONE by JOB 0
[ time 29 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 0 (of 10) ]
[ time 30 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   5 - response   0 - turnaround  25

  Avg  0: startTime n/a - response 0.00 - turnaround 25.00

```
🔍 **Análisis de ejecución paso a paso**
- Primera ráfaga:
   - t = 5 → 8: Job 0 usa 3 ticks, luego hace I/O (ioFreq = 3)
   - t = 8 → 13: sistema está IDLE hasta que vuelve el I/O
- Segunda ráfaga:
   - t = 13 → 14: ejecuta 2 ticks restantes de su quantum (le quedaban 2), luego recibe nuevo quantum completo
   - t = 15 → 16: ejecuta 1 tick, luego hace I/O otra vez
- Tercera ráfaga:
   - t = 21 → 23: ejecuta 3 ticks, luego I/O
- Cuarta ráfaga:
   - t = 29: ejecuta el último tick restante

📌 **Confirmación de comportamiento Round-Robin**

- 🔁 Cada vez que vuelve de I/O, retoma desde el mismo nivel de prioridad (único nivel), sin penalización.
- ⏱️ Se le asigna un quantum fijo de 5 ticks.
- 💡 Solo hay un proceso, así que no hay competencia, pero el tiempo de espera después de I/O y el reparto de CPU en bloques de ticks demuestra que se comporta como un Round-Robin clásico.

📊 **Métricas**

- Response time: 0 (empezó a ejecutarse justo al llegar)
- Turnaround time: 30 - 5 = 25

✅ **Conclusión**
Sí, la configuración de MLFQ con una sola cola y un quantum fijo emula perfectamente el comportamiento de un planificador Round-Robin.


### 🚀 Pregunta 4
Ejecute:
```bash
./mlfq.py -n 3 -q 5 -q 10 -q 15 -S -l 0,100,1 -l 0,100,0 -c
```
📌 **Reglas 4a y 4b**
  
🔍 **¿Qué hacen las reglas 4a y 4b?**
Activadas con -S, estas reglas hacen que:
  - 4a (stayAfterIO): Un proceso que hace I/O permanece en el mismo nivel de prioridad al volver, en lugar de ser degradado.
  - 4b (iobump): Además, ese proceso sube de nivel tras completar una operación de I/O.
🔁 Esto permite que un proceso que hace I/O frecuente mantenga o incluso mejore su prioridad, dominando sobre los procesos CPU-bound.

🎯 Objetivo del ejercicio
Queremos crear una carga de trabajo donde:
  - Un proceso CPU-bound (usa mucho CPU, sin I/O) baje de prioridad con el tiempo.
  - Un proceso I/O-bound (frecuente I/O) se mantenga en niveles altos gracias a las reglas 4a y 4b.
  - El proceso I/O-bound "juegue" con el planificador para obtener ~99% de la CPU en un intervalo.

✅ Propuesta de configuración
Parámetros del planificador:
- -n 3                      → 3 niveles de cola
- -q 5 -q 10 -q 15          → Quantums: más alto = más largo, más bajo = más prioritario
- -S                        → Activamos reglas 4a y 4b
Procesos:
1.  Job 0 (I/O-bound):
  - -l 0,100,1 → llega en t=0, necesita 100 ticks, hace I/O cada 1 tick
    Esto lo hace subir y mantenerse en la cola más alta (prioridad 0)
2.  Job 1 (CPU-bound):
  - -l 0,100,0 → llega en t=0, necesita 100 ticks, no hace I/O
    Se irá degradando hasta la cola más baja

🔍 **¿Qué deberíamos observar?**
- Job 0 dominará el uso de la CPU, ya que realiza I/O constantemente y se beneficia de las reglas activadas.
- Job 1 se verá desplazado porque se degrada rápidamente sin I/O que lo “salve”.

Ahora observemos a detalle la ejecucion del script
```
Here is the list of inputs:
OPTIONS jobs 1
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  15
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  15
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  15
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO True
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime 100 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 14 ALLOT 1 TIME 99 (of 100) ]
[ time 1 ] Run JOB 0 at PRIORITY 2 [ TICKS 13 ALLOT 1 TIME 98 (of 100) ]
[ time 2 ] Run JOB 0 at PRIORITY 2 [ TICKS 12 ALLOT 1 TIME 97 (of 100) ]
[ time 3 ] Run JOB 0 at PRIORITY 2 [ TICKS 11 ALLOT 1 TIME 96 (of 100) ]
[ time 4 ] Run JOB 0 at PRIORITY 2 [ TICKS 10 ALLOT 1 TIME 95 (of 100) ]
[ time 5 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 94 (of 100) ]
[ time 6 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 93 (of 100) ]
[ time 7 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 92 (of 100) ]
[ time 8 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 91 (of 100) ]
[ time 9 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 90 (of 100) ]
[ time 10 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 89 (of 100) ]
[ time 11 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 88 (of 100) ]
[ time 12 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 87 (of 100) ]
[ time 13 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 86 (of 100) ]
[ time 14 ] Run JOB 0 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 85 (of 100) ]
[ time 15 ] Run JOB 0 at PRIORITY 1 [ TICKS 14 ALLOT 1 TIME 84 (of 100) ]
[ time 16 ] Run JOB 0 at PRIORITY 1 [ TICKS 13 ALLOT 1 TIME 83 (of 100) ]
[ time 17 ] Run JOB 0 at PRIORITY 1 [ TICKS 12 ALLOT 1 TIME 82 (of 100) ]
[ time 18 ] Run JOB 0 at PRIORITY 1 [ TICKS 11 ALLOT 1 TIME 81 (of 100) ]
[ time 19 ] Run JOB 0 at PRIORITY 1 [ TICKS 10 ALLOT 1 TIME 80 (of 100) ]
[ time 20 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 79 (of 100) ]
[ time 21 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 78 (of 100) ]
[ time 22 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 77 (of 100) ]
[ time 23 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 76 (of 100) ]
[ time 24 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 75 (of 100) ]
[ time 25 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 74 (of 100) ]
[ time 26 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 73 (of 100) ]
[ time 27 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 72 (of 100) ]
[ time 28 ] Run JOB 0 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 71 (of 100) ]
[ time 29 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 70 (of 100) ]
[ time 30 ] Run JOB 0 at PRIORITY 0 [ TICKS 14 ALLOT 1 TIME 69 (of 100) ]
[ time 31 ] Run JOB 0 at PRIORITY 0 [ TICKS 13 ALLOT 1 TIME 68 (of 100) ]
[ time 32 ] Run JOB 0 at PRIORITY 0 [ TICKS 12 ALLOT 1 TIME 67 (of 100) ]
[ time 33 ] Run JOB 0 at PRIORITY 0 [ TICKS 11 ALLOT 1 TIME 66 (of 100) ]
[ time 34 ] Run JOB 0 at PRIORITY 0 [ TICKS 10 ALLOT 1 TIME 65 (of 100) ]
[ time 35 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 64 (of 100) ]
[ time 36 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 63 (of 100) ]
[ time 37 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 62 (of 100) ]
[ time 38 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 61 (of 100) ]
[ time 39 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 60 (of 100) ]
[ time 40 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 59 (of 100) ]
[ time 41 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 58 (of 100) ]
[ time 42 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 57 (of 100) ]
[ time 43 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 56 (of 100) ]
[ time 44 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 55 (of 100) ]
[ time 45 ] Run JOB 0 at PRIORITY 0 [ TICKS 14 ALLOT 1 TIME 54 (of 100) ]
[ time 46 ] Run JOB 0 at PRIORITY 0 [ TICKS 13 ALLOT 1 TIME 53 (of 100) ]
[ time 47 ] Run JOB 0 at PRIORITY 0 [ TICKS 12 ALLOT 1 TIME 52 (of 100) ]
[ time 48 ] Run JOB 0 at PRIORITY 0 [ TICKS 11 ALLOT 1 TIME 51 (of 100) ]
[ time 49 ] Run JOB 0 at PRIORITY 0 [ TICKS 10 ALLOT 1 TIME 50 (of 100) ]
[ time 50 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 49 (of 100) ]
[ time 51 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 48 (of 100) ]
[ time 52 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 47 (of 100) ]
[ time 53 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 46 (of 100) ]
[ time 54 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 45 (of 100) ]
[ time 55 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 44 (of 100) ]
[ time 56 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 43 (of 100) ]
[ time 57 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 42 (of 100) ]
[ time 58 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 41 (of 100) ]
[ time 59 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 40 (of 100) ]
[ time 60 ] Run JOB 0 at PRIORITY 0 [ TICKS 14 ALLOT 1 TIME 39 (of 100) ]
[ time 61 ] Run JOB 0 at PRIORITY 0 [ TICKS 13 ALLOT 1 TIME 38 (of 100) ]
[ time 62 ] Run JOB 0 at PRIORITY 0 [ TICKS 12 ALLOT 1 TIME 37 (of 100) ]
[ time 63 ] Run JOB 0 at PRIORITY 0 [ TICKS 11 ALLOT 1 TIME 36 (of 100) ]
[ time 64 ] Run JOB 0 at PRIORITY 0 [ TICKS 10 ALLOT 1 TIME 35 (of 100) ]
[ time 65 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 34 (of 100) ]
[ time 66 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 33 (of 100) ]
[ time 67 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 32 (of 100) ]
[ time 68 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 31 (of 100) ]
[ time 69 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 30 (of 100) ]
[ time 70 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 29 (of 100) ]
[ time 71 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 28 (of 100) ]
[ time 72 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 27 (of 100) ]
[ time 73 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 26 (of 100) ]
[ time 74 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 25 (of 100) ]
[ time 75 ] Run JOB 0 at PRIORITY 0 [ TICKS 14 ALLOT 1 TIME 24 (of 100) ]
[ time 76 ] Run JOB 0 at PRIORITY 0 [ TICKS 13 ALLOT 1 TIME 23 (of 100) ]
[ time 77 ] Run JOB 0 at PRIORITY 0 [ TICKS 12 ALLOT 1 TIME 22 (of 100) ]
[ time 78 ] Run JOB 0 at PRIORITY 0 [ TICKS 11 ALLOT 1 TIME 21 (of 100) ]
[ time 79 ] Run JOB 0 at PRIORITY 0 [ TICKS 10 ALLOT 1 TIME 20 (of 100) ]
[ time 80 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 19 (of 100) ]
[ time 81 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 18 (of 100) ]
[ time 82 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 17 (of 100) ]
[ time 83 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 16 (of 100) ]
[ time 84 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 15 (of 100) ]
[ time 85 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 14 (of 100) ]
[ time 86 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 13 (of 100) ]
[ time 87 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 12 (of 100) ]
[ time 88 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 11 (of 100) ]
[ time 89 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 10 (of 100) ]
[ time 90 ] Run JOB 0 at PRIORITY 0 [ TICKS 14 ALLOT 1 TIME 9 (of 100) ]
[ time 91 ] Run JOB 0 at PRIORITY 0 [ TICKS 13 ALLOT 1 TIME 8 (of 100) ]
[ time 92 ] Run JOB 0 at PRIORITY 0 [ TICKS 12 ALLOT 1 TIME 7 (of 100) ]
[ time 93 ] Run JOB 0 at PRIORITY 0 [ TICKS 11 ALLOT 1 TIME 6 (of 100) ]
[ time 94 ] Run JOB 0 at PRIORITY 0 [ TICKS 10 ALLOT 1 TIME 5 (of 100) ]
[ time 95 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 4 (of 100) ]
[ time 96 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 3 (of 100) ]
[ time 97 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 2 (of 100) ]
[ time 98 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 1 (of 100) ]
[ time 99 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 0 (of 100) ]
[ time 100 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround 100

  Avg  0: startTime n/a - response 0.00 - turnaround 100.00
```
🔧 **Parámetros configurados**
- Número de colas: 3 (prioridades 2, 1, 0; 2 es la más alta)
- Quantum por cola: 15 para todas
- Allotments: 1 en cada cola (solo un "quantum" completo antes de bajar de prioridad)
- boost: 0 (no hay boost periódico, es decir, los procesos no suben de prioridad automáticamente)
- stayAfterIO: True (si hubiera I/O, el proceso mantiene su prioridad)
- iobump: False (la prioridad no se incrementa tras hacer I/O)
- Job 0:
   - startTime = 0
   - runTime = 100
   - ioFreq = 0 (nunca hace I/O)

🧠 **Comportamiento del trabajo (Job 0)**

1. Inicio:

  - El trabajo entra al sistema en time = 0.
  - Comienza en la cola de prioridad más alta: cola 2.

2. Descenso de prioridad:

  - En cada cola tiene un solo allotment = 1, lo que significa que tras consumir un quantum completo (15 ticks), el trabajo baja a la 
    siguiente cola.
  - Al no hacer I/O (ioFreq = 0), el trabajo nunca se pausa ni recupera prioridad.

3. Ejecución:

  - Ejecuta:

     - 15 ticks en cola 2 → baja a prioridad 1
     - 15 ticks en cola 1 → baja a prioridad 0
     - Luego permanece en cola 0 por el resto del tiempo hasta finalizar
     - En cada quantum en cola 0, se reinicia el contador de ticks (porque allotment sigue siendo 1)

🕒 **Resumen de ejecución**
| Cola | Inicio en tiempo | Duración (ticks) |
|------|------------------|------------------|
| 2 (alta) | 0 | 15 |
| 1 (media) | 15 | 15 |
| 0 (baja) | 30 | 70 |

📌 **Observaciones clave**

- Sin I/O y sin boost, el trabajo permanece estancado en la cola más baja (0) después de agotar sus allotments.
- Tiempos de quantum y allotments son iguales en todas las colas, por lo tanto el descenso es automático cada 15 unidades de tiempo si no 
  hay I/O.
- La ejecución es continua porque no hay competencia con otros trabajos ni eventos de E/S.
- El trabajo termina exactamente al time = 100, como se esperaba.

✅ **Conclusión**

Este comportamiento muestra cómo el planificador MLFQ penaliza los procesos CPU-bound (sin I/O) bajándolos rápidamente a la cola más baja, donde permanecen. Es un ejemplo clásico del diseño de MLFQ para favorecer trabajos interactivos (que hacen I/O frecuentemente).

### 🚀 Pregunta 5
Ejecute:
```bash
./mlfq.py -n 3 -q 10 -B 200
```
📌 **¿con qué frecuencia debería aumentar los trabajos al nivel de prioridad más alto (con la -B bandera) para garantizar que un solo trabajo de larga duración (y potencialmente hambriento) obtenga al menos el 5% de la CPU?**

🔹 **¿Qué significa esto?**

- La cola más alta tiene una cuántica de 10 ms, es decir, un proceso que se encuentra allí puede ejecutarse durante 10 ms antes de ser 
bajado de nivel si no termina.
- La bandera -B en el script mlfq.py permite que periódicamente los trabajos vuelvan a la cola de más alta prioridad (es decir, "boosting").
- El enunciado pide encontrar con qué frecuencia debe hacerse este boost para que un proceso largo (que normalmente bajaría de nivel por usar toda la cuántica) no se quede con menos del 5% del tiempo total de CPU.

❗**Significado de los parámetros:**
- -n 3: Ejecutar la simulación con 3 procesos.
- -q 10: Cuánto tiempo (en unidades de tiempo) puede ejecutar un proceso antes de que ocurra interrupción por quantum (tiempo de CPU por turno).
- -B 200: La duración total de la simulación es de 200 unidades de tiempo.

Ahora ejecutamos el script
```
Here is the list of inputs:
OPTIONS jobs 3
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 200
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  84 - ioFreq   7
  Job  1: startTime   0 - runTime  42 - ioFreq   3
  Job  2: startTime   0 - runTime  51 - ioFreq   4

Compute the execution trace for the given workloads.
If you would like, also compute the response and turnaround
times for each of the jobs.
```
Y ahora una ejecucion mas detallada 

```
Here is the list of inputs:
OPTIONS jobs 3
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 200
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  84 - ioFreq   7
  Job  1: startTime   0 - runTime  42 - ioFreq   3
  Job  2: startTime   0 - runTime  51 - ioFreq   4


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] JOB BEGINS by JOB 1
[ time 0 ] JOB BEGINS by JOB 2
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 83 (of 84) ]
[ time 1 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 82 (of 84) ]
[ time 2 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 81 (of 84) ]
[ time 3 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 80 (of 84) ]
[ time 4 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 79 (of 84) ]
[ time 5 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 78 (of 84) ]
[ time 6 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 77 (of 84) ]
[ time 7 ] IO_START by JOB 0
IO DONE
[ time 7 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 41 (of 42) ]
[ time 8 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 40 (of 42) ]
[ time 9 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 39 (of 42) ]
[ time 10 ] IO_START by JOB 1
IO DONE
[ time 10 ] Run JOB 2 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 50 (of 51) ]
[ time 11 ] Run JOB 2 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 49 (of 51) ]
[ time 12 ] IO_DONE by JOB 0
[ time 12 ] Run JOB 2 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 48 (of 51) ]
[ time 13 ] Run JOB 2 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 47 (of 51) ]
[ time 14 ] IO_START by JOB 2
IO DONE
[ time 14 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 76 (of 84) ]
[ time 15 ] IO_DONE by JOB 1
[ time 15 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 75 (of 84) ]
[ time 16 ] Run JOB 0 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 74 (of 84) ]
[ time 17 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 38 (of 42) ]
[ time 18 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 37 (of 42) ]
[ time 19 ] IO_DONE by JOB 2
[ time 19 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 36 (of 42) ]
[ time 20 ] IO_START by JOB 1
IO DONE
[ time 20 ] Run JOB 2 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 46 (of 51) ]
[ time 21 ] Run JOB 2 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 45 (of 51) ]
[ time 22 ] Run JOB 2 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 44 (of 51) ]
[ time 23 ] Run JOB 2 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 43 (of 51) ]
[ time 24 ] IO_START by JOB 2
IO DONE
[ time 24 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 73 (of 84) ]
[ time 25 ] IO_DONE by JOB 1
[ time 25 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 35 (of 42) ]
[ time 26 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 34 (of 42) ]
[ time 27 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 33 (of 42) ]
[ time 28 ] IO_START by JOB 1
IO DONE
[ time 28 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 72 (of 84) ]
[ time 29 ] IO_DONE by JOB 2
[ time 29 ] Run JOB 2 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 42 (of 51) ]
[ time 30 ] Run JOB 2 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 41 (of 51) ]
[ time 31 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 71 (of 84) ]
[ time 32 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 70 (of 84) ]
[ time 33 ] IO_START by JOB 0
IO DONE
[ time 33 ] IO_DONE by JOB 1
[ time 33 ] Run JOB 1 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 32 (of 42) ]
[ time 34 ] Run JOB 2 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 40 (of 51) ]
[ time 35 ] Run JOB 2 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 39 (of 51) ]
[ time 36 ] IO_START by JOB 2
IO DONE
[ time 36 ] Run JOB 1 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 31 (of 42) ]
[ time 37 ] Run JOB 1 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 30 (of 42) ]
[ time 38 ] IO_START by JOB 1
IO DONE
[ time 38 ] IO_DONE by JOB 0
[ time 38 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 69 (of 84) ]
[ time 39 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 68 (of 84) ]
[ time 40 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 67 (of 84) ]
[ time 41 ] IO_DONE by JOB 2
[ time 41 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 66 (of 84) ]
[ time 42 ] Run JOB 0 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 65 (of 84) ]
[ time 43 ] IO_DONE by JOB 1
[ time 43 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 64 (of 84) ]
[ time 44 ] Run JOB 2 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 38 (of 51) ]
[ time 45 ] Run JOB 2 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 37 (of 51) ]
[ time 46 ] Run JOB 2 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 36 (of 51) ]
[ time 47 ] Run JOB 2 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 35 (of 51) ]
[ time 48 ] IO_START by JOB 2
IO DONE
[ time 48 ] Run JOB 1 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 29 (of 42) ]
[ time 49 ] Run JOB 1 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 28 (of 42) ]
[ time 50 ] Run JOB 1 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 27 (of 42) ]
[ time 51 ] IO_START by JOB 1
IO DONE
[ time 51 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 63 (of 84) ]
[ time 52 ] IO_START by JOB 0
IO DONE
[ time 52 ] IDLE
[ time 53 ] IO_DONE by JOB 2
[ time 53 ] Run JOB 2 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 34 (of 51) ]
[ time 54 ] Run JOB 2 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 33 (of 51) ]
[ time 55 ] Run JOB 2 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 32 (of 51) ]
[ time 56 ] IO_DONE by JOB 1
[ time 56 ] Run JOB 2 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 31 (of 51) ]
[ time 57 ] IO_START by JOB 2
IO DONE
[ time 57 ] IO_DONE by JOB 0
[ time 57 ] Run JOB 1 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 26 (of 42) ]
[ time 58 ] Run JOB 1 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 25 (of 42) ]
[ time 59 ] Run JOB 1 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 24 (of 42) ]
[ time 60 ] IO_START by JOB 1
IO DONE
[ time 60 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 62 (of 84) ]
[ time 61 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 61 (of 84) ]
[ time 62 ] IO_DONE by JOB 2
[ time 62 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 60 (of 84) ]
[ time 63 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 59 (of 84) ]
[ time 64 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 58 (of 84) ]
[ time 65 ] IO_DONE by JOB 1
[ time 65 ] Run JOB 1 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 23 (of 42) ]
[ time 66 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 22 (of 42) ]
[ time 67 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 57 (of 84) ]
[ time 68 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 56 (of 84) ]
[ time 69 ] IO_START by JOB 0
IO DONE
[ time 69 ] Run JOB 2 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 30 (of 51) ]
[ time 70 ] Run JOB 2 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 29 (of 51) ]
[ time 71 ] Run JOB 2 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 28 (of 51) ]
[ time 72 ] Run JOB 2 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 27 (of 51) ]
[ time 73 ] IO_START by JOB 2
IO DONE
[ time 73 ] Run JOB 1 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 21 (of 42) ]
[ time 74 ] IO_START by JOB 1
IO DONE
[ time 74 ] IO_DONE by JOB 0
[ time 74 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 55 (of 84) ]
[ time 75 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 54 (of 84) ]
[ time 76 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 53 (of 84) ]
[ time 77 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 52 (of 84) ]
[ time 78 ] IO_DONE by JOB 2
[ time 78 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 51 (of 84) ]
[ time 79 ] IO_DONE by JOB 1
[ time 79 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 50 (of 84) ]
[ time 80 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 49 (of 84) ]
[ time 81 ] IO_START by JOB 0
IO DONE
[ time 81 ] Run JOB 2 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 26 (of 51) ]
[ time 82 ] Run JOB 2 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 25 (of 51) ]
[ time 83 ] Run JOB 2 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 24 (of 51) ]
[ time 84 ] Run JOB 2 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 23 (of 51) ]
[ time 85 ] IO_START by JOB 2
IO DONE
[ time 85 ] Run JOB 1 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 20 (of 42) ]
[ time 86 ] IO_DONE by JOB 0
[ time 86 ] Run JOB 1 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 19 (of 42) ]
[ time 87 ] Run JOB 1 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 18 (of 42) ]
[ time 88 ] IO_START by JOB 1
IO DONE
[ time 88 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 48 (of 84) ]
[ time 89 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 47 (of 84) ]
[ time 90 ] IO_DONE by JOB 2
[ time 90 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 46 (of 84) ]
[ time 91 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 45 (of 84) ]
[ time 92 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 44 (of 84) ]
[ time 93 ] IO_DONE by JOB 1
[ time 93 ] Run JOB 2 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 22 (of 51) ]
[ time 94 ] Run JOB 2 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 21 (of 51) ]
[ time 95 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 43 (of 84) ]
[ time 96 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 42 (of 84) ]
[ time 97 ] IO_START by JOB 0
IO DONE
[ time 97 ] Run JOB 1 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 17 (of 42) ]
[ time 98 ] Run JOB 1 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 16 (of 42) ]
[ time 99 ] Run JOB 1 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 15 (of 42) ]
[ time 100 ] IO_START by JOB 1
IO DONE
[ time 100 ] Run JOB 2 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 20 (of 51) ]
[ time 101 ] Run JOB 2 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 19 (of 51) ]
[ time 102 ] IO_START by JOB 2
IO DONE
[ time 102 ] IO_DONE by JOB 0
[ time 102 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 41 (of 84) ]
[ time 103 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 40 (of 84) ]
[ time 104 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 39 (of 84) ]
[ time 105 ] IO_DONE by JOB 1
[ time 105 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 38 (of 84) ]
[ time 106 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 37 (of 84) ]
[ time 107 ] IO_DONE by JOB 2
[ time 107 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 36 (of 84) ]
[ time 108 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 35 (of 84) ]
[ time 109 ] IO_START by JOB 0
IO DONE
[ time 109 ] Run JOB 1 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 14 (of 42) ]
[ time 110 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 13 (of 42) ]
[ time 111 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 12 (of 42) ]
[ time 112 ] IO_START by JOB 1
IO DONE
[ time 112 ] Run JOB 2 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 18 (of 51) ]
[ time 113 ] Run JOB 2 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 17 (of 51) ]
[ time 114 ] IO_DONE by JOB 0
[ time 114 ] Run JOB 2 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 16 (of 51) ]
[ time 115 ] Run JOB 2 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 15 (of 51) ]
[ time 116 ] IO_START by JOB 2
IO DONE
[ time 116 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 34 (of 84) ]
[ time 117 ] IO_DONE by JOB 1
[ time 117 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 33 (of 84) ]
[ time 118 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 32 (of 84) ]
[ time 119 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 31 (of 84) ]
[ time 120 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 30 (of 84) ]
[ time 121 ] IO_DONE by JOB 2
[ time 121 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 29 (of 84) ]
[ time 122 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 28 (of 84) ]
[ time 123 ] IO_START by JOB 0
IO DONE
[ time 123 ] Run JOB 1 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 11 (of 42) ]
[ time 124 ] Run JOB 1 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 10 (of 42) ]
[ time 125 ] Run JOB 1 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 9 (of 42) ]
[ time 126 ] IO_START by JOB 1
IO DONE
[ time 126 ] Run JOB 2 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 14 (of 51) ]
[ time 127 ] Run JOB 2 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 13 (of 51) ]
[ time 128 ] IO_DONE by JOB 0
[ time 128 ] Run JOB 2 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 12 (of 51) ]
[ time 129 ] Run JOB 2 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 11 (of 51) ]
[ time 130 ] IO_START by JOB 2
IO DONE
[ time 130 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 27 (of 84) ]
[ time 131 ] IO_DONE by JOB 1
[ time 131 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 26 (of 84) ]
[ time 132 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 25 (of 84) ]
[ time 133 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 24 (of 84) ]
[ time 134 ] Run JOB 1 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 8 (of 42) ]
[ time 135 ] IO_DONE by JOB 2
[ time 135 ] Run JOB 1 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 7 (of 42) ]
[ time 136 ] Run JOB 1 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 6 (of 42) ]
[ time 137 ] IO_START by JOB 1
IO DONE
[ time 137 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 23 (of 84) ]
[ time 138 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 22 (of 84) ]
[ time 139 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 21 (of 84) ]
[ time 140 ] IO_START by JOB 0
IO DONE
[ time 140 ] Run JOB 2 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 10 (of 51) ]
[ time 141 ] Run JOB 2 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 9 (of 51) ]
[ time 142 ] IO_DONE by JOB 1
[ time 142 ] Run JOB 2 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 8 (of 51) ]
[ time 143 ] Run JOB 2 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 7 (of 51) ]
[ time 144 ] IO_START by JOB 2
IO DONE
[ time 144 ] Run JOB 1 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 5 (of 42) ]
[ time 145 ] IO_DONE by JOB 0
[ time 145 ] Run JOB 1 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 4 (of 42) ]
[ time 146 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 3 (of 42) ]
[ time 147 ] IO_START by JOB 1
IO DONE
[ time 147 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 20 (of 84) ]
[ time 148 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 19 (of 84) ]
[ time 149 ] IO_DONE by JOB 2
[ time 149 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 18 (of 84) ]
[ time 150 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 17 (of 84) ]
[ time 151 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 16 (of 84) ]
[ time 152 ] IO_DONE by JOB 1
[ time 152 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 15 (of 84) ]
[ time 153 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 14 (of 84) ]
[ time 154 ] IO_START by JOB 0
IO DONE
[ time 154 ] Run JOB 2 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 6 (of 51) ]
[ time 155 ] Run JOB 2 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 5 (of 51) ]
[ time 156 ] Run JOB 2 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 4 (of 51) ]
[ time 157 ] Run JOB 2 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 3 (of 51) ]
[ time 158 ] IO_START by JOB 2
IO DONE
[ time 158 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 2 (of 42) ]
[ time 159 ] IO_DONE by JOB 0
[ time 159 ] Run JOB 1 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 1 (of 42) ]
[ time 160 ] Run JOB 1 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 0 (of 42) ]
[ time 161 ] FINISHED JOB 1
[ time 161 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 13 (of 84) ]
[ time 162 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 12 (of 84) ]
[ time 163 ] IO_DONE by JOB 2
[ time 163 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 11 (of 84) ]
[ time 164 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 10 (of 84) ]
[ time 165 ] Run JOB 0 at PRIORITY 0 [ TICKS 5 ALLOT 1 TIME 9 (of 84) ]
[ time 166 ] Run JOB 0 at PRIORITY 0 [ TICKS 4 ALLOT 1 TIME 8 (of 84) ]
[ time 167 ] Run JOB 0 at PRIORITY 0 [ TICKS 3 ALLOT 1 TIME 7 (of 84) ]
[ time 168 ] IO_START by JOB 0
IO DONE
[ time 168 ] Run JOB 2 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 2 (of 51) ]
[ time 169 ] Run JOB 2 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 1 (of 51) ]
[ time 170 ] Run JOB 2 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 0 (of 51) ]
[ time 171 ] FINISHED JOB 2
[ time 171 ] IDLE
[ time 172 ] IDLE
[ time 173 ] IO_DONE by JOB 0
[ time 173 ] Run JOB 0 at PRIORITY 0 [ TICKS 2 ALLOT 1 TIME 6 (of 84) ]
[ time 174 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 5 (of 84) ]
[ time 175 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 4 (of 84) ]
[ time 176 ] Run JOB 0 at PRIORITY 0 [ TICKS 9 ALLOT 1 TIME 3 (of 84) ]
[ time 177 ] Run JOB 0 at PRIORITY 0 [ TICKS 8 ALLOT 1 TIME 2 (of 84) ]
[ time 178 ] Run JOB 0 at PRIORITY 0 [ TICKS 7 ALLOT 1 TIME 1 (of 84) ]
[ time 179 ] Run JOB 0 at PRIORITY 0 [ TICKS 6 ALLOT 1 TIME 0 (of 84) ]
[ time 180 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround 180
  Job  1: startTime   0 - response   7 - turnaround 161
  Job  2: startTime   0 - response  10 - turnaround 171

  Avg  2: startTime n/a - response 5.67 - turnaround 170.67
```

🔍 **Resultados y análisis**
⚙️ **Configuración del Planificador**
- Se utilizaron tres colas de prioridad (2, 1 y 0, siendo 2 la de mayor prioridad). La configuración del planificador MLFQ fue la siguiente:
   - Quantum de cada cola: 10 unidades de tiempo.
   - Allotment (asignación de veces que puede ser elegido antes de bajar de nivel): 1 para todas las colas.
   - I/O time: 5 unidades de tiempo.
   - Boost (reinicio de prioridades): cada 200 unidades.
   - stayAfterIO: False (los procesos que hacen I/O no conservan su nivel).
   - iobump: False (no suben de prioridad al volver de I/O).

🧪 **Características de los Trabajos**
| Job | startTime | runTime | ioFreq |
|-----|-----------|---------|--------|
| 0   | 0         | 84      | 7      |
| 1   | 0         | 42      | 3      |
| 2   | 0         | 51      | 4      |

📊 **Comportamiento Observado**

1. Inicialización:
- Todos los trabajos inician al tiempo 0 en la cola de prioridad más alta (2).
- El planificador comienza ejecutando el Job 0.
2. I/O y cambio de prioridades:
- Los trabajos hacen I/O frecuentemente. Por ejemplo:
   - Job 0 hace I/O cada 7 unidades.
   - Job 1 cada 3.
   - Job 2 cada 4.
- Debido a la política stayAfterIO = False, los trabajos pierden prioridad tras hacer I/O, y con allotments = 1, rápidamente se degradan de nivel.
3. Cambio de prioridades:
- Se observa que todos los procesos eventualmente llegan a la cola de menor prioridad (0) por agotar su allotment tras cada ejecución.
- Por ejemplo:
   - A tiempo 24, Job 0 es ejecutado en prioridad 1.
   - A tiempo 51, Job 0 ya está en prioridad 0.
4. Equidad (Fairness):
- Aunque Job 1 y Job 2 tienen menor tiempo de ejecución, se ven igualmente afectados por las políticas del planificador, y descienden de prioridad rápidamente.
- No hay boost, por lo tanto, los procesos permanecen en las colas más bajas una vez que llegan allí.
5. Starvation (Inanición):
- No se observa inanición total gracias a que todos los trabajos tienen tiempo asignado incluso en la cola de menor prioridad.
- Sin embargo, el descenso agresivo de prioridad y la falta de boost podría causar retardo considerable en sistemas con más procesos.
6. Ineficiencias y tiempos muertos:
- En algunos momentos, el planificador entra en estado IDLE (por ejemplo, en tiempo 52), lo cual refleja tiempos donde ningún proceso está disponible en CPU por estar en I/O.

🧠 **Conclusiones**
- La política de descenso automático tras el uso de CPU, sin boost, hace que todos los procesos eventualmente terminen en la cola de menor prioridad, aumentando su tiempo de espera.
- El valor de stayAfterIO = False penaliza a procesos I/O-bound, haciéndolos bajar de prioridad a pesar de ceder voluntariamente la CPU.
- Si se desea una mejor respuesta para procesos interactivos (con I/O frecuentes), convendría habilitar iobump = True o stayAfterIO = True, o reducir el tiempo de boost.
- A pesar de que el sistema evita la inanición, no logra garantizar eficiencia ni respuesta rápida para procesos más cortos.

### 🚀 Pregunta 6
Ejecute:
```bash
./mlfq.py -l 0,20,5:1,20,0
```
📌 **indicador -I**

✳️ **¿Qué hace -I?**
- Sin -I (por defecto): un trabajo que finaliza su E/S se agrega al final de la cola correspondiente a su prioridad actual.
- Con -I activado: el trabajo que finaliza su E/S se agrega al principio de la cola correspondiente, por lo tanto será ejecutado antes que los demás trabajos que ya estaban esperando en esa cola.

✳️ **¿Qué hace este comando?**
- -l 0,20,5:1,20,0: Crea dos trabajos:
   - Job 0: inicia en el tiempo 0, necesita 20 unidades de CPU y hace I/O cada 5 unidades.
   - Job 1: inicia en el tiempo 1, necesita 20 unidades y no hace I/O (ioFreq=0).

Veamos el resultado detallado de la ejecucion sin -I
```
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  20 - ioFreq   5
  Job  1: startTime   1 - runTime  20 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 19 (of 20) ]
[ time 1 ] JOB BEGINS by JOB 1
[ time 1 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 18 (of 20) ]
[ time 2 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 17 (of 20) ]
[ time 3 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 16 (of 20) ]
[ time 4 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 15 (of 20) ]
[ time 5 ] IO_START by JOB 0
IO DONE
[ time 5 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 19 (of 20) ]
[ time 6 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 18 (of 20) ]
[ time 7 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 17 (of 20) ]
[ time 8 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 16 (of 20) ]
[ time 9 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 15 (of 20) ]
[ time 10 ] IO_DONE by JOB 0
[ time 10 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 14 (of 20) ]
[ time 11 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 13 (of 20) ]
[ time 12 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 12 (of 20) ]
[ time 13 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 11 (of 20) ]
[ time 14 ] Run JOB 1 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 10 (of 20) ]
[ time 15 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 14 (of 20) ]
[ time 16 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 13 (of 20) ]
[ time 17 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 12 (of 20) ]
[ time 18 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 11 (of 20) ]
[ time 19 ] Run JOB 0 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 10 (of 20) ]
[ time 20 ] IO_START by JOB 0
IO DONE
[ time 20 ] Run JOB 1 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 9 (of 20) ]
[ time 21 ] Run JOB 1 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 8 (of 20) ]
[ time 22 ] Run JOB 1 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 7 (of 20) ]
[ time 23 ] Run JOB 1 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 6 (of 20) ]
[ time 24 ] Run JOB 1 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 5 (of 20) ]
[ time 25 ] IO_DONE by JOB 0
[ time 25 ] Run JOB 1 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 4 (of 20) ]
[ time 26 ] Run JOB 1 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 3 (of 20) ]
[ time 27 ] Run JOB 1 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 2 (of 20) ]
[ time 28 ] Run JOB 1 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 1 (of 20) ]
[ time 29 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 0 (of 20) ]
[ time 30 ] FINISHED JOB 1
[ time 30 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 9 (of 20) ]
[ time 31 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 8 (of 20) ]
[ time 32 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 7 (of 20) ]
[ time 33 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 6 (of 20) ]
[ time 34 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 5 (of 20) ]
[ time 35 ] IO_START by JOB 0
IO DONE
[ time 35 ] IDLE
[ time 36 ] IDLE
[ time 37 ] IDLE
[ time 38 ] IDLE
[ time 39 ] IDLE
[ time 40 ] IO_DONE by JOB 0
[ time 40 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 4 (of 20) ]
[ time 41 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 3 (of 20) ]
[ time 42 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 2 (of 20) ]
[ time 43 ] Run JOB 0 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 1 (of 20) ]
[ time 44 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 0 (of 20) ]
[ time 45 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround  45
  Job  1: startTime   1 - response   4 - turnaround  29

  Avg  1: startTime n/a - response 2.00 - turnaround 37.00
```

🔍 **Análisis del resultado:**
🔧 **Parámetros por defecto:**
- 3 colas de prioridad: 2 (alta), 1 (media), 0 (baja).
- Cada cola tiene:
   - Quantum = 10 ticks
   - Allotment = 1 (si usa su quantum completo, baja de nivel)
- boost = 0 (sin reinicio de prioridades)
- ioTime = 5 (tiempo que dura el I/O)
- stayAfterIO = False: al terminar el I/O, reingresa con su prioridad anterior
- iobump = False: el I/O no sube prioridad

📊 **Comportamiento de los procesos:**

**JOB 0**
- Comienza a tiempo 0
- Hace I/O cada 5 ticks → pierde CPU cada cierto tiempo
- Requiere 20 ticks de CPU en total
- Como stayAfterIO = False, vuelve con la misma prioridad tras I/O
- Termina en el tiempo 45
- Turnaround: 45 - 0 = 45
- Response time: 0 (empieza a ejecutarse al llegar)

**JOB 1**
- Comienza a tiempo 1
- No realiza I/O
- Gana la CPU cuando JOB 0 hace I/O
- Se degrada de prioridad 2 → 1 al agotar su quantum
- Termina en el tiempo 30
- Turnaround: 30 - 1 = 29
- Response time: 5 - 1 = 4

📈 **Métricas finales:**
- Response time promedio: (0 + 4) / 2 = 2.0
- Turnaround promedio: (45 + 29) / 2 = 37.0

Ahora veremos cómo cambiaría este comportamiento si activamos -I para que los trabajos que terminan I/O recuperen prioridad

```
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump True


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime  20 - ioFreq   5
  Job  1: startTime   1 - runTime  20 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 19 (of 20) ]
[ time 1 ] JOB BEGINS by JOB 1
[ time 1 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 18 (of 20) ]
[ time 2 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 17 (of 20) ]
[ time 3 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 16 (of 20) ]
[ time 4 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 15 (of 20) ]
[ time 5 ] IO_START by JOB 0
IO DONE
[ time 5 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 19 (of 20) ]
[ time 6 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 18 (of 20) ]
[ time 7 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 17 (of 20) ]
[ time 8 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 16 (of 20) ]
[ time 9 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 15 (of 20) ]
[ time 10 ] IO_DONE by JOB 0
[ time 10 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 14 (of 20) ]
[ time 11 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 13 (of 20) ]
[ time 12 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 12 (of 20) ]
[ time 13 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 11 (of 20) ]
[ time 14 ] Run JOB 0 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 10 (of 20) ]
[ time 15 ] IO_START by JOB 0
IO DONE
[ time 15 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 14 (of 20) ]
[ time 16 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 13 (of 20) ]
[ time 17 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 12 (of 20) ]
[ time 18 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 11 (of 20) ]
[ time 19 ] Run JOB 1 at PRIORITY 2 [ TICKS 0 ALLOT 1 TIME 10 (of 20) ]
[ time 20 ] IO_DONE by JOB 0
[ time 20 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 9 (of 20) ]
[ time 21 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 8 (of 20) ]
[ time 22 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 7 (of 20) ]
[ time 23 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 6 (of 20) ]
[ time 24 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 5 (of 20) ]
[ time 25 ] IO_START by JOB 0
IO DONE
[ time 25 ] Run JOB 1 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 9 (of 20) ]
[ time 26 ] Run JOB 1 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 8 (of 20) ]
[ time 27 ] Run JOB 1 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 7 (of 20) ]
[ time 28 ] Run JOB 1 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 6 (of 20) ]
[ time 29 ] Run JOB 1 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 5 (of 20) ]
[ time 30 ] IO_DONE by JOB 0
[ time 30 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 4 (of 20) ]
[ time 31 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 3 (of 20) ]
[ time 32 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 2 (of 20) ]
[ time 33 ] Run JOB 0 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 1 (of 20) ]
[ time 34 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 0 (of 20) ]
[ time 35 ] FINISHED JOB 0
[ time 35 ] Run JOB 1 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 4 (of 20) ]
[ time 36 ] Run JOB 1 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 3 (of 20) ]
[ time 37 ] Run JOB 1 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 2 (of 20) ]
[ time 38 ] Run JOB 1 at PRIORITY 1 [ TICKS 1 ALLOT 1 TIME 1 (of 20) ]
[ time 39 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 0 (of 20) ]
[ time 40 ] FINISHED JOB 1

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround  35
  Job  1: startTime   1 - response   4 - turnaround  39

  Avg  1: startTime n/a - response 2.00 - turnaround 37.00
```

↔️ **Comparación sin -I vs con -I**

| Métrica         | Job 0 (sin `-I`) | Job 0 (con `-I`) | Job 1 (sin `-I`) | Job 1 (con `-I`) |
|-----------------|------------------|------------------|------------------|------------------|
| Tiempo de respuesta | 0                | 0                | 4                | 4                |
| Tiempo de turnaround | 45               | 35               | 29               | 39               |

📊 **Análisis**
- ✅ Job 0 se beneficia del -I: su turnaround baja de 45 a 35. Esto ocurre porque es promovido de prioridad al salir de I/O, lo que le da más acceso a CPU.
- ❌ Job 1 empeora con -I: su turnaround sube de 29 a 39, ya que Job 0 le "quita CPU" más veces después de volver del I/O con mayor prioridad.
- 🟰 Tiempos de respuesta iguales: ambos trabajos comienzan a ejecutarse lo antes posible, así que -I no afecta ese aspecto.

📌 **Conclusión**
El flag -I favorece a trabajos que hacen I/O frecuente (como Job 0), dándoles prioridad tras cada I/O, pero puede penalizar a trabajos CPU-bound (como Job 1) al hacerlos esperar más.

## Conlusiones.
**1. El algoritmo MLFQ favorece trabajos interactivos**

Los trabajos que realizan operaciones de E/S frecuentes (I/O-bound) tienden a mantenerse en niveles de prioridad más altos gracias a las reglas como stayAfterIO y iobump, lo que les permite recibir más CPU en comparación con trabajos CPU-bound.

**2. La ausencia de boost puede generar inanición**

Cuando no se usa la opción de boosting (-B), los trabajos CPU-bound pueden descender a las colas de menor prioridad y permanecer allí indefinidamente, recibiendo menos CPU y aumentando sus tiempos de respuesta y turnaround.

**3. El uso de iobump mejora el rendimiento de trabajos con I/O**

Al activar la opción -I, los trabajos que terminan una operación de E/S se insertan al frente de su cola, mejorando su acceso a CPU. Esto reduce su turnaround pero puede perjudicar a trabajos que no hacen E/S.

**4. MLFQ puede configurarse como Round-Robin**

Si se usa una sola cola (-n 1) con un quantum fijo y sin degradación ni boosting, el comportamiento del planificador MLFQ emula exactamente el de un Round-Robin clásico, útil para comparar comportamientos de algoritmos.

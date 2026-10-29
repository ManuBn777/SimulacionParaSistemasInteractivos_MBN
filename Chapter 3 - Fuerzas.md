## UNIDAD 3
### Actividad 4

##### Instrumento funcional y publicado: 
https://manubn777.github.io/Chapter-3-Activity-3-/

#### Concepto

Quería un instrumento donde las partículas se sintieran como si tuvieran voluntad propia dependiendo del modo, a veces como arena que fluye libre como la que era el código original, a veces como un cuerpo rígido que respira con el beat de un botón, a veces como humo que persigue al puntero. Al escuchar la canción me imaginaba ciertas animaciones ya sea por el beat, alguno sonido en particular y copié mis ideas en una hoja de lo que me gustaría que tuviera el sistema

Inicié con un repositorio que tenía otra información y fue todo un proceso (lo cual implicó usar 3 ias diferentes porque ninguna hacía lo que quería o tal vez yo no me explicaba correctamente) hasta que llegó un punto en que la interfaz completa cambió y la pantalla era negra lo cual aparentemente era un error de los shaders (despues de verificar en la consola para ver el error), así que decidí devolverla a una versión anterior lo cual terminó en mi concepto de una esfera muy tiesa

<img width="1600" height="714" alt="20a11f41-d688-4b77-9b5f-8e907aff9082" src="https://github.com/user-attachments/assets/2c11a5ca-03b2-4529-b78e-fdab68924945" />

También se puede notar que aún estaban los sliders del otro repositorio, los cuales han ido cambiando durante el proceso (lo cual implicó una pelea con la ia, pero salió bien).

<img width="844" height="663" alt="920d0cf9-ae2f-45e3-90a3-2ab6e0e54d90" src="https://github.com/user-attachments/assets/aaf6da09-c8e9-409b-a058-dba5b24f9aa0" />

Logré que hubiera más partículas pero seguían de cierta manera tiesas (tristemente no tomé foto de la interfaz)

#### Mapa del sistema

Así está organizado el sistema (teniendo en cuenta que viene también del anterior repositorio)

###### parameters.js
Tiene todos los "estados" como la posición del puntero, en qué modo estoy (de los modos que tengo), los radios de cada forma, el ángulo del viento, y los disparadores de cada efecto (kick, estática, locura).

###### createSimulation.js
Aquí están todas las fuerzas, organizadas por modo (Arena, Esfera, Círculo, Puntero, Neutro), más algunas fuerzas universales que aplican sin importar el modo (viento, ondas del click, kick, contención).

###### main.js
Maneja todo el teclado, el mouse y el loop que se ejecuta en cada frame.

AUTO EVALUACION:

Criterio	Peso	Qué debe demostrar la evidencia	Valoración
Trazabilidad y comprensión del sistema	25	Puedo señalar y explicar estado, fuerzas, integración, render y controles; además puedo ubicar qué partes produjo o modificó la IA.	


Verificación del algoritmo de fuerzas	25	Estudié en detalle el proyecto y aunque no comprenda toda la sintaxis, puedo identificar su arquitectura, sus partes, puedo aislar una fuerza central, formular una predicción, la ejecuté ya analicé, comparé el resultado, cambié deliberadamente un signo o parámetro y expliqué la diferencia.	


Diseño de fuerzas e intención	20	Las fuerzas y sus parámetros hacen perceptible una intención; el comportamiento surge de la dinámica y no de trayectorias previamente dibujadas.	


Instrumento, score e interpretación	15	El score conecta la escucha con decisiones; escogí pocos controles expresivos y puedo conducir el sistema en vivo sin que el audio lo controle automáticamente.	


Experimentación y criterio frente a la IA	10	Comparé alternativas, registré hallazgos y descartes, corregí propuestas de IA y puedo justificar por qué conservé la versión presentada.	


Entrega técnica y documentación	5	la URL pública abre; la bitácora permite verificar el proceso.	
Total Puntos	???	



###### labPanel.js
Solo dibuja los botones del panel LAB (interfaz). Cada botón llama a la misma función que dispara la tecla correspondiente.

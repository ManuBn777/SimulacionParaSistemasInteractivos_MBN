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

###### labPanel.js
Solo dibuja los botones del panel LAB (interfaz). Cada botón llama a la misma función que dispara la tecla correspondiente.

AUTO EVALUACION U3:
1. Trazabilidad y comprensión del sistema — 19/25

Puedo señalar dónde está cada cosa (como en el mapa del sistema que hice), la posición y la velocidad de las partículas se guardan en createSimulation.js, ahí mismo están las fuerzas de cada modo, y main.js es el que escucha mis teclas y cambia los parámetros ademas se que primero se cambia la velocidad y después con esa se mueve la partícula como en el ejemplo del profe incluso sé qué partes hizo la IA pero hay algunas que todavía me cuesta explicar a fondo (sobre todo las fórmulas de las formas o otros detalles)

2. Verificación del algoritmo de fuerzas — 15/25

Entiendo cómo está armado y puedo probar las fuerzas con mis propios controles, como apretar todo al centro con el click derecho o abrirlo con el kick aunque sinceramente no hice muchas pruebas fue mas estilo prueba y error hasta que saliera como me lo habia imaginado y insistia hasta que saliera lo suficientemente bien

3. Diseño de fuerzas e intención — 18/20

Quería que las partículas se sintieran con voluntad propia, a veces como arena, a veces como un cuerpo que respira con el beat (esto en referencia que habia visto), a veces como humo que persigue al puntero todo teniendo en cuenta como lo visualizaba en mi mente además las partículas no se ponen a la fuerza en su lugar, sino que se van guiando solitas hasta llegar a la forma deseada (en el caso de modo circulo y modo esfera)

4. Instrumento, score e interpretación — 12/15

Tristemente no llegue a tocala en vivo con LesAlpx aun asi nada lo controla el audio, todo lo hago yo con el teclado y el mouse. Tiene muchísimos controles (demasiados la verdad) y la verdad al ser un proyecto "viejo" no me acuerdo que tenia en mente la Manuela del pasado, siento que podría haber organizado mejor, separando momentos de la cancion como por fases, pienso que tenia las ideas pero me falto organizar

5. Experimentación y criterio frente a la IA — 7/10

Usé 3 IAs diferentes porque ninguna hacía lo que quería, hubo un momento donde la pantalla se puso negra revisé la consola, vi que era un error de los shaders y decidí devolverme a una versión anterior. También pedí el esparcidor porque las partículas se quedaban atascadas en un punto, y decidí dejar el LAB como estaba pues era util con los botones.

6. Entrega técnica y documentación — 4/5

La página abre y funciona y en la bitácora se ve parte del proceso, pero le faltan cosas como el score y las pruebas

Total — 75/100



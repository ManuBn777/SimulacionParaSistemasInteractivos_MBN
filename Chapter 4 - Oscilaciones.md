## UNIDAD 4
### Actividad 2

##### Kuramoto Vocaloid: 
https://editor.p5js.org/ManuBn777/sketches/2U4a2Oji6

#### Concepto


#### Requisitos mínimos

La aplicación deberá cumplir, como mínimo, con las siguientes condiciones:

- 8 agentes simultáneos gobernados por el sistema dinámico.
R// Escogi 8 vocaloids que es un tema que me gusta bastante, Hatsune Miku, Rin y Len Kagamine, Megurine Luka, KAITO, MEIKO, Gumi y V Flower.Cada uno es un oscilador de Kuramoto con su propia fase y su propio ritmo natural ademas que cuanto terminen un ciclo cantan (se puede cambiar por instrumentos y voces, y me base de acuerdo a su presencia de las VoiceBanks originales)

- 4 personalidades audiovisuales diferentes.
R// Hice 8 personalidades organizadas en 4 (duos). Cada familia comparte una idea base y cada cantante le da su propio giro (quería que fueran diferentes entre si:
  - MIKU es la protagonista, ella salta más alto, suelta chispas y brilla más con el grupo como la Miku original y GUMI se mece como un metrónomo y da saltitos pequeños pero precisos
  - RIN y LEN dan un doble brinquito rápido e inclinándose en espejo y son los que más se sacuden cuando los empujo.(Esto porque el concepto de ellos es ser un espejo del otro, entonces me pareció un buen detalle)
  - KAITO y MEIKO casi no saltan y estilo durante su ciclo KAITO toma aire y al cantar se aplasta; MEIKO se recoge y al cantar se estira (y se complementan ligeramente al ser los más viejos si no estoy mal)
  - LUKA no salta, flota despacio y se mece (por el hecho de que su voz es muy suave); vFLOWER da un golpe tipo headbang (la mayoría de sus canciones son de rock y ella misma tiene una vibra muy rock)

- Cada agente deberá tener una manifestación visual y una manifestación sonora vinculadas a su comportamiento.
R// Lo visual y lo sonoro dependen directamente de la fase de Kuramoto, estilo: cuando un cantante completa su ciclo, en ese mismo instante suena su voz (o instrumento), se ilumina, suelta una onda y hace su movimiento. También cuando se sincronicen estos detalles también lo harán

- El usuario deberá poder modificar en tiempo real al menos 2 variables relacionadas con el modelo, siendo obligatorio poder intervenir (K).
R// En la banda gris de arriba hay sliders que se pueden mover por el usuario:
  - Unión del coro (K): qué tanto se escuchan los cantantes entre sí
  - Diferencia de ritmos: qué tan distintos son los ritmos naturales (ω) de cada cantante (estilo pueden ser todos iguales o todos con un ritmo diferente)
  - Tempo (BPM): el ritmo promedio del coro, acelera o frena a todos por igual (es simplemente la velocidad no afecta en la sincronización lo único que afecta es al público)

- Deberán existir al menos 2 formas diferentes de interacción performativa, una que afecte el comportamiento global del sistema y otra que permita intervenir en agentes individuales.
R// Pues están los sliders de diferencia de ritmos, unión del coro y tempo que cambian cómo se comporta todo el coro y con el botón "Desordenar a todos" (o la barra espaciadora) hacen que todos cambien o sea literal desordenar a todos
Pero también si haces clic en un cantante (o usando las teclas 1 a 8) para sacarlo de su ritmo, también puedo silenciar a cada uno o ponerlo en "solo" para escucharlo únicamente a él (esto era más para verificar que si estuviera sonando o solo quería escuchar ciertos instrumentos/voces y al final se quedó)

- Deberá existir al menos 1 mecanismo de perturbación que permita alterar el estado de uno o varios agentes y observar posteriormente la respuesta del colectivo.
R// El poderosismo botón de "Desordenar a todos" o también al hacer clic en un cantante, se puede empujar fuera de su ritmo, elevándose en el proceso; además, en la partitura queda una rayita blanca en el momento del empujón

- La experiencia deberá permitir reconocer al menos 3 estados colectivos: desorden, organización parcial y organización estable.
R// Pues como se pide y se pueden ver los 3 estados:
Desorden: con la unión baja, cada uno canta a su ritmo, los puntos de la partitura salen regados y se escucha una lluvia de notas sueltas.
Organización parcial: al subir la unión, primero se juntan los cantantes con ritmos parecidos, mientras los extremos (RIN, la más rápida, y KAITO, el más lento) se quedan por fuera.
Organización estable: con la unión alta, todos cantan juntos, suena como un acorde (o sea, todos tocando la misma nota pero con sonidos diferentes)

- Deberá existir al menos 1 forma perceptible de comunicar el estado colectivo. Puede ser visual, sonora, audiovisual o mediante un indicador explícito.
R// Pues hay varios uno es el indicador arriba a la derecha con el nombre del estado y una barra que muestra R (qué tan juntos están) como una barra de progreso que va variando, lo otro es que cada cantante brilla según qué tan unido está al grupo, así que en la organización parcial se ve quiénes están juntos y quiénes no, tambien temeos la partitura en la pantalla azul cuando los puntos quedan alineados en vertical y ya por ultimo el sonido pues logicamente cuando estan desordenadas pues suena notas sueltas y si se sincronizan sonara un acorde junto
 

#### Preguntas clave

¿Cómo convertir un modelo de autoorganización en un instrumento audiovisual performativo?

¿Qué hace Kuramoto en esta experiencia que no podría resolverse simplemente mediante un reloj global, un secuenciador o temporizadores independientes?

<img width="1140" height="691" alt="image" src="https://github.com/user-attachments/assets/10c8113f-df5b-4a85-aa8d-9993841a2d5d" />
Este fue el primer boceto que hice con la ia, siendo demasiado técnico por ahora quería plantear los 8 vocaloids, pero siento que se puede pulir aun mas 

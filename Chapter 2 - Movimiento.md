<img width="996" height="636" alt="f1cae78e-059f-4266-bbac-03b3087a7d21" src="https://github.com/user-attachments/assets/d916dd90-2bd7-4a11-bfa4-935f0f64f287" />## UNIDAD 2
### Actividad 5
#### Reto de diseño: una contradicción en movimiento

##### Intencion:
Formula la tensión: "Quiero explorar la tensión entre la necesidad de conectar con los demás y el deseo de mantener la propia libertad."

Quería mostrar que no todas las personas viven el amor de la misma manera, algunas buscan relaciones, otras no, algunas se obsesionan a niveles no sanos y otras simplemente ya existen con aquella persona que les gusta

###### Tipos de partícula:

Hice en total 6 tipos de partículas diferentes 

Amor: seleccione el amor como simbolismo visual de este, este se atrae a sí mismo y también se atrae a los demás por eso todos sus números son positivos

Buscadoras: Quería que un tipo de partícula representara a esas personas que buscan constantemente una relación, quería que persiguieran a las receptivas para representar un amor no correspondido pero además que se sientan atraídas hacia el amor en general también porque es lo que buscan al final, solo un poco de amor

Receptivas: (aunque de receptivas no tiene mucho excepto consigo mismas) quería representar a aquellos que ya encontraron su lugar o pareja, por eso forman pequeños grupos entre ellas y rechazan a las buscadoras

Obsesión: selección a este tipo porque quería representar una relación tóxica y que solo persiguiera a un solo tipo de partícula

Independencia: aquí quería representar a quienes quieren mantener su libertad y alejarse de esas relaciones tóxicas, huyen de la obsesión pero sin alejarse completamente del amor

Errantes: Este tipo representa a quienes no participan en las dinámicas románticas, evitan a todo el mundo y se mueven libremente sin formar grupos estables

###### Cantidad de partículas:
Amor (120): Quería que estuviera presente en gran parte del sistema pues es la representacion pura del amor y que pudieran formar grupos visibles
Buscadoras (90): Quería que hubiera suficientes para generar persecuciones si alguna receptiva estuviera cerca o que simplemente se mantenga muy cerca del amor
Receptivas (90): Tienen la misma cantidad para mantener un equilibrio con las Buscadoras pero que también formen sus círculos entre ellas
Obsesión (35): Es la población más pequeña porque representa un comportamiento menos común, pero mucho más intenso.
Independencia (90): Quería que siempre existieran partículas que pudieran escapar de la Obsesión.
Errantes / Aroace (80): Para que no se sienta tan solo el espacio hice que hubiera partículas recorriendo el espacio sin seguir las mismas dinámicas que las demás...ellas evitan a todo el mundo incluso a sí mismas

###### Matriz de atracción, repulsión e indiferencia:
  //  Amor,   Busc,  Recept, Obses, Indep, Aroace
  [  0.3,   0.4,    0.2,   0.1,   0.2,    0.1 ], // 0. Amor
  [  0.6,  -0.7,    0.8,  -0.1,  -0.3,   -0.5 ], // 1. Buscadoras
  [  0.1,  -0.9,    0.4,   0.0,  -0.2,   -0.5 ], // 2. Receptivas
  [  0.0,   0.0,    0.0,  -0.6,   1.5,   -0.3 ], // 3. Obsesión
  [  0.2,  -0.4,   -0.1,  -0.8,  -0.3,   -0.4 ], // 4. Independencia
  [ -0.4,  -0.4,   -0.4,  -0.4,  -0.4,    0.0 ]  // 5. Errantes

###### Intensidad y alcance de las relaciones:
Cada relación tiene una fuerza y una distancia diferentes (lógicamente como en la vida real)
Por ejemplo: La obsesión tiene el mayor alcance y la mayor fuerza para representar una persecución insistente
En cambio, el amor tiene una fuerza moderada para formar gurpis sin atraer a todas las partículas

let rMaxMatrix = [
  [ 55,  65,  50,  90,  50,  40 ], // Amor (Radio restaurado a 55 para permitir la unión natural)
  [ 65,  45,  60,  80,  40,  40 ], // Buscadoras
  [ 50,  60,  45,  80,  40,  40 ], // Receptivas
  [ 90,  80,  80, 110, 140,  60 ], // Obsesión
  [ 50,  40,  40, 110,  40,  40 ], // Independencia
  [ 40,  40,  40,  60,  40,  40 ]  // Aroace

Lo mismo para con distancias de interacción, ella solo interactúan cuando están dentro de cierta distancia

let dx = other.pos.x - this.pos.x;
let dy = other.pos.y - this.pos.y;

###### Fricción: Selecciona una fricción de 0.82 para que el movimiento fuera fluido y las partículas pudieran formar grupos sin moverse demasiado rápido

###### Velocidad máxima: 
Seleccioné una velocidad máxima de 3.5 para que las persecuciones fueran fáciles de observar y las partículas no atravesaran todo el sistema demasiado rápido, considere que fue un buen punto de velocidad

###### Apariencia e interacción:
Amor: un corazón porque representa el centro del sistema además es la representación clara del amor
Buscadoras: un triángulo porque transmite dirección y búsqueda, además de mostrar una diferencia entre las receptivas, un triángulo /= un círculo
Receptivas: un círculo por lo que menciona anteriormente, además en colores es lo opuesto de manera literal al color azul de las buscadoras
Obsesión: una esfera con púas para representar un vínculo dañino además de un tono verde para representar lo tóxico
Independencia: un círculo pequeño después de estar tan cerca de Obsesión, y rosado para que estuviera cerca del rojo del amor (ademas de que se notaba mas que el morado que tenia antes)
Errantes: un anillo blanco para mostrar que no participan de las dinámicas románticas, escogi el blanco porque es un color mas o menos neutro 

##### Versiones

<img width="920" height="617" alt="4e56f8cc-2734-48be-bffe-dbbb75267491" src="https://github.com/user-attachments/assets/186d8d12-2c5b-4e96-8e74-27dff8d90c35" />

<img width="996" height="636" alt="f1cae78e-059f-4266-bbac-03b3087a7d21" src="https://github.com/user-attachments/assets/74628266-b5f8-4bfe-9d8a-27966e378904" />

<img width="995" height="637" alt="86314faf-8de1-449c-b0a3-1106c1ad3988" src="https://github.com/user-attachments/assets/f501b8c8-646d-480a-831f-d1206b83e00f" />

<img width="992" height="635" alt="84e816ea-9e3e-4a2c-a73b-5586b32cf75d" src="https://github.com/user-attachments/assets/8c3cb6bb-f704-4491-84e3-b04975d561d4" />

<img width="993" height="633" alt="0464d5bc-c5ca-45fc-aaa0-410646ff4433" src="https://github.com/user-attachments/assets/91bc8fca-535b-45df-b1b6-3e4ba3b1d342" />

<img width="998" height="636" alt="c756267c-5f6d-49fe-970d-6c2c1dd069c7" src="https://github.com/user-attachments/assets/b6dbbdb2-a0ca-49c0-9101-437227623a7c" />

<img width="995" height="637" alt="2d867202-8f47-47ac-a37a-4e6c25976fb8" src="https://github.com/user-attachments/assets/e304c7ae-cef9-4dff-bae3-e9fbba7983e1" />


##### Codigo final:

```

```

##### URL 

##### AUTOEVALUACION


###### Evidencia


Influencia: El usuario puede colocar un cubo de azúcar en cualquier parte del escenario, cuando una hormiga encuentra el azúcar, regresa al hormiguero 
y aparecen hormigas recolectoras que siguen el rastro de feromonas hacia el azúcar, este evento también es posible si ningún usuario interactúa

2- He usado el random para el movimiento de las hormigas, el Lévy flight para que las hormigas les dé por dar un gran salto y aumentar su velocidad para ir a áreas que otras no han ido o incluso ir más lejos, también una distribución normal (gaussiana) para la velocidad y realizar cambios de dirección


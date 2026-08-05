## UNIDAD 2
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

Aqui es la primera formulacion de lo que queria, aparecieron estos bichitos que por muy bonitos que sean no mostraban el comportamiento que queria

<img width="996" height="636" alt="f1cae78e-059f-4266-bbac-03b3087a7d21" src="https://github.com/user-attachments/assets/74628266-b5f8-4bfe-9d8a-27966e378904" />

En esta otra foto habiamos avanzado pero las particulas se comenzaron a juntar es una gran particula ademas de quedarse estancadas en las esquinas que en ese entonces eran los limites (algo que tambien em habia medio pasado con las hormigas en su momento)

<img width="995" height="637" alt="86314faf-8de1-449c-b0a3-1106c1ad3988" src="https://github.com/user-attachments/assets/f501b8c8-646d-480a-831f-d1206b83e00f" />

Aqui ya habia un poquito mas de avance y ya habia comportamientos distinguibles de lo que habia planeado pero no me convencia aun

<img width="992" height="635" alt="84e816ea-9e3e-4a2c-a73b-5586b32cf75d" src="https://github.com/user-attachments/assets/8c3cb6bb-f704-4491-84e3-b04975d561d4" />

hice que el amor no se juntara tanto entre ellos porque a veces solia suceder que se juntaban entre si tanto tanto que volvia a formar una super particula de amor

<img width="993" height="633" alt="0464d5bc-c5ca-45fc-aaa0-410646ff4433" src="https://github.com/user-attachments/assets/91bc8fca-535b-45df-b1b6-3e4ba3b1d342" />

Problemas tecnicos otra vez de la super particula

<img width="998" height="636" alt="c756267c-5f6d-49fe-970d-6c2c1dd069c7" src="https://github.com/user-attachments/assets/b6dbbdb2-a0ca-49c0-9101-437227623a7c" />

Aqui ya añadi el cambio de diseño de unas particulas porque me parecio que añadia a la narrativa, aqui los cambios fueron minimos y habia cosas en el comportamietno de obsesion que aun no me convencia a mi misma

<img width="995" height="637" alt="2d867202-8f47-47ac-a37a-4e6c25976fb8" src="https://github.com/user-attachments/assets/e304c7ae-cef9-4dff-bae3-e9fbba7983e1" />

y asi quedo ya en su estado final ademas de añadir el loop en los limites para que siguieran fluyendo por ahi (aunque a veces se buguean)

##### Codigo final:

```
// Actividad 05: Particle Life Pro (Optimizado, con corazones juntos formando núcleos y receptivas rodeándolos)

let particles = [];
let grid = {};
let cellSize = 75; 

let typesConfig = [
  { name: "Amor", count: 120, color: "#FF5964" },
  { name: "Buscadoras", count: 90, color: "#0059ff" },
  { name: "Receptivas", count: 90, color: "#FFa600" },
  { name: "Obsesión", count: 35, color: "#61DE2A" },
  { name: "Independencia", count: 90, color: "#ff0a8a" },
  { name: "Errantes / Aroace", count: 80, color: "#FFFFFF" }
];

let matrix = [
  //  Amor,   Busc,  Recept, Obses, Indep, Aroace
  [  0.3,   0.4,    0.2,   0.1,   0.2,    0.1 ], // 0. Amor (Restaurado a 0.3 para que vuelvan a unirse y formar cúmulos)
  [  0.6,  -0.7,    0.8,  -0.1,  -0.3,   -0.5 ], // 1. Buscadoras
  [  0.1,  -0.9,    0.4,   0.0,  -0.2,   -0.5 ], // 2. Receptivas
  [  0.0,   0.0,    0.0,  -0.6,   1.5,   -0.3 ], // 3. Obsesión
  [  0.2,  -0.4,   -0.1,  -0.8,  -0.3,   -0.4 ], // 4. Independencia
  [ -0.4,  -0.4,   -0.4,  -0.4,  -0.4,    0.0 ]  // 5. Errantes/Aroace
];

let rMaxMatrix = [
  [ 55,  65,  50,  90,  50,  40 ], // Amor (Radio restaurado a 55 para permitir la unión natural)
  [ 65,  45,  60,  80,  40,  40 ], // Buscadoras
  [ 50,  60,  45,  80,  40,  40 ], // Receptivas
  [ 90,  80,  80, 110, 140,  60 ], // Obsesión
  [ 50,  40,  40, 110,  40,  40 ], // Independencia
  [ 40,  40,  40,  60,  40,  40 ]  // Aroace
];

let rMin = 18;      
let friction = 0.82; 
vMax = 3.5;

function setup() {
  createCanvas(800, 600);
  
  for (let t = 0; t < typesConfig.length; t++) {
    for (let i = 0; i < typesConfig[t].count; i++) {
      particles.push(new Particle(random(width), random(height), t));
    }
  }
}

function draw() {
  background(12, 12, 16, 220);

  // 1. Spatial Hash Grid (Limpieza optimizada)
  for (let key in grid) {
    grid[key] = [];
  }

  for (let i = 0; i < particles.length; i++) {
    let p = particles[i];
    let cx = floor(p.pos.x / cellSize);
    let cy = floor(p.pos.y / cellSize);
    let cellKey = cx + "," + cy;
    
    if (!grid[cellKey]) {
      grid[cellKey] = [];
    }
    grid[cellKey].push(p);
  }

  // 2. Calcular y actualizar
  for (let i = 0; i < particles.length; i++) {
    particles[i].calculateForces();
  }

  for (let i = 0; i < particles.length; i++) {
    particles[i].update();
    particles[i].display();
  }
}

class Particle {
  constructor(x, y, type) {
    this.pos = createVector(x, y);
    this.vel = createVector(random(-1, 1), random(-1, 1));
    this.acc = createVector(0, 0);
    this.type = type;
    this.color = color(typesConfig[type].color);
    this.noiseOffset = random(1000);
  }

  calculateForces() {
    let fx = 0;
    let fy = 0;

    fx += random(-0.015, 0.015);
    fy += random(-0.015, 0.015);

    if (this.type === 5) {
      let angle = noise(this.noiseOffset + millis() * 0.0004) * TWO_PI * 4;
      fx += cos(angle) * 0.4;
      fy += sin(angle) * 0.4;
    }

    let currentCx = floor(this.pos.x / cellSize);
    let currentCy = floor(this.pos.y / cellSize);

    for (let x = currentCx - 1; x <= currentCx + 1; x++) {
      for (let y = currentCy - 1; y <= currentCy + 1; y++) {
        let cellKey = x + "," + y;
        let cell = grid[cellKey];
        if (!cell) continue;

        for (let j = 0; j < cell.length; j++) {
          let other = cell[j];
          if (other === this) continue;

          let dx = other.pos.x - this.pos.x;
          let dy = other.pos.y - this.pos.y;
          
          if (abs(dx) > width / 2) dx = dx > 0 ? dx - width : dx + width;
          if (abs(dy) > height / 2) dy = dy > 0 ? dy - height : dy + height;

          let dSq = dx * dx + dy * dy;
          let rMax = rMaxMatrix[this.type][other.type];

          if (dSq > 0 && dSq < rMax * rMax) {
            let d = sqrt(dSq);
            let f = matrix[this.type][other.type];
            let forceMagnitude = 0;

            if (d < rMin) {
              forceMagnitude = (d / rMin - 1) * 3.5;
            } else {
              let percent = (d - rMin) / (rMax - rMin);
              forceMagnitude = f * sin(percent * PI);
            }

            fx += (dx / d) * forceMagnitude;
            fy += (dy / d) * forceMagnitude;
          }
        }
      }
    }

    this.acc.x += fx;
    this.acc.y += fy;
  }

  update() {
    this.vel.x += this.acc.x;
    this.vel.y += this.acc.y;
    this.vel.mult(friction);
    this.vel.limit(vMax);
    
    this.pos.add(this.vel);
    this.acc.set(0, 0);

    if (this.pos.x < 0) this.pos.x += width;
    if (this.pos.x > width) this.pos.x -= width;
    if (this.pos.y < 0) this.pos.y += height;
    if (this.pos.y > height) this.pos.y -= height;
  }

  display() {
    if (this.type === 0) {
      // Amor: Corazón grande
      noStroke();
      fill(this.color);
      push();
      translate(this.pos.x, this.pos.y);
      let s = 0.85;
      scale(s);
      triangle(-6, 0, 6, 0, 0, 9);
      ellipse(-3, -2, 6, 6);
      ellipse(3, -2, 6, 6);
      pop();
    } else if (this.type === 1) {
      // Buscadoras: Triángulo
      noStroke();
      fill(this.color);
      push();
      translate(this.pos.x, this.pos.y);
      triangle(0, -4.5, -4, 3.5, 4, 3.5);
      pop();
    } else if (this.type === 2) {
      // Receptivas: Círculo normal
      noStroke();
      fill(this.color);
      ellipse(this.pos.x, this.pos.y, 5);
    } else if (this.type === 3) {
      // Obsesión: Orbe grande con espinas triangulares
      noStroke();
      fill(this.color);
      push();
      translate(this.pos.x, this.pos.y);
      ellipse(0, 0, 10, 10);
      let numSpikes = 6;
      let rotAngle = millis() * 0.001;
      for (let i = 0; i < numSpikes; i++) {
        let angle = rotAngle + (TWO_PI / numSpikes) * i;
        push();
        rotate(angle);
        triangle(4, -1.5, 4, 1.5, 9, 0);
        pop();
      }
      pop();
    } else if (this.type === 4) {
      // Independencia: Círculo translúcido
      noStroke();
      let c = color(typesConfig[4].color);
      c.setAlpha(180);
      fill(c);
      ellipse(this.pos.x, this.pos.y, 4.5);
    } else if (this.type === 5) {
      // Errantes / Aroace: Círculo hueco (anillo)
      noStroke();
      noFill();
      stroke(this.color);
      strokeWeight(1.2);
      ellipse(this.pos.x, this.pos.y, 6);
    }
  }
}
```

##### URL 

https://editor.p5js.org/ManuBn777/sketches/fnUx554S5

##### AUTOEVALUACION
Criterio
La intención es clara y perceptible en el comportamiento.	20%		
Los tipos, cantidades, matriz y parámetros están justificados desde la intención.	25%		
Comprendo y puedo modificar el funcionamiento técnico del sistema.	20%		
El sistema produce variaciones con una identidad reconocible.	15%		
Experimenté, comparé, seleccioné y descarté con criterios claros.	10%		
Puedo distinguir y sustentar lo diseñado y lo emergente.	10%		
Total	100%		

###### Evidencia

- La intencion de las diferentes relaciones romanticas o no son percetibles en el comportamiento al menos desde mi punto de vista
- Eso lo explico en la parte de particulas mas arriba y que era lo que buscaba
- Si, creo que soy capaz si es necesario :D
- Las variaciones de como se forman circulos y persecusiones son diferentes en toda caso, ademas que el diseño que escogi para cada particula hace que resalten tanto por su actitud y forma/diseño
- Me pelee con la ia y conmigo misma, pero al final logre tener algo que me gusta y que esta dentro de los parametros de lo que me piden (espero)
- Si :D



## UNIDAD 1
### Actividad 7
#### Reto de diseño: Navegar la incertidumbre

##### Concepto:
posibilidad: Todas las hormigas salen del hormiguero, cada una realiza Traditional Random Walk, durante la exploración ellas dejan un rastro de feromonas que 
las hormigas suelen dejar que representa los caminos que pueden dejar el cual es totalmente libre


Tendencia: Después de un tiempo comienza a aparecer patrones, las feromonas de las hormigas hacen que ciertos caminos sean recorrido con mayor frecuencia


Normalidad: la mayoría de las hormigas presenta un comportamiento similar, explorar con velocidades cercanas al promedio y realizan pequeños cambios de 
dirección siguiendo una distribución normal (gaussiana)


Excepción: En ocasiones una hormiga realiza un Levy Flight, un desplazamiento mucho más largo y rápido que el resto, esto permite abandonar los caminos 
habituales y descubrir nuevas zonas del entorno


Influencia: El usuario puede colocar un cubo de azúcar en cualquier parte del escenario, cuando una hormiga encuentra el azúcar, regresa al hormiguero 
y aparecen hormigas recolectoras que siguen el rastro de feromonas hacia el azúcar, este evento también es posible si ningún usuario interactúa

#####Versiones

<img width="1142" height="870" alt="image" src="https://github.com/user-attachments/assets/184259d8-6a1f-46e9-bc2b-511b7b2553ef" />

Aqui podemos ver unos inicios del proyecto, por ahora estaba tratando de que funcionara lo basico como que las hormigas se movieran ademas del que hormiguero era un simple punto negro, casi un estilo demasiado minimalista, el problema que se juntaban como grupo de 5 o mas hormigas y se quedaban en un bucle girando unas con tras como manchas mas grandes

<img width="1600" height="1600" alt="89291107-bb82-4001-81a6-76ca19865cb7" src="https://github.com/user-attachments/assets/8ea2e293-12d6-4110-baef-f0bcb58a49ad" />

Entonces decidi hacer un diseño de como me gustaria ver el producto final, mostrando como los caminos como raices que crean las hormigas con feromonas ademas
de plantear como funcionaria los cubos de azucar y que estetica buscaba

<img width="537" height="162" alt="a57126f2-47cb-40c2-a20b-2c86cd74e120" src="https://github.com/user-attachments/assets/fa62dceb-24d4-4054-8389-83498ff50a3f" />
<img width="956" height="861" alt="332ceb76-bf01-45c3-aaa6-01bfb0af2eaf" src="https://github.com/user-attachments/assets/fec448a3-e622-4e13-84c2-31d12add4489" />

Logre tener la estetica que queria pero las hormigas comenzaron ir todas a la derecha asi que vi como arreglarlo con ayuda de la IA

<img width="956" height="857" alt="fd6c54c6-4168-471e-9ad1-820a22d3f542" src="https://github.com/user-attachments/assets/c9f3f487-a851-493e-ba57-97846cc57270" />

despues de un tiempo logre que siguera el concepto que tenia planteado, ademas de crear una hormiga que al detectar el eazucar iria hacia la colonia para avisar y las recolectoras...pero aun no funcionaba y tenia un color cafe no tan agradable asi que decidi cambiar el color tambien

<img width="1600" height="722" alt="6f066177-e86f-4e86-aad0-4ee7c39cf83d" src="https://github.com/user-attachments/assets/4692ffda-4ac7-4eae-9786-0fcaa8d88aa4" />

Aqui ya esta en una fase donde lo que tenian que hacer las hormigas lo hacen, ellas van por ahi ccreando caminos con sus feromonas (las cual hice que desaparecieran si eran muy antiguas para que no saturara la pantalla), ya esta la hormiga roja que es la que encuentra el azucar y al avisar en el hormiguero salen las 6 recolectoras para recoger un cubito de azucar hasta que desaparezca completamente
En terminos de estetica, las hormigas ya no son ovalos sino que ya tienen forma de hormiga, decidi tambien añadir rocas y tal vez charcos, los cuales no me convencieron entonces decidi quitarlos

<img width="1600" height="724" alt="d53cd7f6-313f-42ea-9413-b6a7d05b7031" src="https://github.com/user-attachments/assets/9a2bc274-c03c-4c65-8c13-a252845c8e0f" />
<img width="1600" height="727" alt="1a88bbd0-9dc8-462f-a9fb-9aadfb346c4e" src="https://github.com/user-attachments/assets/b7010e9e-b1d9-48df-9b9d-4508126512a1" />

Aqui ya esta terminado, decidi poner unos arbustos en los limites para visualizarlos mejor ademas de un difuminado en el suelo de claro a mas oscuro mientras mas lejos del hormiguero este

##### Codigo final:

```
/*
========================================================
THE NATURE OF CODE
Daniel Shiffman

Simulación:
Colonia de hormigas (Caminos dinámicos, azúcar automática, fondo degradado, bordes de bosque estrictamente en los límites y hormigas culonas rojizas oscuras)
========================================================
*/

//======================================================
// VARIABLES GLOBALES
//======================================================

let ants = [];
let pheromones = [];
let sugars = [];
let obstacles = [];
let nest;

let nestRadius = 45;
const MAX_ANTS = 50; 
const LEVY_PROBABILITY = 0.003;

let spawnTimer = 0;
const SPAWN_INTERVAL = 8;

let sugarTimer = 0;
const SUGAR_SPAWN_INTERVAL = 450;

// Configuración de obstáculos (Solo rocas)
const NUM_ROCKS = 6; 

//======================================================
// SETUP
//======================================================

function setup() {
    createCanvas(windowWidth, windowHeight);
    angleMode(RADIANS);
    nest = new Nest(width / 2, height / 2);
    generateObstacles();
}

function generateObstacles() {
    obstacles = [];
    
    // Crear Rocas (Cubos Grises)
    for (let i = 0; i < NUM_ROCKS; i++) {
        let rx, ry;
        let attempts = 0;
        do {
            rx = random(120, width - 120);
            ry = random(120, height - 120);
            attempts++;
        } while (dist(rx, ry, nest.position.x, nest.position.y) < 180 && attempts < 50);
        
        obstacles.push(new Obstacle(rx, ry, "rock", 28)); 
    }
}

//======================================================
// DRAW
//======================================================

function draw() {
    drawBackgroundAndForest();

    // Aparición automática de azúcar
    sugarTimer++;
    if (sugarTimer > SUGAR_SPAWN_INTERVAL && sugars.length < 3) {
        let randomX = random(120, width - 120);
        let randomY = random(120, height - 120);
        
        let d = dist(randomX, randomY, nest.position.x, nest.position.y);
        let valid = d > nestRadius + 100;
        
        for (let obs of obstacles) {
            if (dist(randomX, randomY, obs.position.x, obs.position.y) < obs.radius + 30) {
                valid = false;
            }
        }

        if (valid) {
            sugars.push(new Sugar(randomX, randomY));
            sugarTimer = 0;
        }
    }

    // Actualizar feromonas
    for (let i = pheromones.length - 1; i >= 0; i--) {
        pheromones[i].update();
        pheromones[i].display();
        if (pheromones[i].dead()) {
            pheromones.splice(i, 1);
        }
    }

    // Generar exploradoras base
    spawnTimer++;
    let explorerCount = ants.filter(a => a.role == "explorer" || a.role == "scout").length;
    if (spawnTimer > SPAWN_INTERVAL && explorerCount < MAX_ANTS) {
        ants.push(new Ant("explorer"));
        spawnTimer = 0;
    }

    // Dibujar obstáculos
    for (let obs of obstacles) {
        obs.display();
    }

    // Dibujar azúcar
    for (let sugar of sugars) {
        sugar.display();
    }

    // Dibujar hormiguero
    nest.display();

    // Actualizar y eliminar hormigas recolectoras
    for (let i = ants.length - 1; i >= 0; i--) {
        let ant = ants[i];
        ant.update();
        ant.display();

        if (ant.role == "collector" && (!ant.foodTarget || ant.foodTarget.empty())) {
            ants.splice(i, 1);
        }
    }
}

//======================================================
// FONDO CON DEGRADADO Y BORDES DE BOSQUE (Estrictamente en los límites)
//======================================================

function drawBackgroundAndForest() {
    background(112, 143, 54);
    
    // Viñeta radial sutil para oscurecer los bordes
    push();
    noFill();
    let maxDist = dist(0, 0, width / 2, height / 2);
    let steps = 15;
    for (let i = steps; i > 0; i--) {
        let currentR = map(i, 0, steps, maxDist * 0.4, maxDist * 1.2);
        let alpha = map(i, 0, steps, 0, 110);
        stroke(55, 78, 25, alpha);
        strokeWeight(maxDist / steps);
        ellipse(width / 2, height / 2, currentR * 2);
    }
    pop();

    // Patrón de secuencia exacta: [Pequeña, Mediana, Pequeña, Grande, Grande]
    let patternSizes = [22, 34, 24, 48, 52];

    push();
    noStroke();
    
    // Función para dibujar una línea de arbustos exactamente en un borde exterior
    let drawBorderLine = (startX, startY, stepX, stepY, limit) => {
        let index = 0;
        let x = startX;
        let y = startY;

        while (true) {
            if (stepX > 0 && x > limit) break;
            if (stepX < 0 && x < limit) break;
            if (stepY > 0 && y > limit) break;
            if (stepY < 0 && y < limit) break;

            let s = patternSizes[index % patternSizes.length];
            
            // Capas de los arbustos ceñidas al borde
            fill(45, 68, 20, 230);
            circle(x, y, s * 1.2);
            
            fill(60, 88, 28, 210);
            circle(x + (stepY !== 0 ? 8 : 0), y + (stepX !== 0 ? 8 : 0), s * 0.8);

            x += stepX;
            y += stepY;
            index++;
        }
    };

    let spacing = 22;

    // Borde Superior (pegado arriba: y = 12)
    drawBorderLine(-20, 12, spacing, 0, width + 20);
    // Borde Inferior (pegado abajo: y = height - 12)
    drawBorderLine(-20, height - 12, spacing, 0, width + 20);
    // Borde Izquierdo (pegado a la izquierda: x = 12)
    drawBorderLine(12, -20, 0, spacing, height + 20);
    // Borde Derecho (pegado a la derecha: x = width - 12)
    drawBorderLine(width - 12, -20, 0, spacing, height + 20);

    pop();
}

//======================================================
// RESPONSIVE E INTERACCIÓN
//======================================================

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
    nest.position.set(width / 2, height / 2);
}

function mousePressed() {
    let d = dist(mouseX, mouseY, nest.position.x, nest.position.y);
    if (d > nestRadius) {
        let valid = true;
        for (let obs of obstacles) {
            if (dist(mouseX, mouseY, obs.position.x, obs.position.y) < obs.radius + 15) {
                valid = false;
            }
        }
        if (valid) {
            let newSugar = new Sugar(mouseX, mouseY);
            sugars.push(newSugar);
            sugarTimer = 0;
        }
    }
}

//======================================================
// CLASE OBSTÁCULO (Roca Cúbica)
//======================================================

class Obstacle {
    constructor(x, y, type, radius) {
        this.position = createVector(x, y);
        this.type = type; 
        this.radius = radius; 
        this.angle = random(TWO_PI); 
    }

    display() {
        push();
        translate(this.position.x, this.position.y);
        rotate(this.angle);
        rectMode(CENTER);
        noStroke();

        fill(110, 110, 110);
        square(0, 0, this.radius * 1.8);
        fill(90, 90, 90);
        square(-this.radius * 0.3, -this.radius * 0.2, this.radius * 0.8);
        pop();
    }
}

//======================================================
// CLASE HORMIGUERO
//======================================================

class Nest {
    constructor(x, y) {
        this.position = createVector(x, y);
    }

    display() {
        push();
        translate(this.position.x, this.position.y);
        noStroke();
        fill(145, 91, 57);
        circle(0, 0, 90);
        fill(110, 67, 45);
        circle(0, 0, 65);
        fill(82, 48, 35);
        circle(0, 0, 45);
        fill(40, 25, 20);
        circle(0, 0, 22);
        pop();
    }
}

//======================================================
// CLASE HORMIGA
//======================================================

function angleDifference(a, b) {
    let diff = b - a;
    while (diff > PI) diff -= TWO_PI;
    while (diff < -PI) diff += TWO_PI;
    return diff;
}

class Ant {
    constructor(role, targetSugar = null) {
        this.position = nest.position.copy();
        this.angle = random(TWO_PI);
        this.velocity = p5.Vector.fromAngle(this.angle);
        
        this.speed = randomGaussian(1.6, 0.15);
        this.noiseOffset = random(1000);
        
        this.role = role; 
        this.foodTarget = targetSugar;
        this.hasSugar = false;
        this.maxDistance = randomGaussian(450, 100);
        this.restFrames = 0;

        if (this.role == "collector") {
            this.state = "collecting";
            this.angle = p5.Vector.sub(this.foodTarget.position, this.position).heading();
        } else {
            this.state = "exploring";
        }

        this.isLevy = false;
        this.levyFrames = 0;
    }

    startLevy() {
        this.isLevy = true;
        this.levyFrames = floor(random(25, 50));
        this.angle += random(-PI, PI);
    }

    goHome() {
        this.state = "returning";
        this.isLevy = false;
    }

    spawnCollectors(sugar) {
        for (let i = 0; i < 6; i++) {
            ants.push(new Ant("collector", sugar));
        }
    }

    updateState() {
        let d = p5.Vector.dist(this.position, nest.position);

        if (this.state == "exploring") {
            if (this.role == "explorer" && d > this.maxDistance) {
                this.goHome();
            }
        } 
        else if (this.state == "returning") {
            if (d < 18) {
                if (this.role == "scout" && this.foodTarget) {
                    this.spawnCollectors(this.foodTarget);
                    this.role = "explorer";
                }

                this.hasSugar = false;
                
                if (this.role == "collector" && this.foodTarget && !this.foodTarget.empty()) {
                    this.state = "collecting";
                } else {
                    this.state = "rest";
                    this.restFrames = 30;
                }
            }
        } 
        else if (this.state == "rest") {
            this.restFrames--;
            if (this.restFrames <= 0) {
                this.state = "exploring";
                this.role = "explorer";
                this.foodTarget = null;
                this.maxDistance = randomGaussian(500, 120);
                this.angle = random(TWO_PI);
            }
        }
        else if (this.state == "collecting") {
            if (!this.foodTarget || this.foodTarget.empty()) {
                return;
            }

            let distToSugar = p5.Vector.dist(this.position, this.foodTarget.position);
            if (distToSugar < this.foodTarget.radius + 6) {
                if (this.foodTarget.takeCrystal()) {
                    this.hasSugar = true;
                    this.goHome();
                }
            }
        }
    }

    update() {
        this.updateState();

        if (!this.isLevy && this.state == "exploring" && this.role == "explorer") {
            if (random() < LEVY_PROBABILITY) {
                this.startLevy();
            }
        }

        let targetAngle = this.angle;

        if (this.state == "exploring") {
            let randomTurn = randomGaussian(0, 0.22);
            let noiseTurn = map(noise(this.noiseOffset), 0, 1, -0.1, 0.1);
            this.noiseOffset += 0.01;
            this.angle += randomTurn + noiseTurn;
        } 
        else if (this.state == "collecting") {
            if (this.foodTarget && !this.foodTarget.empty()) {
                let desired = p5.Vector.sub(this.foodTarget.position, this.position);
                targetAngle = desired.heading();
                
                let noiseTurn = map(noise(this.noiseOffset), 0, 1, -0.35, 0.35);
                this.noiseOffset += 0.02;
                
                let diff = angleDifference(this.angle, targetAngle);
                this.angle += constrain(diff * 0.08, -0.05, 0.05) + noiseTurn * 0.15;
            }
        } 
        else if (this.state == "returning") {
            let desired = p5.Vector.sub(nest.position, this.position);
            targetAngle = desired.heading();
            
            let noiseTurn = map(noise(this.noiseOffset), 0, 1, -0.35, 0.35);
            this.noiseOffset += 0.02;
            
            let diff = angleDifference(this.angle, targetAngle);
            this.angle += constrain(diff * 0.08, -0.05, 0.05) + noiseTurn * 0.15;
        }

        // EVITACIÓN DE OBSTÁCULOS
        for (let obs of obstacles) {
            let d = p5.Vector.dist(this.position, obs.position);
            if (d < obs.radius + 20) {
                let awayAngle = p5.Vector.sub(this.position, obs.position).heading();
                let diff = angleDifference(this.angle, awayAngle);
                this.angle += (diff > 0 ? 0.18 : -0.18);
            }
        }

        this.velocity = p5.Vector.fromAngle(this.angle);

        if (this.isLevy) {
            this.velocity.setMag(4.2);
            this.levyFrames--;
            if (this.levyFrames <= 0) {
                this.isLevy = false;
            }
        } else {
            this.velocity.setMag(this.speed);
        }

        if (this.state != "rest") {
            this.position.add(this.velocity);
        }

        if (!this.hasSugar && this.state == "exploring" && this.role == "explorer") {
            for (let i = sugars.length - 1; i >= 0; i--) {
                let sugar = sugars[i];
                let d = p5.Vector.dist(this.position, sugar.position);

                if (d < sugar.radius + 10) {
                    if (sugar.takeCrystal()) {
                        this.hasSugar = true;
                        this.foodTarget = sugar;

                        if (!sugar.discovered) {
                            sugar.discovered = true;
                            sugar.scout = this;
                            this.role = "scout";
                        }

                        this.goHome();
                    }

                    if (sugar.empty()) {
                        sugars.splice(i, 1);
                    }
                    break;
                }
            }
        }

        // GESTIÓN DE FEROMONAS
        let dropInterval = (this.role == "explorer") ? 4 : 6;
        if (frameCount % dropInterval == 0 && this.state != "rest") {
            let type = "";
            let strength = 1;

            if (this.role == "scout" && this.hasSugar) {
                type = "scout_trail";
                strength = 3.5;
                pheromones.push(new Pheromone(this.position.x, this.position.y, strength, type, this.foodTarget));
            } else if (this.role == "explorer") {
                type = "explore";
                strength = 1.35;
                pheromones.push(new Pheromone(this.position.x, this.position.y, strength, type, this.foodTarget));
            } else if (this.role == "collector") {
                type = "collector_trail";
                strength = 2.0;
                pheromones.push(new Pheromone(this.position.x, this.position.y, strength, type, this.foodTarget));
            }
        }

        // LÍMITES DE PANTALLA
        let margin = 35;
        if (this.position.x < margin) {
            this.angle = PI - this.angle + random(-0.2, 0.2);
            this.position.x = margin;
        } else if (this.position.x > width - margin) {
            this.angle = PI - this.angle + random(-0.2, 0.2);
            this.position.x = width - margin;
        }
        if (this.position.y < margin) {
            this.angle = -this.angle + random(-0.2, 0.2);
            this.position.y = margin;
        } else if (this.position.y > height - margin) {
            this.angle = -this.angle + random(-0.2, 0.2);
            this.position.y = height - margin;
        }
    }

    display() {
        push();
        translate(this.position.x, this.position.y);
        rotate(this.angle);
        noStroke();

        if (this.role == "scout") {
            fill(210, 40, 40); 
        } else if (this.role == "collector") {
            fill(139, 53, 33); 
        } else if (this.isLevy) {
            fill(70, 30, 25);
        } else {
            // Tono rojizo oscuro característico de las hormigas culonas (Atta laevigata)
            fill(85, 32, 25); 
        }

        // Abdomen
        ellipse(-6, 0, 9, 6);
        // Tórax
        ellipse(0, 0, 6, 4.5);
        // Cabeza
        ellipse(5, 0, 5, 4);

        if (this.hasSugar) {
            fill(255, 255, 245);
            rectMode(CENTER);
            square(0, -5, 4);
        }

        stroke(60, 22, 18, 150);
        strokeWeight(0.8);
        line(6, -1.5, 9, -4);
        line(6, 1.5, 9, 4);

        pop();
    }
}

//======================================================
// FEROMONA Y AZÚCAR
//======================================================

class Pheromone {
    constructor(x, y, strength, type = "explore", sugarRef = null) {
        this.position = createVector(x, y);
        this.life = 255;
        this.strength = strength;
        this.type = type;
        this.sugarRef = sugarRef;
        this.size = 7.5;
    }

    update() {
        if (this.type == "scout_trail") {
            if (!this.sugarRef || this.sugarRef.empty()) {
                this.life -= 4.5;
            } else {
                this.life -= 0.35;
            }
        } else if (this.type == "collector_trail") {
            if (!this.sugarRef || this.sugarRef.empty()) {
                this.life -= 3.0;
            } else {
                this.life -= 0.45;
            }
        } else {
            this.life -= 0.35 * this.strength;
        }
    }

    display() {
        push();
        noStroke();
        
        let alphaFactor = this.life / 255;

        if (this.type == "scout_trail") {
            fill(160, 115, 88, this.life * 0.55);
        } else if (this.type == "collector_trail") {
            fill(150, 155, 95, this.life * 0.5);
        } else {
            fill(194, 150, 118, this.life * 0.6);
        }

        let currentSize = this.size * this.strength * constrain(alphaFactor * 1.2, 0.4, 1.0);

        ellipse(this.position.x, this.position.y, currentSize, currentSize * 0.9);
        pop();
    }

    dead() {
        return this.life <= 0;
    }
}

class Sugar {
    constructor(x, y) {
        this.position = createVector(x, y);
        this.crystals = [];
        this.radius = 18;
        this.discovered = false;
        this.scout = null;

        for (let i = 0; i < 60; i++) {
            let a = random(TWO_PI);
            let r = sqrt(random()) * this.radius;
            this.crystals.push({
                x: cos(a) * r,
                y: sin(a) * r,
                size: random(3, 5),
                angle: random(TWO_PI)
            });
        }
    }

    display() {
        push();
        translate(this.position.x, this.position.y);
        rectMode(CENTER);
        noStroke();
        for (let c of this.crystals) {
            push();
            translate(c.x, c.y);
            rotate(c.angle);
            fill(255, 255, 248);
            square(0, 0, c.size);
            pop();
        }
        pop();
    }

    takeCrystal() {
        if (this.crystals.length > 0) {
            this.crystals.pop();
            return true;
        }
        return false;
    }

    empty() {
        return this.crystals.length == 0;
    }
}
```

##### URL 
http://127.0.0.1:5500/

##### AUTOEVALUACION

Criterio	                                                                         CUMPLO NO CUMPLO
- Encargo completo: interpreto los cinco momentos dentro de un mismo sistema visual.	☐	    ☐	

- Simulación con intención: utilizo al menos tres conceptos de la unidad para 
comunicar las ideas del encargo.	                                                    ☐  	☐	

- Interacción significativa: la interacción modifica el comportamiento o las
probabilidades del sistema, que también funciona sin intervención.                  	☐	    ☐	

- Prototipo funcional: la experiencia puede ejecutarse y recorrerse completa 
sin errores que impidan comprenderla.                                               	☐	    ☐	

- Proceso documentado: la bitácora evidencia avances, decisiones, dificultades, 
soluciones, uso de IA y enlace al prototipo.                                        	☐	    ☐




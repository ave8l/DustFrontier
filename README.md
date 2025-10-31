# DustFrontier 🤠
Juego de simulación creado en **Python** inspirado en *Dwarf Fortress* con características del Salvaje Oeste.  
Creado con intención de aplicar los conocimientos adquiridos en la materia **Estructura de Datos y Algoritmos**, aprovechando el enfoque del juego para poner en práctica conceptos de programación avanzada.

---

## 💻 Propósito
El proyecto funciona como recurso educativo para mejorar la comprensión y aplicación de:
- **Estructuras de datos** y **algoritmos.**
- **Programación Orientada a Objetos (POO)**, aplicando conceptos como **polimorfismo**, **herencia** y **encapsulamiento.**
- Uso de librerías externas como **pygame**.
- Trabajo en equipo y asignación de roles dentro del desarrollo de un videojuego.

Es un enfoque que va más allá de lo monótono de un proyecto común, siendo una experiencia práctica, divertida y didáctica de todo lo visto durante el semestre.

---

## 🧱 Características

### POO // DANIEL 🧩
La **Programación Orientada a Objetos (POO)** es el núcleo del proyecto.  
Cada entidad del mundo del juego (personajes, fauna, edificios, recursos, etc.) se modela como un **objeto**, permitiendo estructurar el código de manera modular y reutilizable.

**Principios aplicados:**
- **Herencia:** las clases derivadas extienden comportamientos base (por ejemplo, `Cantina` hereda de `Edificio` o `Vaquero` de `Personaje`).
- **Polimorfismo:** los métodos compartidos se comportan diferente según la clase (por ejemplo, cada personaje o animal tiene su propio `update()`).
- **Encapsulamiento:** los atributos internos (salud, hambre, progreso de construcción, etc.) se controlan dentro de cada clase.

Gracias a la POO, el código es **más limpio, escalable y fácil de mantener**.

---

### POO 💡

#### **📦 classes.py**
Núcleo estructural del sistema. Define:
- `Animal`: movimiento, envejecimiento y renderizado.  
- `FaunaSilvestre`: añade desplazamiento hacia objetivos.  
- `Personaje`: agrega aptitudes, inventario y necesidades.  
- `Accion` y `Tarea`: base del sistema de IA y automatización de acciones.  

#### **👤 characters.py**
Define los **personajes humanos** y la **fauna**:
- Humanos: *Vaquero*, *Cazador*, *Pionero*, *Médico*.  
- Fauna pasiva (*Pollo, Oveja, Vaca, Zancudo*) y agresiva (*Oso, Lobo*).  
Incluye `cargar_imagenes_personaje()` para cargar y escalar sprites en las cuatro direcciones.

#### **🏠 edificios.py**
Modela estructuras del entorno:
- `Edificio`: clase base con progreso de construcción, ocupantes y posición.  
- `Cantina`: edificio derivado con imágenes escaladas (100×100 px) y función de descanso para personajes.  

#### **🏕️ colonia.py**
Coordina el estado global de la simulación mediante la clase `Colonia`:
- Gestiona recursos, entidades y tareas.  
- Usa grupos de `pygame.sprite.Group` para mantener actualizadas las entidades en pantalla.  

#### **⚒️ instances.py**
Centraliza las **acciones del juego** (construir, cazar, descansar, etc.):  
- Define instancias concretas de `Accion` y `Tarea`.  
- Las agrupa en `ACCIONES_ESTANDARES`, usadas por la interfaz y la lógica.  

#### **⚙️ utils.py**
Motor lógico del sistema:  
- Procesa tareas (`procesar_tarea`, `procesar_tarea_caza`).  
- Asigna acciones automáticas (`buscar_y_asignar_tarea`).  
- Actualiza la simulación por fotograma (`simular_tick`).  
- Controla eventos aleatorios (`check_random_events`).  

#### **🖥️ ui.py**
Gestiona la interfaz gráfica mediante `UIManager`:  
- Dibuja recursos, paneles y botones.  
- Detecta clics del jugador (`verificar_click_accion`) y los traduce en tareas del sistema.

📚 **Resumen:**  
- `classes.py` define la base.  
- `characters.py` y `edificios.py` amplían entidades.  
- `colonia.py` coordina la simulación.  
- `instances.py` define las acciones.  
- `utils.py` ejecuta la lógica.  
- `ui.py` conecta la interfaz con el jugador.  

---

### Mapa 🗺️
El mapa se genera mediante la técnica **“handcrafted procedural”**, donde se combinan funciones matemáticas y reglas explícitas para crear terrenos variados.

- **Procedural:** generado por un algoritmo en lugar de un dibujo manual.  
- **Handcrafted:** diseñado mediante fórmulas matemáticas y parámetros como radios, centros y máscaras elípticas.

Se usan curvas seno, radios y máscaras para generar montañas, pantanos, océanos y campos.

#### **MAPA GENERADO:**  
*(Insertar imagen del mapa aquí)*

---
### HEAP Y COMO AFECTA A LOS PERSONAJES Y SUS TAREAS ADALBERTO-------------------------------------------------------------

### pygame 👾
Se usa la biblioteca **pygame** para manejar:
- Renderizado de imágenes, figuras y texto.  
- Detección de interacción del usuario.  
- Control del tiempo y FPS.  
- Reproducción de sonidos o música.  

También gestiona colisiones y condiciones como `walkable`, para determinar si el personaje puede desplazarse por una zona específica.

#### 🧩 Instalación de Pygame
Para ejecutar el proyecto correctamente, asegúrate de tener **Python 3.10+** y luego instala `pygame` con el siguiente comando:

```bash
pip install pygame


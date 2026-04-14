![[1_poo_1.png]]


# 5_Clases (plano)
son los planos del objeto el molde si fuera un balón tendríamos todo lo que hace posible fabricar este balón dentro de esta clase  
```java
// Esta es la CLASE (el molde)
class Auto {
    
    /* todo lo que este dentro de las llavez es lo que le va dando caracteristicas al objeto con atributos y metooso y muchas mas cosas */	   
}

```
# 6_ Objeto (instancia)
es la clase cobrando vida si fuera un balón bueno ese balo seria el objeto ya fabricado para llamarlo en este caso en JAVA se usa 
```java
class Venta{
	/*despues de crear un una clase o el molde podemos llamar a la clase principal */
	Auto miCoche = new Auto();
}
```
# 7_Atributos y Métodos 
## Atributos (¿que es?) 
son las variable que guardan información pero que a su vez es una descripción de ese balón como la variable  ```coloBalon```,   ```formaBalon```, ```logoBalon```
```java
class Auto{
	String color;
	String marca;
	}
```
## Métodos (¿que hace?)
son las funciones que el objeto puede realizar o acciones como ```rebotar()```, ```inyectarAire()``` 
```java
class Auto{
	/*De esta manera podemos poner metodos funciones etc*/
	void arrancar() {
	    System.out.println("El auto está en marcha...");
	}
```
	
## Encapsulamiento (escudo de los datos)
en nuestros objetos no queremos que nadie cambie cosas importantes de los atributos osea que nadie pueda llegar un cambiarlo por un error o por maldad un dato, que podrían cambiar en el balón tendríamos ```colorBalon``` si esta en fabricación por 3 días pero en el día 2 lo modifican la producción sale mal   

# 8_Herencia: La Relación "Es Un" [[1_poo.pdf#search=A. Introducción a la Herencia|1_poo, p.6]]

La herencia permite que una **Subclase** (hija) herede atributos y comportamientos de una **Superclase** (padre).

- **¿Para qué sirve?** Para **reutilizar código**. No escribes lo mismo diez veces; lo escribes una vez en el padre y todos los hijos lo tienen.
- **Ejemplo Real:** Si tienes la clase `Empleado`, todos tienen `nombre` y `ID`. El `Gerente` y el `Operario` **heredan** eso, pero el `Gerente` puede tener un atributo extra como `bonoLogros`  en otras palabras gracias a la herencia podemos reutilizar y optimizar el código
- **Regla de Oro:** Solo usa herencia si puedes decir "El B es un A". (Un Perro **es un** Animal).
### Ejemplo de Herencia en Java
Imagina que tenemos una clase padre llamada `Empleado` (el ADN base) y una clase hija llamada `Gerente` (la especialización).
```java	
	// 1. Clase Padre (Superclase)
class Empleado {
    String nombre;
    double salarioBase;

    // Método que heredarán todos
    void mostrarInformacion() {
        System.out.println("Empleado: " + nombre + " | Salario: $" + salarioBase);
    }
}

// 2. Clase Hija (Subclase) usando 'extends'
class Gerente extends Empleado {
    double bono;

    // Método específico de Gerente
    void administrar() {
        System.out.println(nombre + " está coordinando al equipo...");
    }
}

// 3. Ejecución (El mundo real)
public class Main {
    public static void main(String[] args) {
        // Creamos un objeto de la clase hija
        Gerente miJefe = new Gerente();
        
        // ¡Atención! 'nombre' y 'salarioBase' no están en Gerente, 
        // pero los puede usar porque los HEREDÓ de Empleado.
        miJefe.nombre = "Ana Martínez";
        miJefe.salarioBase = 3500.0;
        miJefe.bono = 500.0;

        miJefe.mostrarInformacion(); // Método heredado
        miJefe.administrar();        // Método propio
    }
}
```

# 9_Polimorfismo: "Muchas Formas" [[1_poo.pdf#search=B. Concepto de Polimorfismo Básico|1_poo, p.6]]

Es la capacidad de un objeto de responder de forma distinta a una misma instrucción. Se logra principalmente mediante la **Sobrescritura de métodos (Overriding)**

- **El concepto:** Imagina que el jefe dice "¡Trabajen!". El programador escribe código, el contador suma números y el diseñador dibuja. La orden es la misma, pero la ejecución depende de **quién** es el objeto.
- **En código:** La clase `Empleado` tiene el método `calcularSalario()`.
    - El `Gerente` lo sobrescribe para sumar bonos.
    - El `Operario` lo sobrescribe para restar deducciones.
    - Tú solo llamas a `empleado.calcularSalario()` y el sistema decide automáticamente cuál usar.

En el ejemplo anterior, todos los empleados tenían un método `mostrarInformacion()`. Pero, ¿qué pasa si el Gerente necesita mostrar algo más (como su bono) que un empleado común no tiene?

Aquí entra la **Sobrescritura de Métodos (`@Override`)**:

1. **La Orden Única:** El sistema principal da una orden genérica: _"¡Todos los empleados, calculen su salario!"_.
2. **La Respuesta Individual:**
    - El **Empleado** común responde: "Mi salario es mi sueldo base".
    - El **Gerente** responde: "Mi salario es mi sueldo base **MÁS** mi bono".
	```java
	class Empleado {
	    double salarioBase = 2000;
	
	    // Método genérico
	    double calcularSalario() {
	        return salarioBase;
	    }
	}
	
	class Gerente extends Empleado {
	    double bono = 500;
	
	    // ¡POLIMORFISMO EN ACCIÓN! 
	    // Redefinimos el comportamiento para el Gerente
	    @Override
	    double calcularSalario() {
	        return salarioBase + bono;
	    }
	}
	```

Polimorfismo es heredar métodos  pero no se puede cambiar el nombre al método en la clase heredada en la clase hija, el Polimorfismo (específicamente la **Sobrescritura** o _Overriding_) sirve para **cambiar la lógica (el código)** dentro del método, manteniendo el mismo nombre.
- **adre (Animal):** `hacerSonido()` -> Código: `System.out.println("Sonido genérico");`
- **Hijo (Perro):** `hacerSonido()` -> Código: `System.out.println("Guau!");`
- **Hijo (Gato):** `hacerSonido()` -> Código: `System.out.println("Miau!");`
con los atributos no es buena practica hacerlo 
# 10_Relaciones entre Clases [[1_poo.pdf#search=C. Relaciones entre Clases|1_poo, p.6]]

No todo es herencia. A veces las clases simplemente se conocen o se necesitan. Según tus apuntes, hay tres niveles de "amistad" entre objetos:

| Relación        | Concepto                        | Fuerza | Ejemplo                                                                                                            |
| --------------- | ------------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------ |
| **Asociación**  | "Tiene un". Son independientes. | Débil  | Un `Profesor` tiene un `Curso`. Si el curso acaba, el profesor sigue existiendo                                    |
| **Agregación**  | Relación Todo-Parte.            | Media  | Un `Equipo` tiene `Jugadores`. Si el equipo desaparece, los jugadores pueden irse a otro                           |
| **Composición** | Relación de vida o muerte.      | Fuerte | Una `Oficina` tiene una `Dirección`. Si destruyes la oficina en el sistema, la dirección ya no tiene sentido sola  |
1. **Asociación: "La Amistad" (Relación Débil)**
	Es una conexión simple donde dos clases se conocen y se comunican, pero **cada una tiene su propia vida**.
	
	- **La Analogía:** Un **Médico** y un **Paciente**. El médico atiende a muchos pacientes, y el paciente ve a varios médicos. Si el médico se jubila, el paciente sigue existiendo. Si el paciente se muda, el médico sigue trabajando.
	- **En el Código:** Una clase tiene una variable que hace referencia a la otra.
	- **Multiplicidad:** Puede ser 1 a 1, 1 a muchos, o muchos a muchos (como un profesor y sus alumnos).
		```java
		// Clase Paciente: Existe de forma independiente
		class Paciente {
		    private String nombre;
		
		    public Paciente(String nombre) {
		        this.nombre = nombre;
		    }
		
		    public String getNombre() {
		        return nombre;
		    }
		}
		
		// Clase Medico: También existe de forma independiente
		class Medico {
		    private String nombre;
		
		    public Medico(String nombre) {
		        this.nombre = nombre;
		    }
		
		    // Aquí está la ASOCIACIÓN:
		    // El médico recibe a un paciente para una consulta específica
		    public void atender(Paciente pacienteAtendido) {
		        System.out.println("El Dr. " + this.nombre + " está atendiendo a: " + pacienteAtendido.getNombre());
		    }
		}
		
		// --- CLASE PRINCIPAL ---
		public class Hospital {
		    public static void main(String[] args) {
		        // Creamos los objetos por separado
		        Medico doctorHouse = new Medico("Gregory House");
		        Paciente pacienteWill = new Paciente("Will Smith");
		
		        // Los asociamos en una acción (la consulta)
		        doctorHouse.atender(pacienteWill);
		
		        // Prueba de independencia:
		        // Si borramos al doctor estableciéndolo como nulo...
		        doctorHouse = null;
		
		        // ¡El paciente sigue existiendo en el sistema!
		        System.out.println("El doctor ya no está, pero el paciente sigue siendo: " + pacienteWill.getNombre());
		    }
		}

		```

	Por qué esto es Asociación:
	
	1. **Independencia:** El objeto `pacienteWill` se creó en el `main`, no dentro del constructor del `Medico`. El médico no es "dueño" del paciente.
	2. **Comunicación:** El médico usa al paciente solo cuando lo necesita (en el método `atender`).
	3. **Multiplicidad:** En este ejemplo es 1 a 1, pero si el médico tuviera un `ArrayList<Paciente>`, sería una asociación de **1 a muchos**.
	
	Esta relación es la más común porque permite que tu código sea flexible. Los objetos colaboran pero no están "atados" de por vida.
	
2. **Agregación: "El Equipo" (Relación Media)**

	Es una relación de tipo **"tiene un"** o **"forma parte de"**. Una clase es un "contenedor" de otras, pero las partes pueden existir fuera de ese contenedor.
	
	- **La Analogía:** Un **Equipo de Fútbol** y sus **Jugadores**. El equipo _agrupa_ a los jugadores. Si el club desaparece (la clase equipo se destruye), los jugadores no desaparecen; simplemente se van a otro equipo.
	- **Diferencia clave:** El "todo" (equipo) necesita a las "partes" (jugadores) para funcionar, pero no es su dueño absoluto.
	
		```java
		import java.util.ArrayList;
		import java.util.List;
		
		// La "Parte": Existe por sí sola
		class Jugador {
		    private String nombre;
		
		    public Jugador(String nombre) {
		        this.nombre = nombre;
		    }
		
		    public String getNombre() { return nombre; }
		}
		
		// El "Todo" (Contenedor): Agrupa a las partes
		class Equipo {
		    private String nombreEquipo;
		    private List<Jugador> jugadores; // Agregación: El equipo TIENE jugadores
		
		    public Equipo(String nombreEquipo) {
		        this.nombreEquipo = nombreEquipo;
		        this.jugadores = new ArrayList<>();
		    }
		
		    // Método para agregar jugadores al equipo
		    public void contratar(Jugador j) {
		        jugadores.add(j);
		    }
		
		    public void mostrarPlantilla() {
		        System.out.println("Equipo: " + nombreEquipo);
		        for (Jugador j : jugadores) {
		            System.out.println("- " + j.getNombre());
		        }
		    }
		}
		
		// --- CLASE PRINCIPAL ---
		public class Main {
		    public static void main(String[] args) {
		        // 1. Creamos a los jugadores PRIMERO (independientes)
		        Jugador p1 = new Jugador("Lionel Messi");
		        Jugador p2 = new Jugador("Cristiano Ronaldo");
		
		        // 2. Creamos el equipo
		        Equipo dreamTeam = new Equipo("Galácticos FC");
		
		        // 3. AGREGAMOS los jugadores al equipo
		        dreamTeam.contratar(p1);
		        dreamTeam.contratar(p2);
		
		        dreamTeam.mostrarPlantilla();
		
		        // 4. PRUEBA DE FUEGO: ¿Qué pasa si el equipo desaparece?
		        System.out.println("\n--- El equipo se disuelve ---");
		        dreamTeam = null; 
		
		        // Los jugadores SIGUEN VIVOS en la memoria porque fueron creados fuera
		        System.out.println("El equipo ya no existe, pero el jugador sigue vivo: " + p1.getNombre());
		    }
		}

		```

	- **Sentido de Pertenencia:** En la _Asociación_ (Médico-Paciente) era un encuentro casual en un método. En la **Agregación**, el objeto `Jugador` se vuelve parte de un atributo (`List<Jugador>`) del `Equipo`. El equipo "contiene" a los jugadores.
	- **Ciclo de Vida:** Los objetos se pasan por referencia al constructor o a un método (como `contratar`). El `Equipo` no creó a los jugadores con un `new Jugador()` dentro de su propio código; solo los recibió.
	- **Independencia Final:** Al igual que en la asociación, si borras el equipo, los jugadores no se borran (no hay `null` en cascada).


3. **Composición: "El Cuerpo Humano" (Relación Fuerte)**

	Es una relación de dependencia total. Aquí, las partes **no tienen sentido** ni pueden existir sin el "todo".
	
	- **La Analogía:** Un **Libro** y sus **Páginas**. Si tú quemas el libro (destruyes el objeto principal), las páginas dejan de existir como parte de ese libro. No puedes tener las páginas de "Harry Potter" flotando por ahí sin el libro al que pertenecen.
	-  La relación entre una **Oficina** y su **Dirección**. Si eliminas la oficina del sistema, esa instancia específica de "dirección" asociada a ella ya no tiene razón de ser.
	- Imagina que una `Casa` tiene una `Habitación`. Si destruyes la casa, no tiene sentido que la habitación quede flotando en el aire en medio de la calle.
	
	```java
	// La "Parte": Depende totalmente de la casa
	class Habitacion {
	    private String tipo;
	
	    public Habitacion(String tipo) {
	        this.tipo = tipo;
	    }
	    //Metodo para devolver el nombre
	    public String getTipo() { return tipo; }
	}
	
	// El "Todo" (Contenedor): Es el DUEÑO absoluto
	class Casa {
	    private Habitacion cocina; // Composición
	
	    public Casa() {
	        // CLAVE DE COMPOSICIÓN: 
	        // La parte se crea AQUÍ ADENTRO. 
	        // La habitación nace cuando la casa nace.
	        this.cocina = new Habitacion("Cocina Integral");
	    }
		//Metodo que imprime la informacion 
	    public void mostrarDetalles() {
	        System.out.println("Esta casa tiene una: " + cocina.getTipo());
	    }
	}
	
	// --- CLASE PRINCIPAL ---
	public class Urbanizacion {
	    public static void main(String[] args) {
	        // Creamos la casa
	        Casa miCasa = new Casa();
	        miCasa.mostrarDetalles();
	
	        // PRUEBA DE FUEGO (Destrucción):
	        System.out.println("--- Demoliendo la casa... ---");
	        miCasa = null; 
	
	        // En este punto, el objeto 'cocina' que estaba dentro de 'miCasa'
	        // es inaccesible. El Recolector de Basura de Java lo borrará de la  memoria
	        // porque no puede existir sin su casa.
	    }
	} 

	```
	1. **Creación Interna:** Nota que en el `main` **nunca** hicimos `new Habitacion()`. La habitación fue creada por la `Casa` en su constructor.
	2. **Privacidad Total:** El mundo exterior no sabe que la habitación existe a menos que la casa se lo diga. La habitación es "propiedad privada" de la casa.
	3. **Dependencia de Vida:** Si la variable `miCasa` pasa a ser `null`, la `cocina` se pierde para siempre. No hay forma de "mudar" esa cocina a otra casa porque nació y murió con la estructura original.
	
	⚖️ Resumen de las 3 relaciones para que no las olvides: ^947696
	
- **Asociación:** Se saludan (Médico - Paciente).
- **Agregación:** Están juntos pero pueden separarse (Equipo - Jugador).
- **Composición:** Si uno muere, el otro también (Casa - Habitación). ^c6918f

# 11_El IDE (Integrated Development Environment)

Un IDE **(Entorno de Desarrollo Integrado)** no es un simple editor de texto (como el Bloc de notas); es un **entorno integral**.

- **La Analogía:** Es como una **cabina de avión**. Tienes el volante (editor), los radares que te avisan de fallos (corrector de errores en tiempo real), el motor (compilador) y la caja negra (depurador).
- **IntelliJ IDEA:** Es el estándar de oro para Java. Es muy inteligente (de ahí su nombre); "entiende" tu código y te sugiere mejoras.
- **VS Code:** Es más ligero y versátil, funciona con casi cualquier lenguaje mediante extensiones.

# 12_Flujo de Compilación (El traductor)

Java es un lenguaje de **alto nivel**, lo que significa que es fácil de leer para nosotros, pero imposible para el procesador.

- **El Proceso:**
    1. Escribes código fuente (`.java`).
    2. El **Compilador** lo traduce a **Bytecode** (`.class`). Es un lenguaje intermedio universal.
    3. La **JVM (Java Virtual Machine)** toma ese Bytecode y lo ejecuta en cualquier computadora.
- **¿Por qué es importante?** Porque esto permite que Java sea "escribe una vez, ejecuta donde sea".

# 13_ Git: El Control de Versiones (La Máquina del Tiempo)

El documento lo describe como algo "vital". Git es el estándar de la industria para gestionar el código.

- **La Analogía:** Es el **"Guardar Partida"** de un videojuego antes de enfrentarte a un jefe final. Si pierdes (si tu código deja de funcionar), simplemente regresas al punto anterior.
- **Conceptos Clave:**
    - **Repository (Repo):** La carpeta del proyecto vigilada por Git.
    - **Commit:** Una "foto" de tu código en un momento específico con un mensaje explicativo.
    - **Branch (Rama):** Un universo paralelo donde puedes probar una función nueva sin dañar la versión principal que ya funciona.
# 14_Tipos Primitivos vs. Objetos (El contenido vs. El envase) [[1_poo.pdf#search=2) Conceptos Clave|1_poo, p.10]]

Antes de guardar mil objetos, debemos entender el dato más simple.

- **Primitivos (`int`, `double`, `boolean`):** Son valores puros. Ocupan muy poca memoria. Es como tener una moneda suelta en el bolsillo.
- **Wrappers (Objetos como `Integer` o `String`):** Son clases que envuelven al primitivo para darle "superpoderes" (métodos). Es como tener esa moneda dentro de un monedero con etiquetas.

### **Arreglos (Arrays): Los Casilleros Estáticos**

Imagina una estantería de madera atornillada a la pared.

- **Características:** Tienen un **tamaño fijo**. Si la compras para 10 libros y quieres meter el 11, no puedes; tienes que construir una estantería nueva.
- **Uso:** Son ultra rápidos porque la computadora sabe exactamente dónde empieza y termina cada espacio.
- **En Java:** `String[] nombres = new String[10];`

### Listas (ArrayList): El Acordeón Dinámico

Aquí es donde la POO se pone interesante. Una lista es un objeto que administra a otros objetos.

- **Características:** **Crecen y se encogen** solas. Si necesitas más espacio, la lista se expande automáticamente en memoria.
- **La Analogía:** Es como un grupo de amigos tomados de la mano. Si llega uno nuevo, simplemente se abre un espacio y se toma de las manos de los demás.
- **En Java:** `List<Persona> lista = new ArrayList<>();`
```java
// Creamos una lista dinámica para guardar nuestros objetos
List<String> inventario = new ArrayList<>();

// Agregamos elementos (la lista crece sola)
inventario.add("Espada");
inventario.add("Escudo");

// Usamos un Iterador (o un for-each, que es su versión moderna)
for (String item : inventario) {
    System.out.println("Tienes un: " + item);
}
```

### El Iterador: El "Puntero" Inteligente

¿Cómo recorres una lista sin perderte?

- **El problema:** A veces, borrar un elemento mientras recorres una lista con un `for` tradicional causa errores (como quitarle un escalón a alguien mientras sube la escalera).
- **La solución (Iterador):** Es un objeto especial cuya única misión es ir de uno en uno preguntando: _"¿Hay alguien más adelante?"_ (`hasNext`) y _"Pásame al siguiente"_ (`next`). Es la forma más segura de recorrer estructuras de datos complejas.

# 15_Modularidad y Reutilización [[1_poo.pdf#search=2) Conceptos Clave|1_poo, p.18]]

La **Modularidad** es el principio de "Divide y Vencerás". Consiste en separar un sistema en partes independientes (módulos) que se comunican entre sí,  esto se logra mediante **Paquetes** y **Bibliotecas**.

1. Los Paquetes (Packages): La lógica del Archivador

	No guardas tus calcetines con las sartenes, ¿verdad? En Java, los paquetes son carpetas lógicas que agrupan clases relacionadas.
	
	- **Nivel Pro:** Los paquetes no solo organizan, sino que crean **espacios de nombres**. Puedes tener dos clases llamadas `Usuario`, una en `com.tienda.db` (para la base de datos) y otra en `com.tienda.ui` (para la interfaz), y no chocarán.
	- **Encapsulamiento de Paquete:** Existe un modificador de acceso (el que viene por defecto si no pones `public` ni `private`) que permite que las clases solo se "hablen" si están en el mismo paquete. Es seguridad a nivel de carpeta.
	- **`src/` (Source):** Aquí es donde escribes TÚ. Dentro de `src` es donde creas tus **Paquetes** (carpetas). Todo lo que está en `src` es tu código "virgen"

2. Bibliotecas (Libraries) y Reutilización

	Una biblioteca es un conjunto de módulos ya probados que puedes "enchufar" a tu proyecto.
	
	- **La Analogía:** No fabricas tus propios tornillos cada vez que haces un mueble; vas a la ferretería y compras una caja de tornillos estándar.
	- **En la práctica:** Usar librerías como _Apache Commons_ o incluso la misma _Java Standard Library_ es lo que permite que el software sea **escalable**. Si ya alguien resolvió cómo enviar un correo electrónico, tú importas esa biblioteca y te enfocas en la lógica de tu negocio.
	- **`lib/` o Dependencias:** Aquí es donde se "instalan" las **Bibliotecas**. En proyectos profesionales (usando Maven o Gradle), estas bibliotecas ni siquiera se ven en las carpetas de código, sino que el sistema las descarga y las tiene listas para que tú las uses con un `import`.

	Ejemplo de una tienda E-commerce esta seria una estructura 
	```powershell 
	src/
	 └── com/
	      └── tuempresa/
	           ├── modelo/         <-- Paquete de "Planos" (Clases base)
	           │    ├── Producto.java
	           │    └── Cliente.java
	           ├── servicios/      <-- Paquete de Lógica (Cálculos, APIs)
	           │    ├── CalculadoraImpuestos.java
	           │    └── ValidadorPago.java
	           └── persistencia/   <-- Paquete de Datos (Guardado)
	                └── DatabaseConnector.java
	
	```
	
	Para usar una clase que está en otro "módulo" o paquete, usamos la sentencia `import`.
	```java
	package com.tuempresa.servicios; // Declaramos dónde estamos
	
	import com.tuempresa.modelo.Producto; // Traemos lo que necesitamos de otro módulo
	
	public class CarritoCompra {
	    public void agregar(Producto p) {
	        // Lógica para añadir el producto
	    }
	}
	```
	
	1. Estructura de Carpetas Estándar 
		
		Independientemente del lenguaje, en el análisis previo se suelen definir estos "dominios":
	
		1. **`domain` o `model` (El Corazón):**
		    - **Qué hay aquí:** Las clases básicas (POJOs en Java). Ej: `Usuario`, `Producto`, `Pedido`.
		    - **SDLC:** Aquí se traduce el **Diagrama de Clases** que mencionamos en la temática 3. Es la representación pura del negocio.
		2. **`repository` o `persistence` (La Memoria):**
		    - **Qué hay aquí:** Las clases que se encargan de hablar con la base de datos o guardar archivos.
		    - **SDLC:** Se define durante el diseño de datos. Su función es que el resto del sistema no sepa si usas MySQL, MongoDB o un archivo de texto.
		3. **`service` o `logic` (El Cerebro):**
		    - **Qué hay aquí:** La lógica de negocio pesada. Ej: `CalculadoraDescuentos`, `ValidadorDeRegistro`.
		    - **Análisis:** Aquí se implementan las reglas que el cliente pidió en la fase de levantamiento de requisitos. Un "Servicio" suele usar varios "Modelos" para completar una tarea.
		4. **`controller` o `api` (La Aduana):**
		    - **Qué hay aquí:** Las clases que reciben las peticiones del exterior (clics del usuario, llamadas desde una App móvil).
		    - **SDLC:** Se diseña en la fase de interfaz y comunicación. Su única misión es recibir datos, pasarlos al `service` y devolver una respuesta.
		5. **`dto` (Data Transfer Objects):**
		    - **Qué hay aquí:** Versiones simplificadas de tus modelos.
		    - **Por qué existe:** Imagina que tu clase `Usuario` tiene 50 atributos, pero para el login solo necesitas `email` y `password`. El DTO es esa "maleta pequeña" para mover solo lo necesario.
		6. **`exception` o `error`:**
		    - **Qué hay aquí:** Clases personalizadas para cuando algo sale mal (Ej: `UsuarioNoEncontradoException`). 


# 17_El Ciclo de Vida del Software (SDLC)

Es el camino que recorre una idea hasta convertirse en un producto real. El documento destaca que no se trata solo de programar, sino de seguir fases:

1. **Requisitos:** Escuchar al cliente. _"Quiero una app para un hospital"_.
2. **Análisis/Diseño:** Aquí entra el **UML**. Creamos los planos.
3. **Implementación:** Escribir el código (todo lo que vimos de clases, herencia, etc.).
4. **Pruebas (Testing):** Verificar que no explote (usando lo que vimos de Excepciones).
5. **Mantenimiento:** Actualizar y mejorar.
6. **UML (Unified Modeling Language):** El Idioma Universal

Imagina que un arquitecto de Japón y uno de Colombia quieren construir un edificio. No necesitan hablar el mismo idioma si ambos saben leer un **plano azul**. El UML es ese plano azul para el software.

El documento se enfoca en dos diagramas vitales:

A. Diagramas de Casos de Uso (¿Qué hace el sistema?)

- **Enfoque:** Describe la funcionalidad desde la perspectiva del usuario (Actor).
- **Elementos:** El "Monigote" (Actor) y los "Ovalos" (Casos de Uso).
- **Ejemplo:** Un Actor "Paciente" tiene un Caso de Uso llamado "Solicitar Cita". No nos importa el código aún, solo **qué** puede hacer el usuario.

B. Diagramas de Clases (¿Cómo está construido?)

Aquí es donde aplicamos todo lo que hemos estudiado:

- **El Cuadro:** Se divide en tres: Nombre de la clase, Atributos y Métodos.
- **Las Flechas:** Representan la **Herencia**, **Asociación**, **Agregación** y **Composición** que analizamos detalladamente antes.
- **Multiplicidad:** Esos numeritos (1.."*" 0..1) que dicen si un Médico puede tener uno o muchos Pacientes.

🛠️ ¿Cómo se lleva el mundo real al código? (El Proceso)

1. **Captura:** El cliente dice: "El sistema debe permitir que un médico vea la ficha de sus pacientes".
2. **Modelo UML:** Dibujas una clase `Medico` conectada por una línea de **Asociación** a una clase `Paciente`.
3. **Traducción a Java:**
    - El cuadro "Medico" se convierte en `public class Medico`.
    - La línea de asociación se convierte en un atributo `private List<Paciente> pacientes;`
    - El caso de uso "Ver Ficha" se convierte en un método `public void verFicha(Paciente p)`

# 18_CRUD [[1_poo.pdf#search=1) Definición|1_poo, p.29]]

Es el acrónimo que describe las cuatro operaciones fundamentales que puedes hacer con la información en cualquier sistema: `**C**reate, **R**ead, **U**pdate y **D**elete.

Si la POO es la estructura (el edificio), el CRUD es el **movimiento de los habitantes** (los datos).

🛠️ ¿Qué significa cada letra? (Con ejemplos en Java)

Imagina que estamos gestionando una lista de `Estudiantes` en tu universidad:

|Sigla|Operación|Acción en el mundo real|Ejemplo de método en Java|
|---|---|---|---|
|**C**|**Create**|Registrar a un alumno nuevo.|`lista.add(nuevoEstudiante);`|
|**R**|**Read**|Buscar los datos de un alumno por su ID.|`lista.get(index);`|
|**U**|**Update**|Cambiar la dirección o el teléfono del alumno.|`estudiante.setTelefono("555-0123");`|
|**D**|**Delete**|Dar de baja a un alumno que se graduó.|`lista.remove(estudiante);`|

💡 ¿Por qué es tan importante para tu formación?

1. **Es el estándar de la industria:** Casi cualquier aplicación que uses hoy (Instagram, Amazon, WhatsApp) es, en el fondo, un "CRUD Gigante".
    - Instagram:  `Creas un post (C), lees el feed (R), editas el pie de foto (U) o borras una historia (D).`
2. **Conecta la POO con las Bases de Datos:** El CRUD es el puente. Cuando aprendas SQL, verás que estas operaciones se traducen directamente a comandos como `INSERT`, `SELECT`, `UPDATE` y `DELETE`.
3. **Aplica todos los pilares:** Para hacer un CRUD profesional, necesitas usar **Encapsulamiento** (para proteger los datos), **Colecciones** (como las listas que vimos en la Temática 5) y **Excepciones** (por si intentas borrar a alguien que no existe).

```java
public class EstudianteService {
    private List<Estudiante> baseDatos = new ArrayList<>();

    // CREATE
    public void crear(Estudiante e) { baseDatos.add(e); }

    // READ
    public Estudiante buscar(int id) { return baseDatos.get(id); }

    // UPDATE
    public void actualizar(int id, String nuevoNombre) {
        baseDatos.get(id).setNombre(nuevoNombre);
    }

    // DELETE
    public void eliminar(int id) { baseDatos.remove(id); }
}
```
# 19_Abstracción y Interfaz

^77d6df

1. ¿Qué es la Abstracción?

	Es el proceso de **ignorar los detalles internos** y concentrarse solo en **lo que hace** un objeto.
	
	- **La esencia:** Es extraer las características esenciales de algo.
	- **El ejemplo del coche:** Para usar un coche, tú te "abstraes" del sistema de inyección de combustible. Solo te importa la "interfaz" (volante, pedales)
2. ¿Qué relación tiene con la Interface?

	La relación es de **Concepto vs. Herramienta**:
	
	- **Abstracción es el concepto:** Es la idea de ocultar la complejidad.
	- **Interface es la herramienta:** Es el mecanismo técnico que usamos en Java para aplicar esa abstracción.
	 ```texto
	 Una **Interface** es una **Abstracción Total**. ¿Por qué? Porque en una interfaz no hay ni una sola línea de código sobre "cómo" se hacen las cosas. Solo hay una lista de "qué" se debe hacer.
	 ```

3.  Para explicarlo con la máxima coherencia, imagina que una **Interface** es un **Manual de Funciones** de un cargo en una empresa. El manual dice: "El empleado debe `firmarDocumento()`", pero no dice si lo firma con bolígrafo azul, negro o de forma digital.

	**clave técnica:** los métodos en una interfaz son **abstractos por definición**, lo que significa que **no tienen cuerpo** (no tienen las llaves `{ }` con código dentro). Solo son la "firma" del método.
	1. La Interfaz es un "Contrato de Comportamiento"
		
		Si tú creas la interfaz `Volable`, sería **incoherente** aplicársela a la clase `Perro`.
		
		- **La Coherencia:** Antes de programar, tú analizas: _"¿Qué tienen en común un Avión, un Pájaro y un Superhéroe?"_. La respuesta es: _"Todos vuelan"_.
		- **La Interfaz:** Creas `interface Volable { void despegar(); }`.
		
	1. Tenemos un sistema que envía mensajes. Queremos **abstraer** el envío para que al programa principal no le importe si es un SMS o un Email.
		```java
				// Esto es 100% abstracto. No hay lógica, solo promesas.
		public interface Notificador {
		    // El método termina en ";" porque NO tiene cuerpo.
		    void enviar(String mensaje); 
		}
		```
		
	2. se implementa (**El como**)
		Aquí es donde la **Coherencia** entra en juego. Diferentes clases firman el contrato y deciden cómo cumplirlo.
		```java
			public class NotificadorEmail implements Notificador {
			    @Override
			    public void enviar(String mensaje) {
			        // Aquí SÍ hay código. Cada clase decide su "cómo".
			        System.out.println("Conectando al servidor SMTP..Enviando Email: " + mensaje);
			    }
			}
		
			public class NotificadorSMS implements Notificador {
			    @Override
			    public void enviar(String mensaje) {
			        System.out.println("Conectando a la red móvil... Enviando SMS: " + mensaje);
		    }
		}
				
		```
		
	3. el poder de las **Abstracción (El uso)**
		- ```java
	public class SistemaPrincipal {
	    public static void main(String[] args) {
	        // Usamos la Interface como tipo de dato (Abstracción)
	        Notificador miServicio;
	
	        // Mañana puedo cambiar esto por SMS y el resto del código no cambia
	        miServicio = new NotificadorEmail(); 
	        
	        // Llamamos al método. El sistema no sabe si es mail o sms, 
	        // solo sabe que "Notificador" garantiza que el método existe.
	        miServicio.enviar("¡Hola, tienes una actualización!");
	    }
	}
			```
			
1. El Contrato (La Interface)

	Aquí aplicamos la **Abstracción Total**. Solo definimos el **QUÉ**.


4. Obligación vs. Libertad (El poder del "Cómo")

	La interfaz **te obliga** a usar los métodos, pero te da libertad absoluta en el **código interno**.
	
	- **La Obligación:** Si firmas el contrato `Volable`, **tienes** que tener el método `despegar()`. Si no lo pones, Java te dará un error rojo y no te dejará seguir.
	- **La Libertad:** El `Avión` despega usando turbinas, el `Pájaro` batiendo alas. El "cómo" es privado de cada clase (Alta Cohesión), pero el "qué" es estándar (Bajo Acoplamiento).

5. La Coherencia evita las "Interfaces Monstruo"

	Si pones demasiados métodos en una interfaz (ej. una interfaz `Acciones` que tenga `volar()`, `nadar()`, `ladrar()`), pierdes la coherencia.
	
	- Un pez se vería obligado a implementar `ladrar()`, lo cual es un error de diseño (Baja Cohesión).
	- **La solución profesional:** Crear interfaces pequeñas y coherentes (`Nadable`, `Ladrable`). Así, cada clase solo firma los contratos que realmente puede cumplir.



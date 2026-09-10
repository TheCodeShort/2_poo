```table-of-contents
title: Conceptos POO
minDepth: 1
maxDepth: 6
listStyle: number
```

[[2_SDLC_sofware.pdf#search=Estructura de datos|SDLC_sofware, p.527]]
# 1_Qué es 

El texto llama a estas estructuras también **arreglos** y explica que sirven para organizar información de forma ordenada. La idea base es simple pero poderosa: en vez de tener datos sueltos, los agrupas para poder recorrerlos, buscarlos, ordenarlos o filtrarlos después. En lógica de programación, esto es como pasar de tener variables aisladas a tener una lista o diccionario bien pensado.

# 2_Vectores

Un **vector** es un arreglo **finito, ordenado y homogéneo**; es decir, todos sus elementos son del mismo tipo y se accede a ellos por posición. El documento remarca algo clave: los índices empiezan en **0**, no en 1. Por eso el primer elemento es `vector[0]` y el último es `vector[length - 1]`. Si intentas acceder a un índice inválido, obtienes `undefined`.

El ejemplo de `frutas = ["Manzana", "Banana", "Pera"]` sirve para mostrar dos cosas: cómo declarar un vector y cómo consultar su tamaño con `frutas.length`. Ahí se ve que `length` no es decoración; es la forma de saber cuántos elementos hay realmente dentro del arreglo. En Python sería lo mismo que usar `len(lista)`.

El material también muestra acceso directo a posiciones concretas con `arreglo[0]`, `arreglo[2]` y `arreglo[arreglo.length - 1]`. Esa parte es importante porque enseña la relación entre índice y posición real. El quinto elemento no está en `5`, sino en `4`, porque el conteo arranca en cero. Ese detalle parece pequeño, pero es el tipo de error que hace llorar a medio curso cuando el arreglo “no funciona”.

# 3_Recorrer y manipular vectores

Para hacer asignaciones o lecturas/escrituras sobre un vector, conviene usar **estructuras repetitivas**. La razón es técnica: los bucles permiten recorrer cada índice de forma ordenada y automática, sin escribir una instrucción manual para cada posición. Esa recomendación aparece claramente cuando se explica el vector de 5 números y el uso de `PARA o FOR` para pedir datos y luego revisarlos uno por uno.
# 4_Métodos comunes de un vector

 métodos muy prácticos esto depende del lenguaje. 

- `indexOf()` busca la posición de un valor
- `join()` convierte el arreglo en texto
- `push()` agrega al final
- `pop()` elimina el último 
- `sort()` ordena 
- `shift()` elimina el primero

La lógica general es esta: no solo guardas datos, también los transformas.

Esto es muy parecido a trabajar con una lista en Python: a veces la usas como almacén, a veces como cola, a veces como texto, y a veces como conjunto de datos que debes ordenar antes de analizar. El documento te está entrenando justamente para pensar en el arreglo como una estructura viva, no como una caja estática.

# 5_Matrices
Las **matrices** se presentan como arreglos de más de una dimensión. El texto las explica de forma muy clara: una matriz puede verse como un vector cuyos elementos son otros vectores. Eso significa que ya no accedes con un solo índice, sino con dos coordenadas, como fila y columna.
## 1_ejemplo
este ejemplo es con el lenguaje JAVA => 
### 1_Declaración e Inicialización

En Java existen dos formas principales de crear una matriz.

 **Inicialización por tamaño:** Declaras el espacio vacío y luego asignas los valores uno a uno.
```java
int[][] matriz = new int[3][3]; // Crea una matriz vacía de 3x3
```

**Inicialización directa (Literal):** Defines la estructura y los valores al mismo tiempo
```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

### 2_El Gran Secreto: Matrices Irregulares (_Jagged Arrays_)

Este es un concepto avanzado que suele faltar en las notas básicas. Como en Java las matrices son arreglos de arreglos, **las filas no están obligadas a tener el mismo tamaño**.

Puedes definir una matriz donde la primera fila tenga 2 elementos, la segunda 4 y la tercera 1:

```JAVA
int[][] matrizIrregular = new int[3][]; // Solo defines la cantidad de filas
matrizIrregular[0] = new int[2]; // Fila 0 tiene 2 columnas
matrizIrregular[1] = new int[4]; // Fila 1 tiene 4 columnas
matrizIrregular[2] = new int[1]; // Fila 2 tiene 1 columna
```

### 3_Recorrido Eficiente (Bucles)

Para leer o modificar una matriz necesitas bucles anidados. Asegúrate de tener anotadas estas dos formas:

**Bucle `for` clásico (Usa la propiedad `.length`):**

```java
for (int i = 0; i < matriz.length; i++) { // matriz.length da el número de filas
	for (int j = 0; j < matriz[i].length; j++) { // matriz[i].length da las columnas de esa fila
		System.out.print(matriz[i][j] + " ");
	}
}
```
        
**Bucle `for-each` (Ideal para solo lectura):**

```java
for (int[] fila : matriz) {
	for (int elemento : fila) {
		System.out.print(elemento + " ");
	}
}
```
# 6_Registros

Los **registros** aparecen como una colección de datos de diferente tipo relacionados entre sí. Aquí ya no todos los elementos son homogéneos: un registro puede mezclar nombre, correo, edad y saldo. Esa mezcla es importante porque modela mejor datos reales de personas, productos o clientes.

El documento codifica los registros como un arreglo de arreglos, donde cada fila contiene la información completa de una persona. Además, para recorrerlos usa **dos ciclos `for` anidados**: uno recorre cada registro y el otro recorre los campos dentro de ese registro. Esa técnica es clave porque te enseña a atravesar estructuras bidimensionales de forma sistemática.

## 1_Datos Heterogéneos (Diferentes tipos)

Hasta ahora, una matriz normal de `int` solo guarda números enteros. Pero en el mundo real, los datos vienen mezclados. Piensa en una **tarjeta de identificación**:

- Nombre \(\rightarrow \) Texto (`String`)
- Edad \(\rightarrow \) Número (`int`)
- Saldo \(\rightarrow \) Decimal (`double`)

```java
// Estructura rígida de Filas y Columnas
Object[][] registros = {
    {"Ana", "ana@mail.com", 25},  // Fila 0
    {"Luis", "luis@mail.com", 30} // Fila 1
};

// Para obtener el correo de Ana tienes que buscar la Fila 0, Columna 1
System.out.println(registros[0][1]); 

```

# 7_Listas
Colecciones lineales de elementos en las que el orden de inserción se respeta. En POO, se implementan mediante clases como ArrayList o LinkedList, cada una con características particulares (García & Mendoza, 2022).
Es la estructura más común. Funcionan como una fila de sillas numeradas donde el orden importa.

_Ejemplo en el código:_ `ArrayList` (muy usada en JAVA) o `LinkedList`.
	
_Uso práctico:_ Mostrar el catálogo de productos de una tienda virtual, donde quieres mantener el orden en el que se agregaron.
		
## 1_¿Cómo funciona en la vida real?

Piensa en un **estuche de CDs** o un **archivador**.

- Cada elemento tiene una **posición** (índice).
- En programación, siempre empezamos a contar desde el **cero (0)**.
- Si quitas el elemento del medio, los demás se "reacomodan". 
	
## 2_ArrayList (Como un estante de libros)

Están todos pegados. Si quieres el libro 5, vas directo a él. Pero si quieres meter un libro nuevo al principio, tienes que empujar todos los demás hacia la derecha.

- **Ventaja:** Acceso instantáneo por posición.
- **Desventaja:** Lento para añadir o quitar cosas en el medio.

1. Ejemplo en Código Java ==ArrayList==
2. ```java
   import java.util.ArrayList; // Importamos la herramienta de listas
	import java.util.List;
	
	public class EjemploListas {
		public static void main(String[] args) {
			
			// 1. Creamos la lista (como una bolsa donde solo caben Strings)
			List<String> listaPacientes = new ArrayList<>();
	
			// 2. AGREGAR: Metemos elementos
			listaPacientes.add("Alex");    // Posición 0
			listaPacientes.add("Juan");    // Posición 1
			listaPacientes.add("Maria");   // Posición 2
	
			// 3. ACCEDER: ¿Quién está en la primera posición?
			System.out.println("El primer paciente es: " + listaPacientes.get(0));
	
			// 4. ELIMINAR: Juan se fue, lo borramos
			listaPacientes.remove(1); 
	
			// 5. TAMAÑO: ¿Cuántos quedan?
			System.out.println("Pacientes restantes: " + listaPacientes.size());
		}
	}
   ```

## 3_LinkedList (Como una cadena de tesoros)

Cada elemento (llamado "nodo") tiene el dato y una "mano" que agarra al siguiente. No están pegados en memoria, están unidos por direcciones.

- **Ventaja:** Rapidez extrema para meter o sacar elementos (solo rompes un eslabón y enganchas el nuevo).
- **Desventaja:** Si quieres el elemento 100, Java tiene que ir desde el 1, pasando por el 2, el 3... hasta llegar al 100. No puede "saltar" directo.

1. **Ejemplo en código Java** ==LinkedList==
	- ```java
  import java.util.LinkedList;
	import java.util.List;
	
	public class EjemploLinkedList {
		public static void main(String[] args) {
			// Solo cambia 'ArrayList' por 'LinkedList'
			List<String> listaEnlazada = new LinkedList<>();
	
			// ¡Los métodos son los mismos!
			listaEnlazada.add("Paciente A");
			listaEnlazada.add("Paciente B");
			
			// Pero LinkedList tiene "superpoderes" extra si usas la clase específica:
			LinkedList<String> listaPro = new LinkedList<>();
			listaPro.add("Medio");
			listaPro.addFirst("Inicio"); // Método que no tiene ArrayList
			listaPro.addLast("Final");   // Método que no tiene ArrayList
	
			System.out.println(listaPro);
		}
	}

	  ```


# 8_Pilas (Stacks - LIFO)
Estructuras de tipo LIFO (Last In, First Out) que permiten apilar y desapilar elementos. Se utilizan en la implementación de algoritmos recursivos, control de llamadas o deshacer acciones.

- El primero en entrar es el primero en salir). Piensa en la fila del banco: el primero que llega es el primero en ser atendido.
    
    - _Uso práctico:_ Una cola de impresión. Si mandas a imprimir 3 documentos, la impresora los saca en el orden exacto en que los recibió. También existen las _Priority Queues_, donde alguien puede "colarse" si tiene mayor urgencia.
        
- **Conjuntos (Sets):** Son como un club exclusivo: **no admiten duplicados**.

	- _Uso práctico:_ Imagina que quieres registrar los números de documento (cédulas) de los usuarios. No pueden existir dos personas con la misma cédula. Un `HashSet` rechazaría automáticamente cualquier intento de guardar una cédula repetida, haciéndolo muy eficiente.

- Para entender las **Pilas**, olvida los estantes y las cadenas. Imagina una **pila de platos** o una **pila de libros**:

	1. Solo puedes poner un plato **arriba** de todos.
	2. Si quieres sacar un plato, solo puedes agarrar el que está **arriba**.
	3. Si quieres el plato que está al fondo, ¡tienes que sacar todos los de arriba primero!

- Los 3 comandos básicos en Java

	En las pilas no hablamos de "añadir" o "quitar", usamos nombres especiales:
	
	- **`push` (Empujar):** Pones un elemento arriba de la pila.
	- **`pop` (Sacar):** Sacas el elemento de arriba (y desaparece de la pila).
	- **`peek` (Vistazo):** Miras qué hay arriba, pero no lo quitas. 
	
## 1_Ejemplo en código Java
### 1_==Stack==
```java
import java.util.Stack;
	
public class EjemploPila {
	public static void main(String[] args) {
// Creamos la pila de pesos
		Stack<Double> historialPesos = new Stack<>();

// 1. PUSH: El paciente se pesa varias veces en el mes
		historialPesos.push(80.5); // Primero en entrar (Fondo)
		historialPesos.push(79.0); 
		historialPesos.push(78.2); // Último en entrar (Cima)

// 2. PEEK: ¿Cuál es el peso actual? (Sin borrarlo)
		System.out.println("Peso actual: " + historialPesos.peek()); // 78.2

// 3. POP: El paciente dice "me equivoqué", borramos el último
		double pesoBorrado = historialPesos.pop(); 
		System.out.println("Eliminamos el peso: " + pesoBorrado);

// Ahora el peso que quedó arriba es el anterior
		System.out.println("Nuevo peso actual: " + historialPesos.peek()); // 79.0
	}
}
```
	
	
### 2_Deque
El nombre **`Deque`** (se pronuncia "deck") significa _Double Ended Queue_ (Cola de doble final). Es como una "Pila Superpoderosa" o una "Cola Flexible".

La gran diferencia es que en un `Deque` puedes meter y sacar cosas **por ambos lados** (por arriba y por abajo).

**¿Por qué se usa en lugar de `Stack`?**

Java recomienda usar `Deque` (específicamente la implementación `ArrayDeque`) porque la clase `Stack` vieja es un poco lenta y pesada. `Deque` es más moderna, rápida y versátil.

#### 1_Ejemplo en código: Usándolo como Pila
		
Aquí tienes cómo se vería tu historial de pesos usando `ArrayDeque`. Fíjate que los métodos cambian un poquito para ser más descriptivos:
```java
import java.util.ArrayDeque;
import java.util.Deque;

public class EjemploDeque {
	public static void main(String[] args) {
		// Creamos el Deque (el motor es un ArrayDeque)
		Deque<Double> historial = new ArrayDeque<>();

		// --- COMPORTAMIENTO DE PILA (LIFO) ---
		
		// 1. Agregar arriba (en lugar de push)
		historial.push(90.0);
		historial.push(85.5);
		historial.push(82.0); // Este queda arriba

		// 2. Ver el de arriba
		System.out.println("Último peso: " + historial.peek()); // 82.0

		// 3. Sacar el de arriba
		historial.pop(); 

		// --- ¿POR QUÉ ES MEJOR? (Flexibilidad) ---
		
		// Puedes agregar algo directamente al fondo sin sacar lo de arriba
		historial.addLast(100.0); 
		
		// O sacar el peso más viejo de todos (el del fondo)
		Double pesoInicial = historial.removeLast();
		
		System.out.println("Historial restante: " + historial);
	}
}
/**
- **Para el frente:** => `addFirst()`, `removeFirst()`, `peekFirst()`.
- **Para el final:** => `addLast()`, `removeLast()`, `peekLast()`.
*/			
```

# 9_Colas (Queues): Estructuras FIFO (First In, First Out) 
útiles para gestionar procesos en espera, tareas de impresión o mensajes en sistemas distribuidos. Variantes como PriorityQueue permiten ordenamientos adicionales.
Piensa en la fila del banco: el primero que llega es el primero en ser atendido.

- _Uso práctico:_ Una cola de impresión. Si mandas a imprimir 3 documentos, la impresora los saca en el orden exacto en que los recibió. También existen las _Priority Queues_, donde alguien puede "colarse" si tiene mayor urgencia.
- Imagina la fila de un banco o la fila para entrar al cine:
1. La gente llega y se pone al **final** de la fila.
2. El cajero atiende únicamente al que está al **principio**.
3. Nadie puede colarse (en teoría) ni salir por el medio.

## 1_Los comandos en Java

A diferencia de la Pila, aquí los nombres cambian para reflejar que es una fila:

- **`add` / `offer`:** Llegas a la fila y te pones al final.
- **`poll`:** El primero de la fila sale porque ya lo atendieron (se elimina).
- **`peek`:** Miras quién es el siguiente en ser atendido, pero no lo sacas.
- **Un detalle de "Modularidad":**  
	Nota que en el código usé `Queue<String> lista = new LinkedList<>();`. Aquí aplicamos de nuevo el **Diseño Orientado a Interfaces**: `Queue` es la interfaz (el contrato) y `LinkedList` es la clase que hace el trabajo sucio.

## 2_Ejemplo en código Java
### 1_==Queue==
```java
import java.util.LinkedList;
import java.util.Queue;

public class EjemploCola {
	public static void main(String[] args) {
		// Usamos LinkedList porque implementa la interfaz Queue
		Queue<String> filaPacientes = new LinkedList<>();

		// 1. LLEGAN PACIENTES (Se forman al final)
		filaPacientes.add("Paciente 1: Carlos");
		filaPacientes.add("Paciente 2: Adriana");
		filaPacientes.add("Paciente 3: Pepe");

		// 2. PEEK: ¿A quién le toca ahora?
		System.out.println("Siguiente en turno: " + filaPacientes.peek()); // Carlos

		// 3. POLL: Atendemos a Carlos y sale de la fila
		String atendido = filaPacientes.poll();
		System.out.println("Atendiendo a: " + atendido);

		// 4. ¿Quién quedó de primero ahora?
		System.out.println("Ahora el turno es de: " + filaPacientes.peek()); // Adriana
	}
}
```


## 2_Conjuntos (Sets)
Colecciones que no permiten duplicados. Implementaciones como HashSet o TreeSet ofrecen eficiencia en las operaciones de búsqueda y manipulación de elementos únicos (Hernández & Baquero, 2023). 

Un **Set** es como una bolsa donde echas cosas, pero con una regla mágica: **No se permiten repetidos.**

Si intentas meter a "Adriana" dos veces, la bolsa simplemente ignora la segunda entrada. Es la estructura perfecta cuando quieres asegurar que algo sea **único**.
		
### 1_¿Cómo funciona en la vida real?
		
Imagina una **lista de invitados** a una fiesta. No importa cuántas veces alguien intente anotarse, solo puede aparecer una vez en la lista final. O piensa en los **números de cédula** dos personas no pueden tener el mismo número.

#### 1_Ejemplo en Código Java ==Set==
```java
import java.util.HashSet;
import java.util.Set;

public class EjemploSets {
	public static void main(String[] args) {
		// Creamos el conjunto de IDs de pacientes
		Set<String> idsPacientes = new HashSet<>();

		// 1. AGREGAR
		idsPacientes.add("1020");
		idsPacientes.add("3040");
		idsPacientes.add("1020"); // ¡Ojo! Estamos repitiendo el ID

		// 2. COMPROBAR EL TAMAÑO
		// Aunque intentamos meter 3, solo habrá 2.
		System.out.println("Total de pacientes únicos: " + idsPacientes.size()); 

		// 3. BUSCAR: Es súper rápido saber si alguien ya está
		if (idsPacientes.contains("1020")) {
			System.out.println("El paciente ya está registrado.");
		}

		// 4. ELIMINAR
		idsPacientes.remove("3040");
	}
}
```

- **Sin Duplicados:** La lista te deja tener 50 "Adrianas". El Set solo una.
- **Sin Orden (Normalmente):** El `HashSet` no te garantiza que los elementos salgan en el mismo orden en que los metiste. Los guarda "donde quepan" para ser más rápido.
- **Búsqueda Veloz:** En una lista de 1 millón de nombres, buscar a "Adriana" toma tiempo. En un Set, Java sabe exactamente en qué rincón de la memoria está, ¡es casi instantáneo!
- En Java, el más usado es el `HashSet`.
- **HashSet:** El más rápido, pero desordenado.
- **TreeSet:** (Aquí se une con el concepto de Árboles). Guarda los elementos **ordenados** (por ejemplo, de la A a la Z), pero es un poquito más lento que el HashSet

# 10_Mapas (Maps)
Asociaciones clave-valor también conocidos como Diccionarios que permiten almacenar pares de datos. Ejemplos comunes incluyen HashMap, TreeMap y LinkedHashMap, fundamentales para implementar diccionarios, índices y caches (García & Mendoza, 2022). 

 _Uso práctico:_ Imagina un casillero. La _Clave_ es el número de tu carnet, y el _Valor_ es tu mochila. Si le das el número de carnet al mapa (`HashMap`), te devuelve tus datos instantáneamente sin tener que buscar uno por uno. Es vital para relacionar usuarios con sus sesiones activas.

Si el **Set** era una bolsa de elementos únicos, el **Mapa** es como una **agenda telefónica** o un **casillero de gimnasio**.
		
- La regla aquí es el concepto de **Clave/Valor**:
	
	- **La Clave (Key):** Es el identificador único (como el número de cédula o el nombre del contacto). No se puede repetir.
	- **El Valor (Value):** Es la información que guardas dentro (como el objeto `Persona` con su peso y altura).
	
## 1_¿Por qué es la "Estructura Maestra"?
	
Porque te permite encontrar a **"Adriana"** (el valor) al instante si conoces su **ID** (la clave), sin tener que recorrer una lista, ni vaciar una pila, ni esperar en una cola.
		
### 1_Ejemplo en Código Java
#### 1_==Map==
```java
import java.util.HashMap;
import java.util.Map;

public class EjemploMapas {
	public static void main(String[] args) {
// Map<Clave, Valor> -> Map<Cédula, Objeto Persona>
	Map<String, String> agendaPacientes = new HashMap<>();

// 1. PUT: Guardar (Clave, Valor)
	agendaPacientes.put("1020", "Adriana (IMC: 22.5)");
	agendaPacientes.put("3040", "Juan (IMC: 28.1)");
	agendaPacientes.put("5060", "Pepe (IMC: 24.0)");

// 2. GET: Buscar directamente por la clave
	String datos = agendaPacientes.get("1020");
	System.out.println("Datos recuperados: " + datos);

// 3. ¿Qué pasa si meto la misma clave otra vez?
	agendaPacientes.put("1020", "Adriana - DATOS ACTUALIZADOS"); 
// ¡El valor viejo se sobrescribe! La clave es única.

// 4. ELIMINAR
	agendaPacientes.remove("5060");

// 5. REVISAR SI EXISTE
	if (agendaPacientes.containsKey("3040")) {
		System.out.println("Juan está en el sistema.");
	}
	}
}
```
			
# 11_Arbol 
Los **Árboles** no son solo "otra forma de guardar datos", sino que son la **estrategia de búsqueda** más eficiente que existe. Se les llama "motor" porque muchas estructuras (como el `TreeSet` o el `TreeMap`) los usan por dentro para que todo sea veloz.

- Imagina que estás buscando una palabra en un diccionario físico de 1,000 páginas:
	
	- **Forma Lista:** Empiezas en la página 1, luego la 2... hasta la 1,000. (Muy lento).
	- **Forma Árbol:** Abres el libro por la mitad. ¿Tu palabra empieza con una letra mayor o menor a la que viste? Si es mayor, descartas 500 páginas de un solo golpe. Repites el proceso y en solo **10 saltos** encuentras tu palabra entre 1,000.
	
## 1_¿Cómo es la estructura?

Se llama árbol porque tiene una **Raíz** (el nodo principal) y de ahí salen **Ramas** (hijos).  
En un **Árbol Binario de Búsqueda** (el más común), la regla es:

- Los valores **menores** van a la **izquierda**.
- Los valores **mayores** van a la **derecha**.	
## 2_Ejemplo visual
	
Si insertas los números de identificación: **50, 20, 70, 10, 30**.
```text
  50 (Raíz)
 /  \
20    70
/  \
10  30
```
Si buscas el **30**:

1. Miras el 50: "¿30 es menor?". Sí, vas a la izquierda.
2. Miras el 20: "¿30 es mayor?". Sí, vas a la derecha.
3. **¡Lo encontraste!** Solo hiciste 2 comparaciones en lugar de 5.

## 3_¿Por qué es el "Motor"?

Cuando usas un 
**`HashMap:`** es un pasillo con **16 casilleros gigantes** (buckets), (por ejemplo, el estado _"En Reparación"_), Java le aplica una fórmula matemática a la palabra (llamada función `hashCode()`) que da como resultado un número de casillero, digamos el casillero **4**. Java va y lo mete ahí.

**`HashSet:`** 
en Java, si hay demasiados datos, Java deja de usar una lista simple y convierte todo internamente en un **Árbol** para que, aunque tengas millones de pacientes, encontrarlos tome milisegundos.
## 4_¿Cuándo lo usarías tú directamente?

Casi nunca programarás un árbol desde cero (a menos que sea para un examen), pero usas su lógica cuando necesitas que tus datos estén **siempre ordenados automáticamente**:
```java
import java.util.TreeSet;
// Un Set que usa un Árbol por dentro
TreeSet<Integer> edades = new TreeSet<>();
edades.add(40);
edades.add(10);
edades.add(25);

System.out.println(edades); // Imprime: [10, 25, 40] -> ¡Se ordenó solo!
```
		

# 12_Colecciones genéricas: 
Permiten trabajar con estructuras de datos parametrizadas por tipo, garantizando la seguridad en tiempo de compilación al evitar errores de tipo en tiempo de ejecución (Vázquez, 2020). 
==son la forma que tiene Java de decir: _"Esta bolsa es solo para un tipo de cosa"_==.

Antes, en las versiones muy viejas de Java, las listas eran como "bolsas negras" donde podías meter cualquier cosa: un String, un número y un objeto `Persona` juntos. El problema era que al sacar algo, no sabías qué era y el programa solía romperse (errores de ejecución).
	
Las **Genéricas** llegaron para dar orden y seguridad usando los símbolos **`< >`** (llamados "diamante").

## 1_¿Cómo se ven?

- **Sin genéricos (Peligroso):** `List lista = new ArrayList();` (Cualquier cosa entra).
- **Con genéricos (Seguro):** `List<Persona> lista = new ArrayList<>();` (Solo entran objetos `Persona`).

## 2_¿Por qué son importantes para tu modularidad?

### 1_Seguridad de Tipo (Type Safety):
Si declaras `List<Double> pesos`, e intentas meter el nombre "Alex" (`pesos.add("Alex")`), **IntelliJ te marcará un error rojo antes de que des Play**. Esto evita errores cuando tu app esté funcionando.
### 2_No necesitas "Castear" (Convertir):**  
Al sacar un elemento, Java ya sabe exactamente qué es.
- **Antes:** Tenías que decirle: `Persona p = (Persona) lista.get(0);`
- **Ahora:** Simplemente pones: `Persona p = lista.get(0);`
### 3_Código más limpio
Cualquier programador que lea tu código sabrá de inmediato qué contiene esa colección sin tener que adivinar.

### 4_Ejemplo

Cuando crees tu lista de pacientes, lo harás así:	
```java
// "List" es la colección, "<Paciente>" es el genérico
List<Paciente> listaDeConsultorio = new ArrayList<>();

listaDeConsultorio.add(new Paciente("Alex", 75.0, 1.75)); 
// Si intentas agregar un número aquí, Java no te dejará.
```

# 13_Comparación de estructuras: 
La elección entre estructuras tradicionales y colecciones modernas depende de factores como la eficiencia, la legibilidad y la compatibilidad con algoritmos avanzados.
	
es el ==proceso de analizar cuál es la mejor forma de organizar tus datos basándote en dos factores: **tiempo** (qué tan rápido es el programa) y **memoria** (cuánto espacio ocupa)==. 

No existe una estructura "perfecta", sino una "adecuada" para cada situación. Por ejemplo, un **ArrayList** es excelente para leer datos rápidamente por su posición, pero un **HashMap** es superior si necesitas buscar un elemento específico sin recorrer toda la lista. 
		
## 1_Tabla Comparativa de Estructuras en Java
		
Esta tabla resume cómo se comportan las herramientas que hemos visto según la tarea que necesites realizar
		
| Estructura        | ¿Permite Repetidos? | ¿Mantiene el Orden? | ¿Para qué es mejor?                 | Desventaja principal                |
| ----------------- | ------------------- | ------------------- | ----------------------------------- | ----------------------------------- |
| **ArrayList**     | Sí                  | Sí (por índice)     | Leer datos rápido por posición.     | Lenta al borrar en el medio.        |
| **LinkedList**    | Sí                  | Sí                  | Insertar/Borrar en los extremos.    | Lenta para buscar el elemento #500. |
| **HashSet (Set)** | **No**              | No                  | Asegurar que los datos sean únicos. | No sabes en qué orden saldrán.      |
| **TreeSet (Set)** | **No**              | **Sí (ordenado)**   | Mantener datos ordenados siempre.   | Más lenta que el HashSet.           |
| **HashMap (Map)** | Claves: No          | No                  | Buscar información usando un ID.    | Usa más memoria que una lista.      |
| **Stack (Pila)**  | Sí                  | LIFO (Inverso)      | Deshacer acciones o retroceder.     | Solo accedes al último que entró.   |
| **Queue (Cola)**  | Sí                  | FIFO (Llegada)      | Gestionar turnos y procesos.        | Solo accedes al primero que llegó.  |

## 2_las combinaciones coherentes permitidas en Java

| Lado Izquierdo (La Interfaz / "Los Poderes") | Lado Derecho Válido (La Implementación / "Cómo se organiza") | ¿Por qué son compatibles? (Relación Coherente)                                                                              | ¿Cuándo elegir esta combinación?                                                                                    |
| -------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **`List<T>`**                                | `new ArrayList<>()`                                          | Ambas manejan colecciones ordenadas por índice (0, 1, 2...). `ArrayList` usa un arreglo interno.                            | El 95% de las veces. Ideal para leer y listar datos rápido de la DB en Spring.                                      |
| **`List<T>`**                                | `new LinkedList<>()`                                         | Ambas implementan `List`. `LinkedList` usa nodos enlazados internamente.                                                    | Cuando vas a insertar o borrar muchos elementos constantemente en medio de la lista.                                |
| **`List<T>`**                                | `new CopyOnWriteArrayList<>()`                               | Es una lista especial diseñada para entornos con múltiples hilos de ejecución (Multithreading).                             | Cuando muchos usuarios leen la lista al mismo tiempo en Spring, pero casi nadie la modifica.                        |
| **`List<T>`**                                | `List.of(...)` o `Arrays.asList(...)`                        | Métodos de Java que fabrican internamente una lista fija o inmutable que encaja en la interfaz `List`.                      | Para listas de configuración estáticas (ej. meses del año, roles fijos como `["ADMIN", "USER"]`).                   |
| **`Set<T>`** _(No permite duplicados)_       | `new HashSet<>()`                                            | La familia `Set` no usa índices, asegura elementos únicos. `HashSet` los organiza usando algoritmos de Hash (sin orden).    | Cuando necesitas asegurar que **ningún dato se repita** (ej. correos electrónicos únicos) y no te importa el orden. |
| **`Set<T>`** _(No permite duplicados)_       | `new LinkedHashSet<>()`                                      | Es un `Set` (elementos únicos) pero mantiene internamente el orden en el que los insertaste.                                | Cuando no quieres duplicados, pero sí quieres **mantener el orden de llegada** de los datos.                        |
| **`Map<K, V>`** _(Clave-Valor)_              | `new HashMap<>()`                                            | La familia `Map` guarda parejas. `HashMap` los organiza internamente de forma desordenada en memoria para ser ultra rápido. | Para diccionarios o búsquedas directas. **Aquí es donde va el HashMap.** (Ej: buscar un usuario por su cédula).     |

# 14_¿Cómo elegir? (El criterio de "Big O")
	
En programación profesional se usa la **Notación Big O** para comparar la eficiencia.
==**La "Big O" (Notación Gran O) no es un método ni una línea de código, es un concepto matemático y teórico.**== Piensa en ella como una **regla de medición** o una "balanza" que usan los programadores para medir qué tan eficiente, rápido o lento es un algoritmo cuando maneja una cantidad enorme de datos.

No mide el tiempo en segundos (porque un computador rápido iría más veloz que uno viejo), sino que **mide cuántos pasos o cuánta memoria necesita tu código a medida que crecen tus datos.**

- **O(1) (Constante):** Es la más rápida. No importa si tienes 10 o 10 millones de datos, tarda lo mismo (ej. `get` en un ArrayList o `put` en un HashMap).

- **O(n) (Lineal):** El tiempo crece según la cantidad de datos (n). Si tienes 1,000 datos, podría tardar 1,000 pasos (ej. buscar a alguien en una lista común).

Al principio de la computación comercial, la memoria RAM era carísima y los procesadores eran lentos. Los ingenieros se vieron obligados a analizar su código porque **los sistemas se congelaban o se quedaban sin memoria**.
## 1_==Importante==
1. 1. **Lo de la izquierda (`List`, `Set`, `Map`):** Es el **RANGO** o la **FUNCIÓN**. Define qué "promete" hacer el objeto. Si dices `List`, prometes que los datos tendrán un orden y un índice.
2. **Lo de la derecha (`new ArrayList`, `new LinkedList`):** Es el **MOTOR** o la **ESTRATEGIA**. Define cómo se organiza la memoria internamente para cumplir esa promesa.
## 2_Los "Superpoderes"
	
Cuando eliges el motor de la derecha, estás eligiendo qué superpoder será más fuerte:

- Si eliges `new ArrayList<>`, el superpoder es **VELOCIDAD DE LECTURA** (encuentra el índice 500 al instante).
- Si eliges `new LinkedList<>`, el superpoder es **AGILIDAD DE CAMBIO** (mete o saca elementos en el medio sin despeinarse).
- Si eliges `new TreeSet<>`, el superpoder es **ORDEN AUTOMÁTICO** (él mismo acomoda los números o letras mientras los vas metiendo).
	
	```java
	// "Prometo que será una LISTA, y hoy quiero que el motor sea un ARRAY"
	List<Paciente> lista = new ArrayList<>(); 
	
	// Pero si mañana tu app de IMC tiene miles de pacientes y borras muchos...
	// ¡Solo cambias el motor y el resto del código sigue igual!
	List<Paciente> lista = new LinkedList<>(); 
	```

## 3_Tabla comparativa 

|Estructura (Izquierda + Derecho)|🔍 Buscar un elemento específico (`.contains()`)|🎯 Acceso Directo (`.get(i)` o por Clave)|➕ Insertar / Borrar un dato (`.add()` / `.remove()`)|El veredicto de su Big O|
|---|---|---|---|---|
|**`List`** con `new ArrayList<>()`|**O(n)** (Lento: debe recorrer uno por uno con un bucle hasta hallarlo).|**O(1)** (Instantáneo: sabe exactamente en qué posición de memoria está el índice).|**O(n)** (Lento: si borras el primero, tiene que mover todos los demás un espacio hacia atrás).|**Excelente para leer por posición**, malo para buscar por valor o insertar en medio.|
|**`List`** con `new LinkedList<>()`|**O(n)** (Lento: camina nodo por nodo siguiendo las flechas de la cadena).|**O(n)** (Lento: para ir al índice 500, debe pasar primero por los 499 anteriores).|**O(1)** (Instantáneo: solo rompe dos flechas de la cadena y conecta el nuevo nodo).|**Excelente para insertar/borrar seguido**, pésimo para accesos aleatorios por índice.|
|**`List`** con `new CopyOnWriteArrayList<>()`|**O(n)** (Lento).|**O(1)** (Instantáneo).|**O(n)** (¡Muy lento! Tiene que duplicar todo el arreglo completo en memoria cada vez).|**Solo sirve si casi nunca vas a modificar datos** y compartes la lista entre muchos hilos.|
|**`List`** con `List.of(...)`|**O(n)** (Lento).|**O(1)** (Instantáneo).|**Prohibido** (Lanza error. No tiene la capacidad de cambiar de tamaño).|**Ideal para datos fijos y de solo lectura**.|
|**`Set`** con `new HashSet<>()`|**O(1)** (Instantáneo: calcula el "código hash" del dato y va directo a ver si existe).|**No aplica** (No tiene índices, no puedes pedir el elemento "número 3").|**O(1)** (Instantáneo: calcula el hash y lo guarda directamente).|**El rey de la velocidad para búsquedas por valor** y asegurar que nada se repita.|
|**`Set`** con `new LinkedHashSet<>()`|**O(1)** (Instantáneo).|**No aplica** (No tiene índices).|**O(1)** (Instantáneo, aunque gasta un poquito más de memoria para recordar el orden).|**Igual de rápido que el HashSet**, pero respetando el orden en que metiste los datos.|
|**`Map`** con `new HashMap<>()`|**O(1)** (Instantáneo buscando por su clave principal).|**O(1)** (Instantáneo: le das la clave y te devuelve el valor de inmediato).|**O(1)** (Instantáneo: guarda la pareja en su casilla correspondiente).|**La estructura más eficiente** si tienes un identificador único (como un ID o Cédula).|

## 4_Un poco de hostoria
Esta es la historia de cómo los programadores "chocaron contra la pared" y descubrieron la necesidad del Big O:

### 1_El primer intento: El Arreglo Fijo (Array)

En los primeros lenguajes (como C o las primeras versiones de Java), solo existían los arreglos tradicionales. Le decías a la computadora: _"Resérvame espacio para 10 usuarios"_.

- **Lo interesante:** Acceder al usuario número 5 era instantáneo (**O(1)**).
- **El gran problema:** Si llegaba el usuario número 11, el sistema fallaba. No se podía agrandar. Tenías que crear un arreglo nuevo más grande y copiar los 10 anteriores uno por uno. ¡Eso era lentísimo!

### 2_La evolución al `ArrayList` (El "Arreglo Inteligente")

Para solucionar lo anterior, crearon el `ArrayList`. Dijeron: _"Hagamos una clase que maneje un arreglo interno y, cuando se llene, ella misma se duplique en secreto y mueva los datos"_.

- **El nuevo problema:** Los ingenieros notaron que si tenían una lista de 1,000,000 de personas en un banco y querían **insertar un nuevo cliente en la posición número 1**, el `ArrayList` tenía que mover 999,999 registros un espacio hacia la derecha en la memoria para abrirle campo al nuevo. El servidor se ponía lento con cada inserción. Descubrieron el **O(n)** de la peor manera.

### 3_La solución radical: La Lista Enlazada (`LinkedList`)

Al ver que mover datos en memoria era costoso, un ingeniero dijo: _"¿Y si en vez de un bloque continuo, guardamos los datos dispersos en la memoria y hacemos que cada dato tenga un papelito que diga dónde está el siguiente?"_. Así nació la `LinkedList`.

- **Lo interesante:** Insertar al inicio era instantáneo (**O(1)**), solo cambiabas los papelitos (punteros).
- **La nueva pared:** Cuando quisieron buscar al cliente en la posición 800,000, se dieron cuenta de que la computadora no podía saltar directo allá. Tenía que leer el papelito del 1, luego el del 2, luego el del 3... hasta llegar al 800,000. Volvieron a caer en **O(n)** para la lectura.

### 4_El momento "Eureka": El `HashMap`

Los ingenieros se dieron cuenta de que buscar por posición o recorrer listas siempre los llevaba a un callejón sin salida cuando los datos crecían a millones. Dijeron: _"Necesitamos buscar por el dato mismo (el ID), no por dónde está guardado"_.

Inventaron las funciones Hash: un algoritmo matemático que agarra el ID de un usuario (ej. `ID: 1020`) y calcula inmediatamente una posición matemática única en la memoria (ej. _Casilla 45_).

- **El gran descubrimiento:** No importa si tienes 10 usuarios o 50 millones; pones el ID en la fórmula y te dice _"Está en la Casilla 45"_. ¡Saltas directo en un solo paso! Habían domado al monstruo y alcanzado el **O(1) puro**.

# 15_Recorrer listas 
_"entre más poderes más lento"_ es una gran verdad en Java. Los bucles más modernos y con más "poderes" visuales a veces añaden una pequeña carga extra detrás de escena.

Vamos a analizar todas las formas de recorrer una lista con `for` y `while`, de la más directa (y rápida) a la más avanzada:

## 1_El For Tradicional (Por índice) 🏎️

Es el clásico `for (int i = 0; i < lista.size(); i++)`.

- **Cómo funciona:** Usa una variable contadora (`i`) para pedirle directamente a la lista el elemento en esa posición usando `.get(i)`.
- **Velocidad (Big O):** En un `ArrayList` es **O(n)** y es **el más rápido de todos**. No crea objetos extra en memoria. Es directo al grano.
- **Limitación:** Solo funciona bien en `ArrayList`. Si intentas usar este `for` en un `linkedList`, el rendimiento se destruye a **O(n²)** (se vuelve lentísimo), porque para cada `i`, la lista enlazada tiene que volver a caminar desde el principio.

 **El Clásico (`for` con índice):**
```java
   for (int i = 0; i < lista.size(); i++) {
	System.out.println(lista.get(i));
}
// Úsalo solo si necesitas saber la posición (ej: "Borrar solo los pares").
```
		
## 2_El For-Each (For mejorado) 🔄

Es el `for (UserDTO usuario : lista)`.

- **Cómo funciona:** Java elimina el contador `i`. Por debajo, Java usa un objeto oculto llamado **`Iterator`** que va saltando al "siguiente" elemento automáticamente.
- **Velocidad (Big O):** Sigue siendo **O(n)**. Es imperceptiblemente un poquito más lento que el tradicional porque crea ese objeto `Iterator` en memoria, pero hoy en día los computadores ni lo sienten.
- **Ventaja:** Funciona igual de rápido tanto en `ArrayList` como en `LinkedList`.
- **Limitación:** Está limitado. **No puedes modificar el tamaño de la lista** adentro (si haces `lista.remove()` dentro de este for, Java romperá tu programa con un error llamado `ConcurrentModificationException`). Tampoco tienes la variable `i` si necesitas saber en qué posición vas.

El `for` clásico (`for i=0...`) tiene un problema: **es muy manual**. Tienes que gestionar el índice `i`, revisar que no te pases del tamaño (`size`) y luego sacar el objeto con `get(i)`. Es fácil equivocarse y que el programa explote.

El **For-Each** dice: _"Java, tú sabes cuántos elementos hay, solo dame el objeto de cada vuelta"_
		
### 1_Más legible Se lee como "Para cada **Paciente p** dentro de **lista**...".
**Más seguro:** Es imposible que te pases del índice (no hay `IndexOutOfBoundsException`).
	
### 2_La lógica del For-Each

Se escribe así: `for (Clase nombreVariable : nombreColeccion)`

1. **Clase:** El tipo de dato que hay dentro (ej: `Paciente`).
2. **nombreVariable:** El nombre que tú quieras darle al objeto en esa vuelta (ej: `p, persona, otrasPersonas`).
3. `:` Significa "dentro de" o "de la".
4. **nombreColeccion:** Tu lista o array.
### 3_El For-Each
```java
 for (Paciente p : lista) {
	// Aquí puedes hacer DE TODO sin errores raros:
	if (p.getPeso() > 100) {
		System.out.println("Alerta con " + p.getNombre());
	}
	// Puedes usar 'break' para detenerte o 'return'
}
// Es el estándar para leer datos.
```
- **Por qué evita errores:** Porque Java gestiona el inicio y el fin de la lista por ti.
- **Por qué es mejor que la Lambda:** Si hay un error dentro del `if`, el **Debugger** de IntelliJ se detendrá exactamente en esa línea y podrás ver cuánto vale el peso de `p` en ese momento.

	3.

## 3_El `.forEach()` con Lambdas (Estilo Funcional) ⚡
Es el `lista.forEach(usuario -> { ... });` (Muy usado en Spring).

- **Cómo funciona:** Es un método propio de la lista que recibe una función flecha (lambda).
- **Velocidad (Big O):** **O(n)**. Es excelente para código limpio y legible, pero internamente tiene un poquito más de "decoración" de código, por lo que en pruebas extremas de rendimiento es un ápice más lento que el For-Each común.
- **Limitación:** Al igual que el anterior, no tienes índice y no puedes alterar la lista mientras la recorres.

 **El `forEach` con Lambda (Nivel avanzado):**  Es una sola línea de código que se usa mucho en Java moderno:
```java
   (nombre de mi lista).forEach(p -> System.out.println(p.getNombre()));
   
   (nombre de la lista).stream()                  // 1. Ponemos los datos en la cinta
	.filter(p -> p.getNombre().equals("Maria")) // 2. El filtro saca a las que no se llamen Maria
	.forEach(p -> System.out.println(p));        // 3. Al final, mostramos lo que quedó
```
Efectivamente, al igual que el operador ternario, el `forEach` con Lambda (`->`) puede volverse un dolor de cabeza si se abusa de él.

- **¿Cuándo falla?** No es que el programa se rompa, sino que se vuelve **imposible de depurar (debuggear)**. Si pones mucha lógica dentro de esa línea y algo falla, IntelliJ no te dirá exactamente qué parte de la línea falló. Además, dentro de una Lambda no puedes usar `break` ni `continue`, lo cual te quita control.

- **Regla de oro:** Úsalo solo para tareas ultra simples, como imprimir algo (`System.out::println`). Para lógica de negocios (como calcular IMC y validar datos), el **For-Each normal** (el de los dos puntos `:`) es mucho mejor.

- si quiero poner algo de lógica compleja es difícil de hacer y se vuelve complejo con el tiempo

## 4_El bucle `While` (El hermano menor) 🛑

El `while` no tiene "derivaciones" como el for.

- **Cómo funciona:** Se usa principalmente de dos formas: con un contador manual (idéntico al for tradicional) o combinado con un `Iterator` explícito (`while(iterator.hasNext())`).
- **Análisis:** No es que no se pueda mejorar, es que el `while` está diseñado para cuando **no sabes cuántas vueltas vas a dar** (por ejemplo, leer líneas de un archivo externo hasta que se acabe). Para listas, usar `while` suele ser incómodo y propenso a errores (como olvidar sumar el contador y crear un bucle infinito que tumbe tu servidor de Spring).
    
### 1_Ejemplo
🚨 El problema con el For-Each común

Si tú intentas borrar un elemento usando un `for` normal, Java se confunde. Imagina que tienes 5 elementos y borras el número 2; ahora el que era el 3 pasa a ser el 2, las posiciones se mueven y Java pierde el control de por dónde iba caminando. Para protegerse, Java lanza un error llamado `ConcurrentModificationException` y detiene el servidor.

🦸‍♂️ La Solución: El Iterator (El guía turístico)

El **`Iterator`** es un objeto especial que actúa como un "guía turístico". Él toma el control absoluto de la lista. Sabe exactamente en qué elemento está parado, cuál sigue, y si borras algo, él mismo reacomoda la lista internamente en tiempo real para no tropezar.

```Java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class EjemploSuperpoder {
    public static void main(String[] args) {
        
// 1. Creamos una lista de precios (del lado derecho un ArrayList)
        List<Integer> precios = new ArrayList<>();
        precios.add(10);
        precios.add(50); // Queremos borrar los mayores a 40
        precios.add(20);
        precios.add(80); // Queremos borrar los mayores a 40
        precios.add(30);

        System.out.println("Lista original: " + precios);

// 2. Le pedimos a la lista que nos dé su "guía turístico" (Iterator)
        Iterator<Integer> guia = precios.iterator();

// 3. Usamos el bucle WHILE: "Mientras el guía vea que hay un elemento adelante..."
        while (guia.hasNext()) {
            
// El guía da un paso hacia adelante y nos da el número actual
            Integer precioActual = guia.next(); 
            
// 4. Aplicamos la condición (Borrarnos los productos caros mayores a 40)
            if (precioActual > 40) {
                
	// ¡EL SUPERPODER! Le decimos al guía que lo borre.
// El guía borra el elemento de la lista de forma segura sin romper nada.
                guia.remove(); 
            }
        }

        // 5. Verificamos el resultado
        System.out.println("Lista limpia (sin mayores a 40): " + precios);
    }
}
```

#### 1_Explicación de los 3 "poderes" del Iterator:

1. **`precios.iterator()`**: Inicializa al guía al principio de la lista (en la posición "-1", antes del primer elemento).
2. **`guia.hasNext()`**: Devuelve un `true` o `false`. Solo pregunta: _"¿Hay un elemento más adelante o ya se terminó la lista?"_.
3. **`guia.next()`**: Hace dos cosas a la vez: salta al siguiente elemento y te entrega el valor de ese elemento.
4. **`guia.remove()`**: Borra el **último elemento** que te entregó `next()`. Como el guía sabe exactamente dónde está parado, lo elimina de la lista original de forma segura.

#### 2_Nota moderna (Java 8+)

Hoy en día, Java añadió un método más corto que hace exactamente esto mismo por debajo en una sola línea, usando lambdas. Si en Spring solo quieres borrar sin hacer logs ni lógica compleja, puedes usar:

```java
// Esto hace exactamente lo mismo que el While + Iterator de arriba:
precios.removeIf(precio -> precio > 40);
```

## 5_Cuadro Comparativo de los "Compañeros de la Lista"

| **Bucle**               | **¿Es rápido?**  | **¿Sirve para `LinkedList`?** | **¿Puedo borrar elementos dentro?**                      | **¿Cuándo usarlo en Spring?**                                                                |
| ----------------------- | ---------------- | ----------------------------- | -------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **For Tradicional**     | 🥇 El más rápido | ❌ No, se vuelve lentísimo     | 95% de las veces no. Solo si manejas el índice al revés. | Para algoritmos matemáticos puros o exprimir el máximo milisegundo.                          |
| **For-Each**            | 🥈 Muy rápido    | Sí, perfecto                  | ❌ No, lanza error                                        | El estándar para procesar datos, enviar correos, o mapear DTOs simples.                      |
| **`.forEach()` Lambda** | 🥉 Rápido        | Sí                            | ❌ No                                                     | Para código moderno, limpio y corto (1 o 2 líneas de lógica).                                |
| **While + Iterator**    | 🥈 Muy rápido    | Sí                            | **¡SÍ! Es el único.**                                    | Cuando necesitas ir recorriendo la lista y **borrando** elementos que cumplan una condición. |

¡Qué gran análisis estás haciendo! Ahora dime:

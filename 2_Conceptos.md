[[1_poo.pdf#search=tema: Principios Avanzados de Programación Orientada a Objetos|1_poo, p.33]]
# 1_Cohesión: "Hacer una sola cosa y hacerla bien"[[1_poo.pdf#search=Los principios avanzados|1_poo, p.33]]
^86881c
La cohesión mide qué tan enfocada está una clase. Una clase con **Alta Cohesión** es como un **especialista**: si tienes un "Chef", él solo cocina; no limpia el piso ni arregla la electricidad.

- **En el código:** Si tu clase `Factura` solo calcula totales y aplica descuentos, tiene cohesión alta. Si esa misma clase también intenta conectarse a la base de datos y enviar correos, tiene **Baja Cohesión** (se vuelve una "Clase Dios" que hace de todo y es difícil de arreglar).
- **Beneficio:** Es más fácil de probar y modificar sin romper cosas ajenas.
- **Mucha Cohesión = BUENO (Súper Pro):** Significa que tu clase está muy enfocada. Si la clase se llama `Calculadora`, solo calcula. Es fácil de arreglar porque sabes exactamente dónde buscar el fallo.
	1. Separamos las responsabilidades en expertos de una sola cosa.
		```java
			class CalculadoraSalario {
			    void calcular(Empleado e) { ... }
			}
				class EmpleadoRepository {
				    void guardar(Empleado e) { ... }
				}
				
				class ServicioEmail {
				    void enviarEmail(String mensaje) { ... }
			}
		```
		
- **Baja Cohesión = MALO:** Es cuando una clase "hace de todo" (lo que tú llamabas "mucha cohesión"). Si la clase `Factura` calcula el precio, lo guarda en la base de datos y además imprime un PDF, es un caos. Si falla el PDF, ¡podrías romper el cálculo del dinero sin querer!
	1. Esta clase hace demasiadas cosas que no tienen que ver entre sí.
		```java
		class GestorEmpleado {
			void calcularSalario() { ... }
			void guardarEnBaseDeDatos() { ... }
			void enviarEmailDeBienvenida() { ... }
		}
		```
# 2_Acoplamiento: "Qué tan pegados están los cables"

El acoplamiento mide la dependencia entre clases. Buscamos siempre un **Bajo Acoplamiento** 

- **La Analogía:** Imagina los audífonos de un avión antiguo que tenían dos entradas raras. Si se rompen, solo puedes comprar esos. Eso es **Alto Acoplamiento**. En cambio, los audífonos con entrada USB o Bluetooth tienen **Bajo Acoplamiento**: puedes conectarlos a cualquier dispositivo porque usan un estándar (una interfaz).

- **Mucho Acoplamiento = MALO:** Significa que las clases dependen demasiado entre sí. Si mueves un cable en la clase A, explota la clase B. Es como la **Composición** [[1_conceptos#^947696]] si el "dueño" muere, la "parte" muere. Eso hace que el código sea rígido y difícil de cambiar
	- Aquí la clase `Impresora` depende **específicamente** de un `DocumentoPDF`. Si mañana quieres imprimir un `Excel`, tienes que modificar la clase `Impresora`.
		- ```java
			class Impresora {
			    void imprimir(DocumentoPDF pdf) { // <--- Está amarrada a PDF
			        System.out.println("Imprimiendo: " + pdf.contenido);
				    }
			}
		  ```

- **Bajo acoplamiento:** el uso de las **`interfaces`** son buenas para lograr un **Bajo acoplamiento**  ya que cuando se implementa interfaces nos obligan a usar sus métodos de lo contrario saldrá error 
	- Usamos una interfaz o una clase general. La `Impresora` no sabe qué está imprimiendo, solo sabe que es algo "imprimible".
		- ```java
		interface Imprimible {
				String getContenido();
		}
				
			class Impresora {
			    void imprimir(Imprimible documento) { // <--- No le importa si es PDF, Excel o Texto
				 System.out.println("Imprimiendo: " + documento.getContenido());
				 }
			}

		  ```
	- ###### Qué tiene que ver con el Acoplamiento?
		- **Sin Interfaces (Alto Acoplamiento):** Tu clase `Tienda` tiene una variable de tipo `TarjetaVisa`. Si mañana quieres aceptar `PayPal`, tienes que romper el código de la `Tienda` para cambiarlo. ¡Están pegadas con pegamento fuerte!
		
		- **Con Interfaces (Bajo Acoplamiento): [[1_conceptos#^77d6df]]** Tu clase `Tienda` tiene una variable de tipo `MetodoDePago` (la interface). A la tienda no le importa si el pago es con Visa, PayPal o Bitcoin; ella solo llama a `pagar()`.
		
		- **Resultado:** Puedes cambiar el banco o la moneda sin tocar una sola línea de la clase `Tienda`. El código es flexible como un cable USB.
		
		- **Bajo Acoplamiento = BUENO (Súper Pro):** Las clases son independientes. Se hablan, pero no se necesitan para existir. Si cambias cómo funciona la clase A, la clase B ni se entera. Esto permite que arregles un método sin que se dañe nada más.
		
		- **En el código:** Si cambias la base de datos de SQL a MongoDB y tienes que reescribir todo tu sistema de usuarios, tenías un acoplamiento muy alto
		- **Beneficio del bajo acoplamiento:** El sistema es flexible. Puedes cambiar una pieza sin que todo el edificio se derrumbe.


1. ¿Quieres arreglar un método sin dañar nada más? Necesitas **Bajo Acoplamiento**.
2. ¿Quieres que tu clase sea fácil de entender y arreglar? Necesitas **Alta Cohesión**.
# 3_Re-utilización de código (No reinventes la rueda)

**¿Qué es?** Es la capacidad de usar piezas de software que ya programaste en nuevos proyectos para no repetir código ni cometer los mismos errores.

- **En palabras sencillas:** Escribir herramientas tan bien hechas que te sirvan para el futuro.
    
- **Ejemplo del documento:** Si creas una buena clase `Logger` (que sirve para registrar los errores del sistema), deberías poder usar ese mismo archivo en tu próxima app de escritorio o en tu app móvil sin tener que cambiarle una sola línea de código.

- Resumen de cómo aporta cada uno a la reutilización

| Concepto         | Cómo reutiliza                                                           |
| ---------------- | ------------------------------------------------------------------------ |
| **Herencia**     | Copia automáticamente lo que hizo el padre en los hijos.                 |
| **Composición**  | Permite usar una clase pequeña como una "pieza de LEGO" dentro de otras. |
| **Polimorfismo** | Permite usar un mismo método para diferentes tipos de objetos.           |
| **Interfaces**   | Permite que diferentes clases compartan el mismo "diseño" o contrato.    |

# 4_Manejo de Excepciones (Atrapar los errores con elegancia) [[1_poo.pdf#search=2) Conceptos Clave|1_poo, p.22]]

**¿Qué es?** Es capturar los errores para que el programa no se estrelle o se cierre de golpe.

- **Ejemplo del documento:** Si una persona intenta pagar y falla, el sistema debería lanzar una excepción como `PagoRechazadoException`. Esto le muestra un mensaje amable al usuario en lugar de cerrar la aplicación.

1. No es un error de sintaxis (escribir mal una palabra), es un **error en tiempo de ejecución**.

- **La Analogía:** Estás siguiendo una receta (tu programa) y dice "agrega dos huevos". Vas a la nevera y no hay huevos. La receta no está mal escrita, pero la realidad impidió continuar.
- **En el Código:** Intentar dividir por cero, abrir un archivo que no existe o conectar a una base de datos sin internet.

2. La Estructura de Seguridad: `try-catch-finally`

	Este es el protocolo de emergencia de Java:
	
	- **`try` (El Experimento):** Metes aquí el código "peligroso" que podría fallar. _"Intenta abrir este archivo"_.
	- **`catch` (La Red de Seguridad):** Si el código en el `try` falla, el programa salta aquí en lugar de cerrarse. _"Si no hay archivo, avísale al usuario y usa uno por defecto"_.
	- **`finally` (La Limpieza):** Este bloque se ejecuta **siempre**, haya habido error o no. Es vital para cerrar conexiones o liberar memoria. _"No importa si hubo huevos o no, apaga la estufa al terminar"_.

3. Jerarquía y Tipos de Excepciones

	Java organiza los errores como una **Herencia** (aplicando lo que vimos en la Temática 3):
	
	- **Checked Exceptions (Verificadas):** El compilador te obliga a manejarlas (ej. leer un archivo). Es como si Java te dijera: "Sé que esto puede fallar, dime qué harás si pasa".
	- **Unchecked Exceptions (No verificadas):** Errores de lógica (ej. acceder a una posición de un arreglo que no existe). Suelen ser culpa del programador.

4. Excepciones Personalizadas

	A veces, los errores estándar de Java (`IOException`, `NullPointerException`) no son suficientes para tu negocio.
	
	- **Ejemplo:** En un sistema bancario, si alguien intenta retirar más dinero del que tiene, no es un error de sistema, es un error de negocio. Creas una clase `SaldoInsuficienteException` que hereda de `Exception`. Esto hace que tu código sea mucho más legible y profesional.

```java
public void realizarRetiro(double cantidad) throws SaldoInsuficienteException {
    try {
        if (cantidad > saldoActual) {
            // Lanzamos nuestra propia excepción personalizada
            throw new SaldoInsuficienteException("No tienes fondos bastantes");
        }
        saldoActual -= cantidad;
    } catch (SaldoInsuficienteException e) {
        // Capturamos el error y lo gestionamos sin que el programa explote
        System.out.println("Error de transacción: " + e.getMessage());
    } finally {
        System.out.println("Sesión bancaria finalizada.");
    }
}

```

# **5_Los Principios SOLID (Gia de diseño como piezas de lego )**

El documento menciona que, aunque no están en el sílabo detallado, los **Principios SOLID** son la base teórica para lograr esa alta cohesión y bajo acoplamiento  Son 5 reglas de oro:

- **SOLID:** No es "Qué" escribir, sino "Cómo" organizar
	1. **S ingle Responsibility (Responsabilidad Única)** Una clase, una sola tarea como la [[2_conceptos#^86881c]] .
		 - Una clase debe tener una, y solo una, razón para cambiar". Esto significa que si mañana cambias el formato de tus reportes, no deberías tener que tocar la clase que calcula los salarios.
		 
	2. **O pen/Closed (Abierto a extensión, cerrado a modificación)**  El código debe estar **abierto** para extenderse (añadir funciones) pero **cerrado** para modificarse (no romper lo que ya sirve).
		- Las entidades de software (clases, módulos, funciones) deben estar **abiertas para la extensión**, pero **cerradas para la modificación**
		- si necesitas añadir una nueva funcionalidad, deberías poder hacerlo **agregando código nuevo**, no cambiando el código que ya escribiste, probaste y funciona.
		- ###### Ejemplo =>
			- Imagina que tienes una clase que calcula descuentos. Cada vez que llega un nuevo tipo de cliente, tienes que entrar a la clase y añadir un `if`.
				- ```java
				  class CalculadorDescuento {
					    public double aplicarDescuento(String tipoCliente, double total) {
					        if (tipoCliente.equals("VIP")) {
					            return total * 0.80;
					        } else if (tipoCliente.equals("PREMIUM")) { // <-- Tuviste que MODIFICAR la clase
					            return total * 0.90;
					        }
					        return total;
					    }
					}
				  ```
			- **_Problema:_** Cada vez que hay un nuevo descuento, modificas código viejo. Si te equivocas en un signo, rompes los descuentos que ya funcionaban.
			
			- Aquí es donde ocurre la magia. Cerramos la clase principal y la abrimos mediante una interfaz.
				- ```java
				  // 1. Definimos el "contrato" (Abierto a extensión)
					interface Descuento {
						double aplicar(double total);
					}
					
					// 2. Creamos clases para cada caso nuevo (Sin tocar lo anterior)
					class DescuentoVIP implements Descuento {
						public double aplicar(double total) { return total * 0.80; }
					}
					
					class DescuentoPremium implements Descuento {
						public double aplicar(double total) { return total * 0.90; }
					}
					
					// 3. La clase principal está CERRADA. No cambia nunca, solo recibe "descuentos".
					class ProcesadorDePedido {
						public void procesar(double total, Descuento descuento) {
							double totalFinal = descuento.aplicar(total);
							System.out.println("Total con descuento: " + totalFinal);
						}
					} 
				  ```
				  
			- Si mañana llega el "Descuento de Navidad", no tocas `ProcesadorDePedido`. Simplemente creas una clase nueva `DescuentoNavidad` que implemente la interfaz y listo. **Cero riesgo de romper código antiguo.** 

	3. **L iskov Substitution (Sustitución de sub-clases)** Si tienes una clase hija, esta debe poder reemplazar al padre sin que el programa explote.
		- Si una clase `B` hereda de una clase `A`, entonces deberíamos poder usar objetos de la clase `B` en cualquier lugar donde usemos objetos de la clase `A` **sin que el programa se rompa o se comporte raro**
		- En palabras simples: Una clase hija debe ser capaz de hacer **todo** lo que el padre hace, cumpliendo las expectativas. No debe "mentir" sobre sus capacidades.
		
			- **Ejemplo**
				- ```java
					class Ave {
					    void volar() {
					        System.out.println("Estoy volando...");
					    }
					}
					
					class Avestruz extends Ave {
					    @Override
					    void volar() {
					        // ¡ERROR! El avestruz no puede volar. 
					        // Lanzar una excepción aquí rompe el programa de quien esperaba que el ave volara.
					        throw new RuntimeException("No puedo volar, soy un avestruz");
					    }
					}
					
					// El desastre en el código principal:
					void hacerVolar(Ave ave) {
					    ave.volar(); // Si le pasas un Avestruz, el programa EXPLOTA.
					}

				  ```
				  
			- Para cumplir con Liskov, no debemos forzar a las clases a heredar comportamientos que no pueden cumplir. Usamos **Interfaces** para separar las habilidades.
				- ```java
					class Ave {
					    void comer() {
					        System.out.println("Comiendo...");
					    }
					}
					
					interface AveVoladora {
					    void volar();
					}
					
					class Gorrion extends Ave implements AveVoladora {
					    public void volar() { System.out.println("El gorrión vuela"); }
					}
					
					class Avestruz extends Ave {
					    // El avestruz solo hereda lo que SÍ puede hacer (comer).
					    // No implementa AveVoladora.
					}

				  ```
	
	4. **I nterface Segregation (Muchos contratos pequeños mejor que uno gigante)** Mejor muchas interfaces pequeñas que una gigante.
		- Un cliente no debe ser obligado a depender de interfaces que no utiliza.
		- En cristiano: Es mejor tener **muchas interfaces pequeñas y específicas** que una sola interfaz gigante y genérica. No obligues a una clase a implementar métodos "vacíos" o que no tienen sentido para ella
		- **Ejemplo:** 
			- Aquí obligamos a todo trabajador a saber programar y cocinar.
				- ```java
				  interface Trabajador {
					    void programar();
					    void cocinar();
					}
					
					class Programador implements Trabajador {
					    public void programar() { System.out.println("Escribiendo código");}
					    
					    // PROBLEMA: El programador NO cocina, pero la interfaz lo obliga a poner el método
					    public void cocinar() { 
					        /* Método vacío o lanza error: ¡Mala práctica! */ 
					    }
					}
	
				  ```
				  
			- Dividimos la interfaz gigante en interfaces especialistas.
				- ```java
				  // Interfaces pequeñas y específicas
				interface ProgramadorHabilidad {
					void programar();
				}
				
				interface CocineroHabilidad {
					void cocinar();
				}
				
				// Cada clase toma SOLO lo que necesita
				class DesarrolladorJava implements ProgramadorHabilidad {
					public void programar() {
						System.out.println("Programando en Java...");
					}
				}
				
				class Chef implements CocineroHabilidad {
					public void cocinar() {
						System.out.println("Preparando una lasaña...");
					}
				}
				  ```
			
	5. **D ependency Inversion (Depender de ideas, no de cosas concretas)** Aquí entran las **Interfaces y el Acoplamiento**. No dependas de clases concretas, depende de abstracciones (contratos).
		- Las clases de alto nivel (la lógica importante) no deben depender de clases de bajo nivel (detalles como la base de datos o una librería específica). Ambas deben depender de **abstracciones** (interfaces).
		- Las abstracciones no deben depender de los detalles. Los detalles deben depender de las abstracciones.
		- **Ejemplo:**
			- Aquí la clase `Tienda` está "amarrada" a `PayPal`. Si `PayPal` falla o queremos cambiarlo, la `Tienda` deja de funcionar.
				- ```java
					class PayPal {
					    void procesarPago() { System.out.println("Pagando con PayPal..."); }
					}
					
					class Tienda {
					    private PayPal pago = new PayPal(); // <-- ERROR: Dependencia directa
					
					    void realizarVenta() {
					        pago.procesarPago();
					    }
					}
			
				  ```
				  
			- Introducimos una **interfaz** en medio. Ahora la `Tienda` no sabe qué banco usas, solo sabe que usa un `MetodoPago`.
				- ```java
				  // 1. La Abstracción (El Enchufe)
					interface MetodoPago {
					    void pagar();
					}
					
					// 2. Los Detalles (Las Lámparas)
					class PayPal implements MetodoPago {
					    public void pagar() { System.out.println("Usando PayPal..."); }
					}
					
					class Tarjeta implements MetodoPago {
					    public void pagar() { System.out.println("Usando Tarjeta..."); }
					}
					
					// 3. Clase de Alto Nivel (La Tienda)
					class Tienda {
					    private MetodoPago metodo; // <-- Depende de la interfaz, no de la clase real
					
					    // Inyectamos la dependencia (le pasamos el objeto ya creado)
					    Tienda(MetodoPago metodo) {
					        this.metodo = metodo;
					    }
					
					    void realizarVenta() {
					        metodo.pagar();
					    }
					}

				  ```

   Si la POO es el material de construcción (ladrillos, cemento), SOLID es el **código de ética del arquitecto**.
	- Puedes construir una casa que se mantenga en pie (que el código funcione), pero sin SOLID, quizás para cambiar una ventana tengas que derribar toda una pared.
	- Con SOLID, cambiar esa ventana es tan fácil como quitar un tornillo.







1. calcular el IMC DE UNA PERSONA 
2. que nos deje hacer sacar la hipotenusa de un triangulo rectángulo rectángulo  
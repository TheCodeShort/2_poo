# 1_¿Cómo se nombran las clases? (Reglas de Oro)

En Java existe una convención estándar llamada **PascalCase** para las clases:

- **Mayúscula inicial:** Siempre deben empezar con mayúscula (ej: `Persona`, no `persona`).
- **Singular:** Se recomienda usar el singular porque la clase es el "molde" para **un** solo objeto (ej: `Persona`, no `Personas`).
- **Sin espacios:** Si el nombre tiene dos palabras, ambas van en mayúscula: `CalculadoraImc`.

# 2_Crear la carpeta de origen (`src`)

1. En el panel de la izquierda (donde dice **`9_im`** en tu imagen), haz **clic derecho** sobre el nombre de tu proyecto (la carpeta raíz).
2. Selecciona **New** > **Directory**.
3. Escribe el nombre **`src`** (todo en minúsculas) y pulsa Enter.

4. Decirle a IntelliJ que esa carpeta es de "Código"

A veces IntelliJ no reconoce automáticamente que ahí va el código. Si la carpeta se ve **gris** y no **azul**, haz esto:

1. Clic derecho sobre la carpeta **`src`** que acabas de crear.
2. Busca la opción **Mark Directory as**.
3. Selecciona **Sources Root**. (Ahora la carpeta se pondrá de color **azul**).


# 3_ a tener en cuenta 

- **`void` (Vacío):** Se usa cuando el método hace una acción pero **no devuelve nada**. Es como si le pidieras a alguien: "¡Grita tu nombre!". La persona grita, tú lo oyes, pero no te entrega un papel con el nombre escrito.
    - _Ejemplo:_ `public void imprimirDatos()` -> Solo muestra algo en pantalla.
- **`double` (Tipo de dato):** Se usa cuando el método **calcula algo y te entrega el resultado**. Es como si le pidieras a alguien: "¿Cuánto es 2 + 2?". La persona hace el cálculo y **te devuelve** el número 4 para que tú lo guardes o lo uses después.
    - _Ejemplo:_ Tu método `calculoPeso()`. Necesitamos que nos devuelva el número del IMC para decidir si es "Normal" o "Sobrepeso".

- **Main**
	- Dentro de esa clase, escribe `psvm` y pulsa la tecla **Tab** (es un atajo de IntelliJ que escribe automáticamente `public static void main(String[] args)`).
	- esto nos ayuda a ejecutar el código 
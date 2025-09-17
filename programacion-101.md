## Clase 1 - Qué es la programación

De manera muy simplificada, programar es escribir comandos para que las siga la computadora.
Para ello, en esencia se utilizan dos herramientas: variables y funciones.

#### Qué es una variable?
Es una "cajita" contenedora de información.
Pueden darle el nombre que quieran. Las creamos nosotros y les asignamos un valor.
El valor es lo que está adentro, lo que contiene.
La asignación es una instrucción que se indica con el signo = y se lee de derecha a izquierda.

---

Qué información?
- Números: decimales o enteros
- Texto: llamados strings, se indican con comillas
- Vectores: grupos de números
- Arrays (arreglos o listas)
- Diccionarios (listas con nombres)
- Y mucho más...

---

En Godot las variables se **declaran** escribiendo VAR y luego dándole un nombre:
```gdscript
var texto
```

Por más que diga "texto" está vacía. Esta es solo la creación, sin ponerle ningún valor dentro. Se les puede dar el nombre que uno quiera siempre que no haya otra variable con el mismo nombre.

---

Se les define un **TIPO** (opcional) usando el signo de DOS PUNTOS (:)
```gdscript
var texto: String
```

Esta variable va a contener caracteres o palabras, por eso le decimos a Godot que su tipo será String. Este paso es opcional pero es muy util para que Godot sepa lo que nosotros pretendemos hacer con esta variable.


---

Se les **ASIGNA** un **VALOR** usando el signo IGUAL (=).

```gdscript
var texto: String = "Hola Mundo"
```

Se necesita usar las comillas para que Godot entienda que esas palabras no son parte del código en sí.

Ahora cada vez que Godot lea la variable [texto], verá su contenido, que es ["Hola Mundo"]

---

Hay distintos **TIPOS** de **VALORES** que pueden contener las variables
```gdscript

var texto: String = "Hola Mundo" # Las comillas son importantes

var numero_entero: int = 69 # Los numeros enteros no tienen decimales

var numero_decimal: float = 4.20 # Los numeros decimales son menos precisos

var verdadero_o_falso: bool = true # Puede ser verdadero o falso, nada más

var variable_vacía = null # Null va a dar error al querer usarlo si no se tiene cuidado

```

---

Se pueden realizar operaciones sobre estos valores.
El VAR solo se necesita la primera vez, que es la **declaración**
El resto de las veces cuando hay un simbolo igual (=) son **asignaciones**

```gdscript
var variable_flexible = 2 # Declaración
variable_flexible = "Hola" # Asignación
variable_flexible = true # Asignación
```

Acá, como no le dijimos un tipo explícito, Godot va a permitir que en la variable haya cualquier tipo de información: números, texto, booleanos. Es posible usarlo así, aunque no es lo recomendable.

---



```gdscript
# Esto es un comentario.

# Los comentarios son para los humanos que leen el código.

# La computadora omite los comentarios por completo, no los procesa.

# Todos los renglones que comienzan con # en Godot son comentarios.
```




---

##### Array / Lista
Los arrays contienen una secuencia de valores, por ejemplo: 
Numeros: [1, 2, 3, 4, 5]
Strings: ["Bulbasaur", "Ivysaur", "Venusaur", "Squirtle", "Wartortle"]

Se puede acceder a los valores dentro de la lista de varias maneras, principalmente:

Buscar un valor específico: Usando un **INDICE**
El índice es un número entero que le va a pedir a la lista que le devuelva el valor en la posición indicada:

var pokemon: Array[String] = ["Bulbasaur", "Ivysaur", "Venusaur", "Squirtle", "Wartortle"]

| Indice | Valor       |
| ------ | ----------- |
| 0      | "Bulbasaur" |
| 1      | "Ivysaur"   |
| 2      | "Venusaur"  |
| 3      | "Squirtle"  |
| 4      | "Wartortle" |
La forma de solicitar el valor es el siguiente:

```gdscript
print(pokemon[0]) # imprimirá "Bulbasaur"
print(pokemon[1]) # imprimirá "Ivysaur"
print(pokemon[2]) # imprimirá "Venusaur"
print(pokemon[3]) # imprimirá "Squirtle"
print(pokemon[4]) # imprimirá "Wartortle"
print(pokemon[5]) # causará un ERROR porque no hay un Indice 5
```
Ahora, si queremos escribir todos los nombres de los pokemon, no es cómodo tener que escribir cada línea una por una... si tan solo hubiera una forma más simple...

Cuál es el patrón que siguen los números de los ejemplos?

---

#### Bucles

Los bucles son una manera de ejecutar las mismas líneas de código varias veces.

Es como decir "por cada miembor de esta lista, segui las siguientes insturcciones"
Ejemplo:
```gdscript
for indice in 5: #Por cada número hasta llegar a 5
	print("Indice: %s", indice) # 
	print("Pokemon: %s", pokemon[indice])

```

Esta función imprimirá lo siguiente:

```
Índice: 0
Pokemon: Bulbasaur
Índice: 1
Pokemon: Ivysaur
Índice: 2
Pokemon: Venusaur
Índice: 3
Pokemon: Squirtle
Índice: 4
Pokemon: Wartortle
```

---

##### Diccionario
Los diccionarios son parecidos a los array, pero pueden contener más información.

Por ejemplo, respecto a los Pokemon.
Imaginemos que tenemos la entrada de Pokedex de Bulbasaur.
Vamos a ver qué información contiene, a grandes rasgos:

```gdscript
var diccionario_bulbasaur: Diccionario {
"ID" = 001,
"Nombre" = "Bulbasaur",
"HP" = 85.5
"Ataque" = 120,
"Defensa" = 130,
"Velocidad" = 80,
"Habilidades" = ["Latigo cepa", "Rayo solar", "Semilla drenadora", "Hoja Cortante"],
"Desmayado" = false
}
```

---

Los diccionarios son similares a las tablas de Excel:

| Clave       | Valor                                                               |
| ----------- | ------------------------------------------------------------------- |
| ID          | 001                                                                 |
| Nombre      | Bulbasaur                                                           |
| HP          | 85.5                                                                |
| Ataque      | 120                                                                 |
| Defensa     | 130                                                                 |
| Velocidad   | 80                                                                  |
| Habilidades | ["Latigo Cepa", "Rayo Solar", "Semilla Drenadora", "Hoja Cortante"] |
| Desmayado   | false                                                               |

Este patrón de poder ponerle un nombre a cada valor, para poder tener pares, se llama diccionario.

Los diccionarios contienen **Claves**, que son los que están a la izquierda y **Valores**, los de la derecha.

Para usar estos valores, en lugar de usar un **Indice** como en los Arrays, podemos utilizar las claves:

```gdscript
print(diccionario_bulbasaur["Nombre"]) # Imprime "Bulbasaur"
```

---

#### Qué es una función?

Es una serie de instrucciones escritas para procesar variables.

Se pueden imaginar como si fueran una especie de **máquina**.

Puede tomar varios inputs (entradas) llamadas **parámetros** y generar un output (salida).
Los inputs suelen ser variables o valores, por ejemplo podemos darle 2 números y obtener el resultado de una operación matemática:


```gdscript
func sumar_numeros(numero_1: int, numero_2: int) -> int:
	var resultado : int = numero_1 + numero_2
	return resultado
```

---

Cada linea de código es una instrucción específica.
Pero las funciones también sirven para hacer cosas más complejas. 
Imaginen una cafetera, los inputs son granos de café y agua, opcional crema, el output es la taza de café.

```gdscript
func hacer_taza_de_cafe(agua, granos, crema) -> cafe:

func lavar_ropa(ropa, agua, jabon) -> ropa:
```

---

Como funciona **PRINT** y la **CONSOLA**:
```gdscript
print(1) # Mostrará un 1 en la CONSOLA 

print(2+2) # Mostrará un 4 en la CONSOLA

print("Hola") # Mostrará Hola en la CONSOLA
```

---

Diferencia entre **LLAMAR** y **DECLARAR** una función:
```gdscript
func _ready():
	print(sumar_numeros(1, 2)) # Mostrará un 3 en la CONSOLA
	
func sumar_numeros(numero_1: int, numero_2: int) -> int:
	var resultado : int = numero_1 + numero_2
	return resultado
```

En programación, por defecto cada línea se ejecuta una detrás de otra de manera secuencial desde la DECLARACIÓN hasta el RETURN
RETURN es una forma de comunicar varias funciones entre sí.

---

Los valores retornados por RETURN pueden guardarse en VARIABLES

```gdscript
var numero_1 = 1
var numero_2 = 2

var resultado_suma: int = sumar_numeros(numero_1, numero_2)

print(resultado_suma)

```

---

![Exact Instructions Challenge](https://www.youtube.com/watch?v=cDA3_5982h8)


---

### Clase 2:
# Interfaz de Godot

#### Qué es un Nodo?
TBD

#### Qué es una Escena?

Cómo crear una escena

Cómo destruir una escena


#### Qué es el inspector? EXPORTS
TBD


#### Qué es una clase?

Es una clasificación que se usa para que Godot sepa qué tipo de 
TBD

Instancia vs Static

Uso de Memoria, free vs queue free

#### Qué es un script?

Es un archivo de texto que va a contener las variables y funciones que va a usar un elemento del juego. Son las instrucciones que van a alterar su comportamiento.

En Godot, casi todo puede contener un script hecho por nosotros. Todo es customizable.

Lo que hay que tener en cuenta es que la mayoría de estos elementos vienen con un script ya hecho por Godot que no podemos editar (por ahora) pero podemos ver en la documentación o en la web de Godot (en github).

---
### Cómo se comunican los nodos?

#### Qué es el arbol de nodos?

Cuando ejecutamos un juego de Godot, el Sistema Operativo crea una ventana, eso es lo equivalente a un [Viewport] en Godot.

Este Viewport es un [[nodo]] que se encarga de [renderizar] todo lo que tiene adentro y se le conoce como [Root] o [Nodo Raíz]

Todo lo que haya en el juego van a ser **nodos hijos de este Nodo Raíz** a menos que tu juego tenga más de una ventana, que también se puede hacer.
A esta colección de nodos se les llama Scene Tree, o árbol de escenas, y se encarga de gestionar cosas como los [Cambiar/Recargar la Escena], [Pausar el juego] o [Cerrar el juego]

Cuando cambiamos la escena, Godot toma todos los Nodos que son hijos del Nodo Raíz

#### Qué es un Autoload?
TBD

#### Qué es una señal?
TBD

##### Qué es un Recurso? Datos vs Runtime
TBD

---
#### Qué es Git y Github?
TBD


---


### Matematicas:

##### Suma, resta, multiplicacion y division
##### Delta Time
##### Modulo, Pow y Sqr
##### Operaciones entre vectores
##### Trigonometría

# Arreglos Estáticos y Dinámicos en Java

En Java, los arreglos son una estructura de datos que se utiliza para almacenar una colección de elementos del mismo
tipo. Los arreglos pueden ser estáticos o dinámicos, dependiendo de si su tamaño es fijo o variable.

## Arreglos Estáticos

Los arreglos estáticos tienen un tamaño fijo que se especifica al crear el arreglo. Una vez que se crea un arreglo
estático, su tamaño no puede cambiar. Para crear un arreglo estático en Java, se utiliza alguna de las siguientes
sintaxis:

```java
// Declaración e inicialización de un arreglo estático de enteros
int[] numeros = new int[5];
// Declaración e inicialización explícita de un arreglo estático de enteros
int[] numeros = {1, 2, 3, 4, 5};
```

En el primer ejemplo, se declara e inicializa un arreglo estático de enteros con un tamaño de 5 elementos. En el
segundo ejemplo, se declara e inicializa un arreglo estático de enteros con los valores `1`, `2`, `3`, `4` y `5`.

Para acceder a un elemento de un arreglo estático, se utiliza el índice del elemento entre corchetes. Por ejemplo:

```java
int[] numeros = {1, 2, 3, 4, 5};
System.out.println(numeros[0]); // 1
System.out.println(numeros[1]); // 2
System.out.println(numeros[2]); // 3
```

En este ejemplo, se accede a los elementos del arreglo `numeros` utilizando los índices `0`, `1` y `2`.

## Arreglos Dinámicos

Los arreglos dinámicos tienen un tamaño variable que puede cambiar durante la ejecución del programa. En Java, los
arreglos dinámicos se implementan utilizando la clase `ArrayList` del paquete `java.util`. Para crear un arreglo
dinámico en Java, se utiliza la siguiente sintaxis:

```java
// Declaración e inicialización de un arreglo dinámico de enteros
ArrayList<Integer> numeros = new ArrayList<Integer>();
// Agregar elementos al arreglo dinámico
numeros.add(1);
numeros.add(2);
numeros.add(3);
```

En este ejemplo, se declara e inicializa un arreglo dinámico de enteros utilizando la clase `ArrayList`. Se agregan
los elementos `1`, `2` y `3` al arreglo dinámico utilizando el método `add`.

Para acceder a un elemento de un arreglo dinámico, se utiliza el método `get` con el índice del elemento como
parámetro. Por ejemplo:

```java
ArrayList<Integer> numeros = new ArrayList<Integer>();
numeros.add(1);
numeros.add(2);
numeros.add(3);
System.out.println(numeros.get(0)); // 1
System.out.println(numeros.get(1)); // 2
System.out.println(numeros.get(2)); // 3
```

En este ejemplo, se accede a los elementos del arreglo dinámico `numeros` utilizando el método `get` con los índices
`0`, `1` y `2`.

Los arreglos dinámicos son útiles cuando se necesita un tamaño variable y se requiere agregar o eliminar elementos
durante la ejecución del programa.

### Funciones de la clase `ArrayList`

La clase `ArrayList` proporciona una serie de funciones útiles para trabajar con arreglos dinámicos en Java. Algunas
de las funciones más comunes son:

- `add`: Agrega un elemento al arreglo dinámico.
    - Ejemplo: `numeros.add(4);`
- `get`: Obtiene un elemento del arreglo dinámico.
    - Ejemplo: `int numero = numeros.get(0);`
- `set`: Reemplaza un elemento del arreglo dinámico.
    - Ejemplo: `numeros.set(0, 5);`
- `remove`: Elimina un elemento del arreglo dinámico.
    - Ejemplo: `numeros.remove(0);`
- `size`: Obtiene el tamaño del arreglo dinámico.
    - Ejemplo: `int tamano = numeros.size();`
- `isEmpty`: Verifica si el arreglo dinámico está vacío.
    - Ejemplo: `boolean vacio = numeros.isEmpty();`
- `indexOf`: Obtiene el índice de un elemento en el arreglo dinámico.
    - Ejemplo: `int indice = numeros.indexOf(3);`
- `clear`: Elimina todos los elementos del arreglo dinámico.
    - Ejemplo: `numeros.clear();`
- `contains`: Verifica si un elemento está presente en el arreglo dinámico.
    - Ejemplo: `boolean contiene = numeros.contains(3);`
- `isEmpty`: Verifica si el arreglo dinámico está vacío.
    - Ejemplo: `boolean vacio = numeros.isEmpty();`
- `toArray`: Convierte el arreglo dinámico en un arreglo estático.
    - Ejemplo: `Integer[] arreglo = numeros.toArray(new Integer[numeros.size()]);`
- `addAll`: Agrega todos los elementos de otro arreglo dinámico al arreglo dinámico actual.
    - Ejemplo: `numeros.addAll(otrosNumeros);`
- `removeAll`: Elimina todos los elementos de otro arreglo dinámico del arreglo dinámico actual.
    - Ejemplo: `numeros.removeAll(otrosNumeros);`
- `retainAll`: Elimina todos los elementos del arreglo dinámico actual que no están presentes en otro arreglo dinámico.
    - Ejemplo: `numeros.retainAll(otrosNumeros);`
- `subList`: Obtiene una sublista del arreglo dinámico.
    - Ejemplo: `ArrayList<Integer> sublista = numeros.subList(0, 2);`
- `sort`: Ordena los elementos del arreglo dinámico.
    - Ejemplo: `Collections.sort(numeros);`

Estas funciones permiten realizar operaciones comunes con arreglos dinámicos, como agregar, eliminar, obtener y
modificar elementos, así como verificar si un elemento está presente en el arreglo dinámico.

Los arreglos estáticos y dinámicos son estructuras de datos fundamentales en Java que se utilizan para almacenar
colecciones de elementos del mismo tipo. Los arreglos estáticos tienen un tamaño fijo que se especifica al crear el
arreglo, mientras que los arreglos dinámicos tienen un tamaño variable que puede cambiar durante la ejecución del
programa. Ambos tipos de arreglos tienen sus propias ventajas y se utilizan en diferentes situaciones dependiendo de
los requisitos del programa.

Los arreglos estáticos son útiles cuando se conoce de antemano el tamaño de la colección y no se espera que cambie
durante la ejecución del programa. Los arreglos dinámicos son útiles cuando se necesita un tamaño variable y se
requiere agregar o eliminar elementos durante la ejecución del programa. La clase `ArrayList` proporciona una serie
de funciones útiles para trabajar con arreglos dinámicos en Java, lo que facilita la manipulación y gestión de
colecciones de elementos.

En resumen, los arreglos estáticos y dinámicos son estructuras de datos esenciales en Java que se utilizan para
almacenar colecciones de elementos del mismo tipo. Cada tipo de arreglo tiene sus propias ventajas y se utiliza en
diferentes situaciones dependiendo de los requisitos del programa.

## Referencias

- [Java Arrays](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html)
- [Java ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
- [Java Collections Framework](https://docs.oracle.com/javase/tutorial/collections/index.html)
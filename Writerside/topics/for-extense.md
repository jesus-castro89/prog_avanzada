# La estructura `for`

La estructura `for` en Java se utiliza para repetir un bloque de código un número específico de veces. La sintaxis
básica de la estructura `for` es la siguiente:

```java
for (inicialización; condición; actualización) {
    // Bloque de código a repetir
}
```

Donde:

- `inicialización`: Es la expresión que se ejecuta una vez antes de que comience el bucle. Se utiliza para inicializar
  variables y establecer condiciones iniciales.
- `condición`: Es la expresión booleana que se evalúa en cada iteración del bucle. Si la condición es verdadera, se
  ejecuta el bloque de código. Si es falsa, se sale del bucle.
- `actualización`: Es la expresión que se ejecuta al final de cada iteración del bucle. Se utiliza para actualizar
  variables y modificar el estado del bucle.
- `bloque de código`: Es el conjunto de instrucciones que se ejecutan en cada iteración del bucle.
- `for`: Es la palabra clave que indica el inicio de la estructura `for`.
- `{}`: Son los corchetes que delimitan el bloque de código a repetir.

> **Nota:** La estructura `for` es una forma conveniente de repetir un bloque de código un número específico de veces y
> es útil cuando se conoce de antemano el número de iteraciones necesarias.

> **Nota:** La estructura `for` puede ser anidada dentro de otra estructura `for`, lo que permite realizar iteraciones
> más complejas. La indentación del código es fundamental para la legibilidad y la comprensión de las estructuras
> anidadas.

> **Nota:** La estructura `for` puede ser usada sin la inicialización, la condición o la actualización, pero es
> importante tener en cuenta que estas partes son opcionales y pueden ser omitidas si no son necesarias.

## Ejemplos de Estructura `for`

A continuación se muestra un ejemplo de cómo se utiliza la estructura `for` en Java:

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Iteración " + i);
}
```

En este ejemplo:

1. Se declara e inicializa una variable `i` con el valor `0
2. Se evalúa la condición `i < 5` en cada iteración del bucle.
3. Se incrementa la variable `i` en `1` al final de cada iteración.
4. Se imprime un mensaje en la consola en cada iteración del bucle.
5. El bucle se repite `5` veces, comenzando desde `0` y terminando en `4`.
6. La salida del programa sería:

```text
Iteración 0
Iteración 1
Iteración 2
Iteración 3
Iteración 4
```

La estructura `for` es una herramienta poderosa para repetir un bloque de código un número específico de veces y es
ampliamente utilizada en la programación Java para realizar tareas repetitivas de manera eficiente y concisa.

## Uso de `break` y `continue` en la Estructura `for`

Dentro de un bucle `for`, se pueden utilizar las palabras clave `break` y `continue` para controlar el flujo de
ejecución del bucle.

> **Nota:** La palabra clave **`break`** se utiliza para salir del bucle inmediatamente, mientras que la palabra clave
> **`continue`** se utiliza para saltar a la siguiente iteración del bucle.

> **Nota:** El uso de **`break`** y **`continue`** en un bucle `for` puede ayudar a controlar el flujo de ejecución y realizar
> operaciones específicas en función de ciertas condiciones durante la iteración del bucle.

> **Nota:** La palabra clave **`break`** puede ser utilizada en cualquier bucle, no solo en la estructura `for`.

A continuación se muestra un ejemplo de cómo se utilizan `break` y `continue` en un bucle `for`:

```java
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break; // Sale del bucle cuando i es igual a 5
    }
    if (i % 2 == 0) {
        continue; // Salta a la siguiente iteración si i es par
    }
    System.out.println("Iteración " + i);
}
```

En este ejemplo:

1. Se declara e inicializa una variable `i` con el valor `0
2. Se evalúa la condición `i < 10` en cada iteración del bucle.
3. Se incrementa la variable `i` en `1` al final de cada iteración.
4. Se verifica si `i` es igual a `5` y se sale del bucle si se cumple la condición.
5. Se verifica si `i` es par y se salta a la siguiente iteración si se cumple la condición.
6. Se imprime un mensaje en la consola en cada iteración del bucle, excepto cuando `i` es igual a `5` o es par.
7. La salida del programa sería:

```text
Iteración 1
Iteración 3
Iteración 7
Iteración 9
```

El uso de `break` y `continue` en la estructura `for` permite controlar el flujo de ejecución y realizar operaciones
específicas en función de ciertas condiciones durante la iteración del bucle.

## Conclusión

La estructura `for` es una herramienta poderosa en Java para repetir un bloque de código un número específico de veces.
Permite inicializar variables, evaluar condiciones y actualizar el estado del bucle en cada iteración. La estructura
`for` es ampliamente utilizada en la programación Java para realizar tareas repetitivas de manera eficiente y
concisa. Además, el uso de `break` y `continue` en la estructura `for` permite controlar el flujo de ejecución y
realizar operaciones específicas en función de ciertas condiciones durante la iteración del bucle.
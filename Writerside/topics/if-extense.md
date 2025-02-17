# La Estructura `if`

La estructura `if` es una de las estructuras de control de selección más básicas en Java. Se utiliza para ejecutar un
bloque de código si una condición es verdadera. La sintaxis básica de la estructura `if` es la siguiente:

```java
if (condición) {
    // Bloque de código a ejecutar si la condición es verdadera
}
```

Donde:

- `condición`: Es una expresión booleana que se evalúa como verdadera o falsa.
- `bloque de código`: Es el conjunto de instrucciones que se ejecutan si la condición es verdadera.
- `if`: Es la palabra clave que indica el inicio de la estructura `if`.
- `{}`: Son los corchetes que delimitan el bloque de código a ejecutar.

> **Nota:** Si la condición es verdadera, se ejecuta el bloque de código dentro de las llaves `{}`. Si la condición es
> falsa, el bloque de código no se ejecuta.

> **Nota:** La condición de un `if` debe ser una expresión booleana, es decir, una expresión que se evalúa como `true`
> o `false`. Si la condición no es de tipo booleano, se producirá un error de compilación. Por ejemplo,
> `if (x > 0)` es una expresión booleana que se evalúa como verdadera si `x` es mayor que `0`.

Toma en cuenta que la estructura `if` puede ser anidada dentro de otra estructura `if`, lo que permite evaluar
condiciones más complejas. Por ejemplo:

```java
int x = 10;
int y = 5;
if (x > 0) {
    if (y > 0) {
        System.out.println("x y y son positivos");
    }
}
```

En este ejemplo, se evalúa si `x` es mayor que `0` y, si es verdadero, se evalúa si `y` es mayor que `0`. Si ambas
condiciones son verdaderas, se imprime el mensaje `"x y y son positivos"` en la consola.

> **Nota:** Es importante tener en cuenta que la indentación del código es fundamental para la legibilidad y la
> comprensión de las estructuras anidadas. Se recomienda utilizar una sangría consistente para facilitar la lectura del
> código.

> **Nota:** La estructura `if` puede hacer uso de los operadores lógicos `&&` (AND), `||` (OR) y `!` (NOT) para
> combinar múltiples condiciones y realizar evaluaciones más complejas. Por ejemplo, `if (x > 0 && y > 0)` evalúa si
> `x` y `y` son mayores que `0`.

## Ejemplos de Estructura `if`

A continuación, se muestra un ejemplo de cómo se utiliza la estructura `if` en Java:

```java
int x = 10;
if (x > 0) {
    System.out.println("x es positivo");
}
```

En este ejemplo, se declara una variable `x` con el valor `10` y se evalúa si `x` es mayor que `0`. Si la condición es
verdadera, se imprime el mensaje `"x es positivo"` en la consola.

La estructura `if` también puede incluir un bloque de código alternativo que se ejecuta si la condición es falsa. Para
esto, se puede utilizar la estructura `if-else`. A continuación, se muestra un ejemplo de cómo se utiliza la estructura
`if-else` en Java:

```java
int x = -5;
if (x > 0) {
    System.out.println("x es positivo");
} else {
    System.out.println("x es negativo o cero");
}
```

En este ejemplo, se declara una variable `x` con el valor `-5` y se evalúa si `x` es mayor que `0`. Si la condición es
verdadera, se imprime el mensaje `"x es positivo"`, de lo contrario, se imprime el mensaje `"x es negativo o cero"`.

La estructura `if-else` es útil para ejecutar diferentes bloques de código dependiendo de si una condición es verdadera
o falsa. Esto permite tomar decisiones en función de los valores de las variables y controlar el flujo de ejecución de
un programa.

También existe la estructura `if-else-if`, que se utiliza para evaluar múltiples condiciones en secuencia. A
continuación, se muestra un ejemplo de cómo se utiliza la estructura `if-else-if` en Java:

```java
int x = 0;
if (x > 0) {
    System.out.println("x es positivo");
} else if (x < 0) {
    System.out.println("x es negativo");
} else {
    System.out.println("x es cero");
}
```

En este ejemplo, se declara una variable `x` con el valor `0` y se evalúa si `x` es mayor que `0`, menor que `0` o
igual a `0`. Dependiendo del resultado de la evaluación, se imprime un mensaje en la consola.

La estructura `if-else-if` es útil para realizar múltiples comprobaciones en secuencia y ejecutar diferentes bloques de
código en función de las condiciones evaluadas.

## Conclusión

La estructura `if` es una herramienta fundamental en Java para controlar el flujo de ejecución de un programa. Permite
evaluar condiciones y ejecutar bloques de código en función de si esas condiciones son verdaderas o falsas. Al combinar
la estructura `if` con `else` y `else-if`, es posible realizar evaluaciones más complejas y tomar decisiones basadas en
múltiples condiciones. El uso adecuado de la estructura `if` es esencial para crear programas que respondan de manera
dinámica a diferentes situaciones y eventos.
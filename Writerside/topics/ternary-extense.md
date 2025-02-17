# El operador `?:`

El operador ternario (`?:`) es una forma abreviada de la estructura `if-else` que se utiliza para asignar un valor a una
variable basado en una condición. Su sintaxis es la siguiente:

```java
variable = (condición) ? valorSiVerdadero : valorSiFalso;
```

Donde:

- `condición` es una expresión booleana que se evalúa como verdadera o falsa.
- `valorSiVerdadero` es el valor que se asigna a la variable si la condición es verdadera.
- `valorSiFalso` es el valor que se asigna a la variable si la condición es falsa.
- `variable` es la variable a la que se asigna el valor en función de la condición.

> **Nota:** El operador ternario es una forma concisa de asignar un valor a una variable basado en una condición. Es
> útil cuando se desea asignar un valor simple en función de una condición. Sin embargo, su uso excesivo puede
> dificultar la legibilidad del código.

## Ejemplo de Operador Ternario

A continuación, se muestra un ejemplo de cómo se utiliza el operador ternario en Java:

```java
int x = 10;
String mensaje = (x > 0) ? "x es positivo" : "x es negativo o cero";
System.out.println(mensaje);
```

En este ejemplo, se declara una variable `x` con el valor `10` y se utiliza el operador ternario para asignar un mensaje
a la variable `mensaje` en función de si `x` es mayor que `0`. Si la condición es verdadera, se asigna el mensaje `"x es
positivo"`, de lo contrario, se asigna el mensaje `"x es negativo o cero"`. Finalmente, se imprime el mensaje en la
consola.

## Anidamiento de Operadores Ternarios

El operador ternario también se puede anidar para evaluar múltiples condiciones. Por ejemplo:

```java
int x = 10;
String mensaje = (x > 0) ? "x es positivo" : (x < 0) ? "x es negativo" : "x es cero";
System.out.println(mensaje);
```

En este ejemplo, se evalúa si `x` es mayor que `0`, menor que `0` o igual a `0`, y se asigna un mensaje en función de la
condición evaluada. El operador ternario anidado permite realizar múltiples comprobaciones en una sola expresión.

## Conclusión

El operador ternario (`?:`) es una forma abreviada y concisa de asignar valores a variables basados en condiciones
simples. Se utiliza para simplificar la asignación de valores en función de una condición y puede anidarse para evaluar
múltiples condiciones en una sola expresión. Es una herramienta útil para mejorar la legibilidad y concisión del código
cuando se desea asignar valores simples en función de condiciones booleanas.
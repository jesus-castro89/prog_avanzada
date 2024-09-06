# Las tablas de verdad en los if de Java

En java, los operadores lógicos pueden usarse en la instrucción `if` para evaluar expresiones booleanas y tomar
decisiones basadas en el resultado de la evaluación.

## Operadores lógicos en los if

Los operadores lógicos más comunes en Java son:

- `&&` (y): Devuelve `true` si ambas expresiones son `true`.
- `||` (o): Devuelve `true` si al menos una de las expresiones es `true`.
- `!` (no): Devuelve `true` si la expresión es `false`.
- `^` (xor): Devuelve `true` si una de las expresiones es `true` y la otra es `false`.
- `&` (y lógico): Devuelve `true` si ambas expresiones son `true`.
- `|` (o lógico): Devuelve `true` si al menos una de las expresiones es `true`.
- `~` (complemento): Devuelve el complemento de la expresión.

Estos operadores se pueden utilizar en las instrucciones `if` para evaluar expresiones booleanas y tomar decisiones
basadas en el resultado de la evaluación.

Por ejemplo:

```java

int x = 5;
int y = 10;

if (x > 0 && y < 20) {
    System.out.println("x es mayor que 0 y y es menor que 20");
} else {
    System.out.println("x no es mayor que 0 o y no es menor que 20");
}

if (x < 0 || y > 20) {
    System.out.println("x es menor que 0 o y es mayor que 20");
} else {
    System.out.println("x no es menor que 0 y y no es mayor que 20");
}

if (!(x == y)) {
    System.out.println("x no es igual a y");
} else {
    System.out.println("x es igual a y");
}

if (x != y) {
    System.out.println("x no es igual a y");
} else {
    System.out.println("x es igual a y");
}

if (x > 0 ^ y < 20) {
    System.out.println("x es mayor que 0 o y es menor que 20, pero no ambos");
} else {
    System.out.println("x no es mayor que 0 o y no es menor que 20, o ambos");
}

if (x > 0 & y < 20) {
    System.out.println("x es mayor que 0 y y es menor que 20");
} else {
    System.out.println("x no es mayor que 0 o y no es menor que 20");
}

if (x < 0 | y > 20) {
    System.out.println("x es menor que 0 o y es mayor que 20");
} else {
    System.out.println("x no es menor que 0 y y no es mayor que 20");
}

if (~x == -6) {
    System.out.println("El complemento de x es -6");
} else {
    System.out.println("El complemento de x no es -6");
}

```

En este ejemplo, se utilizan los operadores lógicos `&&`, `||`, `!`, `^`, `&`, `|` y `~` para evaluar expresiones
booleanas y tomar decisiones basadas en el resultado de la evaluación.
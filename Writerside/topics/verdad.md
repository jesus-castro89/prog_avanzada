# Las tablas de verdad

Las tablas de verdad son una herramienta fundamental en la lógica matemática. Nos permiten analizar el comportamiento de
las proposiciones lógicas y de los conectores lógicos.

## Proposiciones

Una proposición es una afirmación que puede ser verdadera o falsa, pero no ambas cosas a la vez. Por ejemplo, las
siguientes son proposiciones:

- El cielo es azul.
- 2 + 2 = 4.
- 3 es un número par.

En cambio, las siguientes no son proposiciones:

- ¿Cómo estás?
- x + 1 = 5.
- La suma de dos números pares es un número par.

## Conectores lógicos

Los conectores lógicos son operadores que nos permiten combinar proposiciones para formar proposiciones más complejas.
Los conectores lógicos más comunes son:

- La conjunción (y): Se representa con el símbolo ∧. La proposición p ∧ q es verdadera si tanto p como q son verdaderas,
  y falsa en caso contrario. En Java, el operador `&&` es el operador de conjunción.
- La disyunción (o): Se representa con el símbolo ∨. La proposición p ∨ q es verdadera si al menos una de las
  proposiciones p y q es verdadera, y falsa en caso contrario. En Java, el operador `||` es el operador de disyunción.
- La negación (no): Se representa con el símbolo ¬. La proposición ¬p es verdadera si p es falsa, y falsa si p es
  verdadera. En Java, el operador `!` es el operador de negación.

## Tablas de verdad

Una tabla de verdad es una representación de todas las posibles combinaciones de valores de verdad de un conjunto de
proposiciones. Por ejemplo, la tabla de verdad de la conjunción es la siguiente:

|   p   |   q   | p ∧ q | p v q |  !p   |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| true  | true  | true  | true  | false |
| true  | false | false | true  | false |
| false | true  | false | true  | true  |
| false | false | false | false | true  |

En esta tabla, p y q son proposiciones, y p ∧ q es la proposición que resulta de aplicar el operador de conjunción a p y
q.

Las tablas de verdad son una herramienta muy útil para analizar el comportamiento de las proposiciones y de los
conectores lógicos. Nos permiten determinar cuándo una proposición es verdadera o falsa en función de los valores de
verdad de las proposiciones que la componen.

Las tablas de verdad son una herramienta fundamental en la lógica matemática. Nos permiten analizar el comportamiento de
las proposiciones lógicas y de los conectores lógicos.

## En Java

En Java, los operadores lógicos se utilizan para combinar expresiones booleanas y obtener un resultado booleano. Los
operadores lógicos más comunes son:

- `&&` (y): Devuelve `true` si ambas expresiones son `true`.
- `||` (o): Devuelve `true` si al menos una de las expresiones es `true`.
- `!` (no): Devuelve `true` si la expresión es `false`.
- `^` (xor): Devuelve `true` si una de las expresiones es `true` y la otra es `false`.

Por ejemplo:

```java
boolean a = true;
boolean b = false;

System.out.println(a && b); // false
System.out.println(a || b); // true
System.out.println(!a); // false
System.out.println(a ^ b); // true
```

Aunque los operadores no solo aplican a elementos booleanos, sino también a expresiones que devuelvan un valor booleano.

Veamos un ejemplo:

```java
int x = 5;
int y = 10;

System.out.println(x > 0 && y < 20); // true
System.out.println(x < 0 || y > 20); // false
System.out.println(!(x == y)); // true
System.out.println(x != y); // true
System.out.println(x > 0 ^ y < 20); // false
```
# La conversión de datos

La conversión de datos o `casting` es un proceso que consiste en cambiar el tipo de un dato a otro tipo compatible. En
Java, existen dos tipos de conversiones de datos: la conversión implícita y la conversión explícita.

## Conversión Implícita

La conversión implícita es aquella en la que el compilador de Java realiza la conversión de forma automática sin que el
programador tenga que hacer nada. Este tipo de conversión se da cuando se asigna un valor de un tipo de dato más pequeño
a un tipo de dato más grande. Por ejemplo:

```java
int numero = 10;

// Conversión implícita de int a double
double numeroDoble = numero;
```

En este ejemplo, se asigna un valor entero `10` a la variable `numero` de tipo `int`, y luego se asigna la
variable `numero` a la variable `numeroDoble` de tipo `double`. La conversión de `int` a `double` se realiza de forma
implícita, ya que `double` es un tipo de dato más grande que `int`.

## Conversión Explícita

La conversión explícita es aquella en la que el programador realiza la conversión de forma manual utilizando un operador
de conversión. Este tipo de conversión se da cuando se asigna un valor de un tipo de dato más grande a un tipo de dato
más pequeño. Por ejemplo:

```java
double numeroDoble = 10.5;

// Conversión explícita de double a int
int numero = (int) numeroDoble;
```

En este ejemplo, se asigna un valor decimal `10.5` a la variable `numeroDoble` de tipo `double`, y luego se asigna la
variable `numeroDoble` a la variable `numero` de tipo `int`. La conversión de `double` a `int` se realiza de forma
explícita utilizando el operador de conversión `(int)`.

## Usando los Wrappers

Además de estos dos tipos de conversiones, también es posible realizar conversiones entre texto y tipos primitivos
utilizando los *wrappers* correspondientes. Por ejemplo:

```java
String texto = "10";

// Conversión de String a int
int numero = Integer.parseInt(texto);
```

En este ejemplo, se convierte el texto `"10"` a un entero utilizando el método `parseInt` de la clase `Integer`. Este
método convierte el texto en un entero y lo asigna a la variable `numero`.

## Conclusiones

La conversión de datos es un proceso importante en Java que permite cambiar el tipo de un dato a otro tipo compatible.
Existen dos tipos de conversiones: la conversión implícita, en la que el compilador realiza la conversión
automáticamente, y la conversión explícita, en la que el programador realiza la conversión de forma manual. Además, es
posible realizar conversiones entre texto y tipos primitivos utilizando los *wrappers* correspondientes.

La conversión de datos es una herramienta útil que permite trabajar con diferentes tipos de datos en Java de forma
flexible y eficiente.
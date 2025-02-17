# La estructura `switch`

La estructura `switch` se utiliza para seleccionar uno de varios bloques de código para ejecutar, basado en el valor de
una expresión. La expresión puede ser de tipo `int`, `char`, `String` o enumerado. La estructura `switch` es una
alternativa a la estructura `if-else-if` cuando se necesita seleccionar entre múltiples opciones.

La estructura `switch` consta de una expresión que se evalúa y varios casos (`case`) que representan los posibles
valores de la expresión. Cada caso puede contener un bloque de código que se ejecuta si el valor de la expresión
coincide con el valor del caso. Además, se puede incluir un caso `default` que se ejecuta si ninguno de los casos
anteriores coincide con el valor de la expresión.

A continuación, se muestra un ejemplo de cómo se utiliza la estructura `switch` en Java:

```java
int diaSemana = 1;
String nombreDia;
switch (diaSemana) {
    case 1:
        nombreDia = "Lunes";
        break;
    case 2:
        nombreDia = "Martes";
        break;
    case 3:
        nombreDia = "Miércoles";
        break;
    case 4:
        nombreDia = "Jueves";
        break;
    case 5:
        nombreDia = "Viernes";
        break;
    case 6:
        nombreDia = "Sábado";
        break;
    case 7:
        nombreDia = "Domingo";
        break;
    default:
        nombreDia = "Día inválido";
}
System.out.println("Hoy es " + nombreDia);
```

En este ejemplo, se declara una variable `diaSemana` con el valor `1` y se utiliza la estructura `switch` para asignar
un nombre al día de la semana correspondiente al valor de `diaSemana`. Dependiendo del valor de `diaSemana`, se
asigna un nombre de día a la variable `nombreDia` y se imprime en la consola.

La estructura `switch` es útil cuando se necesita seleccionar entre múltiples opciones basadas en el valor de una
expresión. Es una forma más concisa y legible de manejar múltiples casos que la estructura `if-else-if`.

## Forma mejorada de la estructura `switch`

A partir de Java 12, se introdujo una forma mejorada de la estructura `switch` que permite simplificar la sintaxis y
hacerla más concisa. En esta forma mejorada, se utilizan expresiones lambda para definir los bloques de código de cada
caso y el caso `default`.

A continuación, se muestra el mismo ejemplo anterior utilizando la forma mejorada de la estructura `switch`:

```java
int diaSemana = 1;
String nombreDia = switch (diaSemana) {
    case 1 -> "Lunes";
    case 2 -> "Martes";
    case 3 -> "Miércoles";
    case 4 -> "Jueves";
    case 5 -> "Viernes";
    case 6 -> "Sábado";
    case 7 -> "Domingo";
    default -> "Día inválido";
};
System.out.println("Hoy es " + nombreDia);
```

En este ejemplo, se utiliza la forma mejorada de la estructura `switch` para asignar un nombre al día de la semana
correspondiente al valor de `diaSemana`. La expresión lambda `->` se utiliza para definir los bloques de código de cada
caso y el caso `default`. La variable `nombreDia` se inicializa con el valor del caso correspondiente y se imprime en
la consola.

La forma mejorada de la estructura `switch` es más concisa y legible que la forma tradicional, especialmente cuando se
trabaja con múltiples casos y bloques de código cortos.

## Conclusión

La estructura `switch` es una herramienta útil en Java para seleccionar entre múltiples opciones basadas en el valor de
una expresión. Permite escribir un código más limpio y legible al manejar múltiples casos de forma estructurada. La
forma mejorada de la estructura `switch` introducida en Java 12 simplifica aún más la sintaxis y hace que el código sea
más conciso. La elección entre la forma tradicional y la forma mejorada dependerá de las preferencias del programador y
de la legibilidad del código en cada caso.
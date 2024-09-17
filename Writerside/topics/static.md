# La palabra reservada `static`

La palabra reservada `static` se utiliza en Java para definir miembros de clase que pertenecen a la clase en sí misma,
en lugar de a una instancia de la clase. Los miembros estáticos se pueden acceder directamente a través del nombre de la
clase, sin necesidad de crear una instancia de la clase.

## Variables Estáticas

Las variables estáticas son variables de clase que pertenecen a la clase en sí misma, en lugar de a una instancia de la
clase. Las variables estáticas se definen con la palabra clave `static` y se inicializan una sola vez en la memoria
cuando se carga la clase.

Por ejemplo:

```java
public class StaticExample {
    public static int count = 0;

    public StaticExample() {
        count++;
    }

    public static void main(String[] args) {
        StaticExample obj1 = new StaticExample();
        StaticExample obj2 = new StaticExample();

        System.out.println(StaticExample.count); // 2
    }
}
```

En este ejemplo, la variable `count` es una variable estática que se incrementa cada vez que se crea una nueva instancia
de la clase `StaticExample`. La variable `count` se puede acceder directamente a través del nombre de la clase, sin
necesidad de crear una instancia de la clase.

## Métodos Estáticos

Los métodos estáticos son métodos de clase que pertenecen a la clase en sí misma, en lugar de a una instancia de la
clase.

Por ejemplo:

```java
public class StaticExample {
    public static void printMessage() {
        System.out.println("Hello, World!");
    }

    public static void main(String[] args) {
        StaticExample.printMessage(); // Hello, World!
    }
}
```

En este ejemplo, el método `printMessage` es un método estático que se puede llamar directamente a través del nombre de
la clase, sin necesidad de crear una instancia de la clase.

Los métodos estáticos se utilizan a menudo para definir métodos de utilidad que no dependen del estado de una instancia
de la clase.

## Clases Estáticas

Las clases estáticas son clases anidadas que se definen dentro de otra clase y se marcan con la palabra clave `static`.

Por ejemplo:

```java
public class OuterClass {
    public static class StaticNestedClass {
        public void printMessage() {
            System.out.println("Hello, World!");
        }
    }

    public static void main(String[] args) {
        OuterClass.StaticNestedClass nested = new OuterClass.StaticNestedClass();
        nested.printMessage(); // Hello, World!
    }
}
```

En este ejemplo, la clase `StaticNestedClass` es una clase estática anidada dentro de la clase `OuterClass`. La clase
`StaticNestedClass` se puede acceder directamente a través del nombre de la clase externa, sin necesidad de crear una
instancia de la clase externa.

Las clases estáticas se utilizan a menudo para agrupar clases relacionadas que no necesitan acceder a los miembros no
estáticos de la clase externa.

## Bloques Estáticos

Los bloques estáticos son bloques de código que se ejecutan una sola vez cuando se carga la clase en la memoria. Los
bloques estáticos se utilizan para inicializar variables estáticas y realizar tareas de inicialización que deben
realizarse una sola vez.

Por ejemplo:

```java
public class StaticExample {
    public static int count;

    static {
        count = 0;
        System.out.println("Static block executed");
    }

    public static void main(String[] args) {
        System.out.println(StaticExample.count); // 0
    }
}
```

En este ejemplo, el bloque estático se ejecuta una sola vez cuando se carga la clase `StaticExample` en la memoria. El
bloque estático inicializa la variable `count` y muestra un mensaje en la consola.

Los bloques estáticos se utilizan a menudo para realizar tareas de inicialización que deben realizarse una sola vez,
como la inicialización de variables estáticas o la carga de recursos externos.

## Consideraciones

- Los miembros estáticos se comparten entre todas las instancias de la clase y se pueden acceder directamente a través
  del nombre de la clase.
- Los miembros estáticos no pueden acceder a los miembros no estáticos de la clase.
- Los miembros estáticos se inicializan una sola vez cuando se carga la clase en la memoria.
- Los métodos estáticos se utilizan a menudo para definir métodos de utilidad que no dependen del estado de una
  instancia de la clase.

## Resumen

En Java, la palabra reservada `static` se utiliza para definir miembros de clase que pertenecen a la clase en sí misma,
en lugar de a una instancia de la clase. Los miembros estáticos se pueden acceder directamente a través del nombre de la
clase, sin necesidad de crear una instancia de la clase. Los miembros estáticos se utilizan a menudo para definir
variables y métodos de clase que se comparten entre todas las instancias de la clase.

## Referencias

- [Java Static Keyword - GeeksforGeeks](https://www.geeksforgeeks.org/static-keyword-java/)
- [Static Nested Classes - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html)
- [Static Initialization Blocks - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/initial.html)
- [Static Methods - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html)
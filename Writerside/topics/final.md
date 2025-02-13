# La palabra reservada final

La palabra reservada `final` se utiliza en Java para definir constantes, métodos y clases que no pueden ser modificados
o extendidos. La palabra reservada `final` se puede aplicar a variables, métodos y clases en Java.

## Variables Finales

Las variables finales son variables que no pueden ser modificadas una vez que han sido inicializadas. Las variables
finales se definen con la palabra clave `final` y se inicializan una sola vez. Una vez que se ha asignado un valor a
una variable final, no se puede cambiar.

Por ejemplo:

```java
public class FinalExample {
    public final int value = 10;

    public static void main(String[] args) {
        FinalExample obj = new FinalExample();
        System.out.println(obj.value); // 10
    }
}
```

En este ejemplo, la variable `value` es una variable final que se inicializa con el valor `10`. Una vez que se ha
asignado un valor a la variable `value`, no se puede cambiar.

## Métodos Finales

Los métodos finales son métodos que no pueden ser sobrescritos por las subclases. Los métodos finales se definen con la
palabra clave `final` y no pueden ser modificados en las subclases.

Por ejemplo:

```java
public class FinalExample {
    public final void printMessage() {
        System.out.println("Hello, World!");
    }

    public static void main(String[] args) {
        FinalExample obj = new FinalExample();
        obj.printMessage(); // Hello, World!
    }
}
```

En este ejemplo, el método `printMessage` es un método final que imprime el mensaje "Hello, World!". El método
`printMessage` no puede ser sobrescrito por las subclases.

## Clases Finales

Las clases finales son clases que no pueden ser extendidas por otras clases. Las clases finales se definen con la
palabra clave `final` y no pueden ser subclases.

Por ejemplo:

```java
public final class FinalExample {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

En este ejemplo, la clase `FinalExample` es una clase final que imprime el mensaje "Hello, World!". La clase
`FinalExample` no puede ser extendida por otras clases.

La palabra reservada `final` se utiliza para definir constantes, métodos y clases que no pueden ser modificados o
extendidos en Java. Las variables finales, los métodos finales y las clases finales son útiles para garantizar la
inmutabilidad y la integridad del código en Java.

## Conclusión

En resumen, la palabra reservada `final` se utiliza en Java para definir constantes, métodos y clases que no pueden ser
modificados o extendidos. Las variables finales, los métodos finales y las clases finales son útiles para garantizar la
inmutabilidad y la integridad del código en Java.
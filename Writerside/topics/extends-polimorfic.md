# Polimorfismo en la Herencia

El polimorfismo es un concepto fundamental en la programación orientada a objetos que permite a los objetos responder de
manera diferente a los mismos mensajes. En Java, el polimorfismo se puede lograr a través de la herencia y la
sobrescritura de métodos. En este tutorial, exploraremos cómo se puede lograr el polimorfismo en la herencia en Java.

## Tipos de polimorfismo

En Java, existen dos tipos de polimorfismo:

- **Polimorfismo de sobrecarga**: Se refiere a la capacidad de una clase para tener múltiples métodos con el mismo
  nombre pero diferentes tipos de parámetros. Esto permite a los desarrolladores utilizar el mismo nombre de método para
  realizar
  tareas similares con diferentes tipos de datos.
- **Polimorfismo de anulación**: Se refiere a la capacidad de una subclase para proporcionar una implementación
  específica de un método que ya está definido en su superclase. Esto permite a las subclases proporcionar una
  funcionalidad específica que es adecuada para ellas.

## Polimorfismo en la herencia

El polimorfismo en la herencia se refiere a la capacidad de una subclase para proporcionar una implementación específica
de un método que ya está definido en su superclase. Esto permite a las subclases modificar o extender el comportamiento
de los métodos heredados de la superclase. El polimorfismo en la herencia es una forma poderosa de reutilizar y extender
el código en Java.

## Ejemplo de polimorfismo en la herencia

Supongamos que tenemos una clase base `Animal` que define un método `makeSound` que imprime un sonido genérico de
animal.

```java
public class Animal {

    public void makeSound() {
    
        System.out.println("Sonido genérico de animal...");
    }
}
```

Ahora, definimos una subclase `Dog` que hereda de la clase `Animal` y sobrescribe el método `makeSound` para
proporcionar una implementación específica del sonido de un perro.

```java
public class Dog extends Animal {

    @Override
    public void makeSound() {
    
        System.out.println("Guau guau!");
    }
}
```

En este ejemplo, la clase `Dog` sobrescribe el método `makeSound` de la clase `Animal` para proporcionar una
implementación específica del sonido de un perro.

## Llamada a métodos sobrescritos

Para llamar a un método sobrescrito en Java, se puede crear una instancia de la subclase y llamar al método a través de
esa instancia. En el siguiente ejemplo, se crea una instancia de la clase `Dog` y se llama al método `makeSound`.

```java
Animal animal = new Dog();
// Llamada al método sobrescrito
// Se infiere que se llama al método makeSound de Dog
animal.makeSound();
```

En este ejemplo, se crea una instancia de la clase `Dog` y se asigna a una referencia de tipo `Animal`. Cuando se
llama al método `makeSound` a través de la referencia de tipo `Animal`, se llama al método sobrescrito de la clase
`Dog`, lo que demuestra el polimorfismo en la herencia en Java.

El polimorfismo en la herencia es una característica poderosa de la programación orientada a objetos que permite a las
subclases proporcionar implementaciones específicas de los métodos heredados de las superclases. Esto facilita la
reutilización y extensión del código en Java, lo que resulta en un diseño de código más flexible y mantenible.

## Polimorfismo en la herencia vs. polimorfismo de sobrecarga

Es importante tener en cuenta que el polimorfismo en la herencia y el polimorfismo de sobrecarga son conceptos
diferentes en Java. Mientras que el polimorfismo en la herencia se refiere a la capacidad de una subclase para
proporcionar una implementación específica de un método heredado, el polimorfismo de sobrecarga se refiere a la
capacidad de una clase para tener múltiples métodos con el mismo nombre pero diferentes tipos de parámetros.

Ambos tipos de polimorfismo son útiles en la programación orientada a objetos y pueden utilizarse en conjunto para
crear un diseño de código más flexible y extensible en Java.

## Conclusión

En resumen, el polimorfismo en la herencia es un concepto fundamental en la programación orientada a objetos que
permite a las subclases proporcionar implementaciones específicas de los métodos heredados de las superclases. El
polimorfismo en la herencia es una característica poderosa de Java que facilita la reutilización y extensión del código,
lo que resulta en un diseño de código más flexible y mantenible. Al comprender y aplicar el polimorfismo en la herencia,
los desarrolladores pueden crear aplicaciones más robustas y escalables en Java.
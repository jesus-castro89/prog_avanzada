# Interfaces

Una interfaz es un contrato que define un conjunto de métodos que una clase debe implementar. En Java, una interfaz es
un tipo de referencia, similar a una clase, que puede contener solo constantes, métodos abstractos, métodos
predeterminados y métodos estáticos. No se pueden instanciar interfaces, pero se pueden implementar. Una clase puede
implementar cualquier número de interfaces.

## Definición

Una interfaz en Java se define con la palabra clave `interface`. A continuación, se muestra un ejemplo de una interfaz
simple:

```java
public interface Animal {

    void eat();

    void sleep();

}
```

En este ejemplo, la interfaz `Animal` define dos métodos: `eat` y `sleep`. Las interfaces no pueden contener
implementaciones de métodos, solo la firma de los métodos.

## Constantes

Las interfaces pueden contener constantes. Las constantes en una interfaz son implícitamente `public`, `static` y
`final`. A continuación, se muestra un ejemplo de una interfaz con una constante:

```java
public interface Animal {

    int MAX_AGE = 100;

}
```

En este ejemplo, `MAX_AGE` es una constante que se puede acceder a través de la interfaz `Animal`.

## Implementación

Una clase implementa una interfaz utilizando la palabra clave `implements`. A continuación, se muestra un ejemplo de una
clase que implementa la interfaz `Animal`:

```java
public class Dog implements Animal {

    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }

    @Override
    public void sleep() {
        System.out.println("Dog is sleeping");
    }

}
```

En este ejemplo, la clase `Dog` implementa la interfaz `Animal` y proporciona implementaciones para los métodos `eat`
y `sleep`.

## Herencia de interfaces

Una interfaz puede extender una o más interfaces. A continuación, se muestra un ejemplo de una interfaz que extiende
otra interfaz:

```java
public interface Pet extends Animal {

    void play();

}
```

En este ejemplo, la interfaz `Pet` extiende la interfaz `Animal` y agrega un nuevo método `play`.

## Interfaces funcionales

Una interfaz funcional es una interfaz que contiene un solo método abstracto. A partir de Java 8, las interfaces
funcionales se pueden anotar con la anotación `@FunctionalInterface`. A continuación, se muestra un ejemplo de una
interfaz funcional:

```java
@FunctionalInterface
public interface Calculator {

    int calculate(int a, int b);

}
```

En este ejemplo, la interfaz `Calculator` es una interfaz funcional con un solo método `calculate`.

## Métodos predeterminados

A partir de Java 8, las interfaces pueden contener métodos predeterminados. Un método predeterminado es un método que
tiene una implementación predeterminada en la interfaz. A continuación, se muestra un ejemplo de una interfaz con un
método predeterminado:

```java
public interface Animal {

    void eat();

    void sleep();

    default void breathe() {
        System.out.println("Animal is breathing");
    }

}
```

En este ejemplo, la interfaz `Animal` contiene un método predeterminado `breathe` que tiene una implementación
predeterminada.

## Métodos estáticos

A partir de Java 8, las interfaces pueden contener métodos estáticos. Un método estático es un método que se puede
invocar sin crear una instancia de la interfaz. A continuación, se muestra un ejemplo de una interfaz con un método
estático:

```java
public interface Animal {

    void eat();

    void sleep();

    static void makeSound() {
        System.out.println("Animal is making a sound");
    }

}
```

En este ejemplo, la interfaz `Animal` contiene un método estático `makeSound` que se puede invocar sin crear una
instancia de la interfaz.

## Ejemplo

A continuación, se muestra un ejemplo completo que demuestra el uso de interfaces en Java:

```java
public interface Animal {

    void eat();

    void sleep();

    default void breathe() {
        System.out.println("Animal is breathing");
    }

    static void makeSound() {
        System.out.println("Animal is making a sound");
    }

}

public class Dog implements Animal {

    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }

    @Override
    public void sleep() {
        System.out.println("Dog is sleeping");
    }

}

public class Main {

    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();
        dog.sleep();
        dog.breathe();
        Animal.makeSound();
    }

}
```

## Para nuestro proyecto

En el proyecto de RPG, podríamos definir una interfaz `Randomized` que contenga un método algunos métodos para
generar números aleatorios.

### La interfaz `Randomized`

```java
package rpg.utils;

public interface Randomize {

    int MIN = 1;

   static int getRandomInt(int min, int max) {
        return (int) (Math.random() * (max - min + 1) + min);
    }

    static boolean getRandomBoolean() {
        return Math.random() < 0.5;
    }
}
```

## Resumen

- Una interfaz en Java es un contrato que define un conjunto de métodos que una clase debe implementar.
- Las interfaces pueden contener métodos abstractos, métodos predeterminados, métodos estáticos y constantes.
- Una clase implementa una interfaz utilizando la palabra clave `implements`.
- Una interfaz puede extender una o más interfaces.
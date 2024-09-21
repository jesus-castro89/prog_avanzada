# La Herencia en Java

La herencia es un concepto fundamental en la programación orientada a objetos. Es una técnica que permite definir una
nueva clase basada en una clase existente. La nueva clase hereda atributos y métodos de la clase existente, y puede
agregar nuevos atributos y métodos, o modificar los existentes.

## Clases base y clases derivadas

En la herencia, la clase existente se conoce como clase base o superclase, y la nueva clase se conoce como clase
derivada o subclase. La clase derivada hereda todos los atributos y métodos de la clase base, y puede agregar nuevos
atributos y métodos, o modificar los existentes.

## Ejemplo de herencia en Java

```java
public class Animal {
    void eat() {
        System.out.println("Comiendo...");
    }
}

public class Dog extends Animal {
    void bark() {
        System.out.println("Ladrando...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();
        dog.bark();
    }
}
```

En este ejemplo, la clase `Dog` hereda de la clase `Animal`. La clase `Dog` tiene un método `bark` adicional, pero
también hereda el método `eat` de la clase `Animal`.

## Palabra clave `extends`

En Java, la herencia se implementa utilizando la palabra clave `extends`. Al definir una clase derivada, se utiliza la
palabra clave `extends` seguida del nombre de la clase base.

```java
public class Dog extends Animal {
    // Código de la clase Dog
}
```

## Herencia de múltiples clases

Java no permite la herencia de múltiples clases, es decir, una clase no puede heredar de más de una clase base. Sin
embargo, Java admite la herencia múltiple a través de interfaces, que se discutirán en un tema posterior.
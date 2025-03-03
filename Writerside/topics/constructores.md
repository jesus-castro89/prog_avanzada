# Constructores `private` y `protected`

En Java, los constructores son métodos especiales que se utilizan para inicializar objetos. Los constructores tienen el
mismo nombre que la clase y no tienen un tipo de retorno. En Java, los constructores pueden ser `public`, `private`,
`protected` o `default`.

En este artículo, veremos cómo se pueden utilizar los constructores `private` y `protected` en Java.

## Constructores `private`

Un constructor `private` es un constructor que solo se puede invocar desde dentro de la clase en la que se define. Esto
significa que no se puede crear una instancia de la clase desde fuera de la clase. Los constructores `private` se
utilizan para implementar el patrón de diseño Singleton, que garantiza que solo haya una instancia de una clase en un
programa.

Aquí hay un ejemplo de cómo se puede definir un constructor `private` en Java:

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {
        // Constructor privado
    }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

En este ejemplo, la clase `Singleton` tiene un constructor `private` que se utiliza para garantizar que solo haya una
instancia de la clase en un programa.

## Constructores `protected`

Un constructor `protected` es un constructor que solo se puede invocar desde dentro de la clase en la que se define o
desde una subclase de la clase en la que se define. Esto significa que no se puede crear una instancia de la clase desde
fuera de la clase, pero se puede crear una instancia de la clase desde una subclase.

Aquí hay un ejemplo de cómo se puede definir un constructor `protected` en Java:

```java
public class Animal {
    protected String nombre;
    protected int edad;

    protected Animal(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }
}
```

```java
public class Perro extends Animal {
    private String raza;

    public Perro(String nombre, int edad, String raza) {
        super(nombre, edad);
        this.raza = raza;
    }
}
```

En este ejemplo, la clase `Animal` tiene un constructor `protected` que se utiliza para inicializar los campos `nombre`
y `edad`. La clase `Perro` tiene un constructor que invoca el constructor `protected` de la clase `Animal` para
inicializar los campos `nombre` y `edad` y también inicializa el campo `raza`.

## Conclusión

En este artículo, hemos visto cómo se pueden utilizar los constructores `private` y `protected` en Java. Los
constructores `private` se utilizan para garantizar que solo haya una instancia de una clase en un programa, mientras
que los constructores `protected` se utilizan para inicializar los campos de una clase y permitir que las subclases
accedan a ellos.
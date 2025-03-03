# La palabra reservada `super`

La palabra reservada `super` en Java se utiliza para hacer referencia a la clase base de una clase derivada. Se puede
utilizar para acceder a los miembros y métodos de la clase base desde la clase derivada y para invocar el constructor de
la clase base desde el constructor de la clase derivada.

## Acceso a miembros y métodos de la clase base

Cuando una clase hereda de otra clase, puede acceder a los miembros y métodos de la clase base utilizando la palabra
reservada `super`. Por ejemplo, si una clase derivada tiene un método con el mismo nombre que un método de la clase
base, se puede utilizar `super` para llamar al método de la clase base. Aquí hay un ejemplo de cómo se puede utilizar
`super` para acceder a un método de la clase base:

```java
public class Animal {
    public void comer() {
        System.out.println("El animal está comiendo");
    }
}
```

```java
public class Perro extends Animal {
    public void comer() {
        super.comer();
        System.out.println("El perro está comiendo");
    }
}
```

En este ejemplo, la clase `Perro` hereda de la clase `Animal` y tiene un método `comer` que llama al método `comer` de
la clase `Animal` utilizando `super`. Esto permite que la clase `Perro` agregue su propia funcionalidad al método
`comer` sin tener que reescribir todo el código del método `comer` de la clase `Animal`.

## Invocación del constructor de la clase base

La palabra reservada `super` también se puede utilizar para invocar el constructor de la clase base desde el constructor
de la clase derivada. Esto se hace utilizando `super` seguido de paréntesis que contienen los argumentos necesarios para
el constructor de la clase base. Aquí hay un ejemplo de cómo se puede utilizar `super` para invocar el constructor de la
clase base:

```java
public class Animal {
    protected String nombre;
    protected int edad;

    public Animal(String nombre, int edad) {
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

En este ejemplo, la clase `Perro` hereda de la clase `Animal` y tiene un constructor que invoca el constructor de la
clase `Animal` utilizando `super`. Esto permite que la clase `Perro` inicialice los campos `nombre` y `edad` de la clase
`Animal` antes de inicializar su propio campo `raza`.

> **Nota**: La palabra reservada `super` solo se puede utilizar en el contexto de una clase derivada para hacer
> referencia a la clase base. No se puede utilizar en una clase que no hereda de otra clase.

> En el caso de los constructores, la palabra reservada `super` debe ser la primera instrucción en el constructor de la
> clase derivada y solo se puede utilizar una vez para invocar el constructor de la clase base. Si no se utiliza `super`
> para invocar el constructor de la clase base, se invocará automáticamente el constructor sin argumentos de la clase
> base. Si la clase base no tiene un constructor sin argumentos, se debe invocar explícitamente un constructor de la
> clase base utilizando `super`.

## Conclusión

La palabra reservada `super` en Java es una herramienta poderosa que se utiliza para hacer referencia a la clase base de
una clase derivada. Se puede utilizar para acceder a los miembros y métodos de la clase base y para invocar el
constructor de la clase base desde el constructor de la clase derivada. Esto permite que las clases derivadas hereden
funcionalidad de la clase base y extiendan su comportamiento de manera eficiente.
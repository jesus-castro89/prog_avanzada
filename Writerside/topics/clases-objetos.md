# Clases y objetos

En Java, una clase es una plantilla para crear objetos. Un objeto es una instancia de una clase. Las clases y los
objetos son conceptos fundamentales en la programación orientada a objetos.

## Clases

Una clase en Java define el comportamiento y las propiedades de un objeto. Una clase puede contener campos (variables),
métodos (funciones) y constructores. Los campos representan las propiedades del objeto, los métodos representan el
comportamiento del objeto y los constructores se utilizan para inicializar el objeto.

Por ejemplo, la siguiente clase `Persona` define una clase que representa a una persona con un nombre y una edad:

```java
public class Persona {
    private String nombre;
    private int edad;

    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }
}
```

En este ejemplo, la clase `Persona` tiene dos campos `nombre` y `edad`, un constructor que inicializa los campos, y
métodos `getNombre`, `setNombre`, `getEdad` y `setEdad` para acceder y modificar los campos.

## Objetos

Un objeto en Java es una instancia de una clase. Para crear un objeto, se utiliza la palabra clave `new` seguida del
nombre de la clase y los argumentos del constructor. Por ejemplo, para crear un objeto de la clase `Persona`, se puede
hacer lo siguiente:

```java
Persona persona = new Persona("Juan", 30);
```

En este ejemplo, se crea un objeto `persona` de la clase `Persona` con el nombre "Juan" y la edad 30.

Los objetos en Java pueden interactuar entre sí a través de métodos y campos. Por ejemplo, se puede acceder a los
métodos y campos de un objeto de la siguiente manera:

```java
String nombre = persona.getNombre();
int edad = persona.getEdad();

System.out.println("Nombre: " + nombre);
System.out.println("Edad: " + edad);
```

En este ejemplo, se accede a los métodos `getNombre` y `getEdad` del objeto `persona` para obtener el nombre y la edad
de la persona, respectivamente.

## Conclusiones

Las clases y los objetos son conceptos fundamentales en la programación orientada a objetos. Las clases definen el
comportamiento y las propiedades de los objetos, y los objetos son instancias de una clase. Al utilizar clases y
objetos, se pueden modelar entidades del mundo real de manera eficiente y reutilizable.
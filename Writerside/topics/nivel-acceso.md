# Niveles de Acceso en Java

En Java, los niveles de acceso o *access modifiers* son palabras clave que se utilizan para controlar la visibilidad de
las clases, campos, métodos y constructores en un programa. Los niveles de acceso permiten restringir el acceso a los
miembros de una clase y proteger la integridad de los datos.

## Niveles de Acceso

En Java, existen cuatro niveles de acceso que se pueden aplicar a los miembros de una clase:

| Nivel de Acceso | Descripción                                             |
|-----------------|---------------------------------------------------------|
| `public`        | Acceso desde cualquier clase en cualquier paquete.      |
| `protected`     | Acceso desde la misma clase y subclases.                |
| `default`       | Acceso desde la misma clase y clases del mismo paquete. |
| `private`       | Acceso solo desde la misma clase.                       |
| `package`       | Acceso desde la misma clase y clases del mismo paquete. |

## Uso de Niveles de Acceso

Los niveles de acceso se utilizan para controlar la visibilidad de los miembros de una clase y proteger los datos de
acceso no autorizado. Por ejemplo, si se declara un campo como `private`, solo se podrá acceder a él desde la misma
clase. Si se declara un método como `public`, se podrá acceder a él desde cualquier clase en cualquier paquete.

## Ejemplo de Niveles de Acceso

A continuación, se muestra un ejemplo de cómo se pueden aplicar los niveles de acceso en Java:

```java
public class Persona {
    private String nombre;
    protected int edad;
    int altura;
    public String genero;

    public Persona(String nombre, int edad, int altura, String genero) {
        this.nombre = nombre;
        this.edad = edad;
        this.altura = altura;
        this.genero = genero;
    }

    private void saludar() {
        System.out.println("Hola, soy " + nombre);
    }

    protected void despedirse() {
        System.out.println("Adiós, hasta luego");
    }

    void presentarse() {
        System.out.println("Hola, mi nombre es " + nombre);
    }

    public void mostrarDatos() {
        System.out.println("Nombre: " + nombre);
        System.out.println("Edad: " + edad);
        System.out.println("Altura: " + altura);
        System.out.println("Género: " + genero);
    }
}
```

En este ejemplo, se define una clase `Persona` con varios campos y métodos con diferentes niveles de acceso. El campo
`nombre` es `private`, el campo `edad` es `protected`, el campo `altura` es `default` y el campo `genero` es `public`.
Los métodos `saludar`, `despedirse` y `presentarse` tienen diferentes niveles de acceso para controlar quién puede
llamarlos. El método `mostrarDatos` es `public` y se puede acceder desde cualquier clase en cualquier paquete.

## Resumen

Los niveles de acceso en Java son una característica importante que permite controlar la visibilidad de los miembros de
una clase y proteger los datos de acceso no autorizado. Al utilizar los niveles de acceso adecuadamente, se puede
mejorar la seguridad y la integridad de un programa Java.
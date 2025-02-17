# Paso por valor y por referencia

En Java, los parámetros de los métodos se pasan por valor, lo que significa que se crea una copia del valor original y
se pasa esa copia al método. Esto se aplica tanto a los tipos primitivos como a los objetos en Java.

## Paso por Valor

Cuando se pasa un parámetro por valor a un método en Java, se crea una copia del valor original y se pasa esa copia al
método. Esto significa que cualquier cambio realizado en el parámetro dentro del método no afectará al valor original
fuera del método.

Por ejemplo, en el siguiente código:

```java
public class Main {
    public static void main(String[] args) {
        int numero = 5;
        incrementar(numero);
        System.out.println(numero); // Imprime 5
    }

    public static void incrementar(int num) {
        num++;
    }
}
```

En este caso, se ha declarado una variable `numero` con el valor `5` y se ha llamado al método `incrementar` con ese
valor. Dentro del método `incrementar`, se incrementa el valor de `num` en `1`, pero este cambio no afecta al valor
original de `numero` fuera del método.

> **Nota:** Los tipos primitivos en Java se pasan por valor, lo que significa que se crea una copia del valor original y
> se pasa esa copia al método.

## Paso por Referencia

En Java, los objetos se pasan por valor, lo que significa que se crea una copia de la referencia al objeto y se pasa esa
copia al método. Esto significa que cualquier cambio realizado en el objeto dentro del método afectará al objeto
original fuera del método, pero no se puede cambiar la referencia al objeto.

Por ejemplo, en el siguiente código:

```java
public class Main {
    public static void main(String[] args) {
        Persona persona = new Persona("Juan");
        cambiarNombre(persona);
        System.out.println(persona.getNombre()); // Imprime "Pedro"
    }

    public static void cambiarNombre(Persona p) {
        p.setNombre("Pedro");
    }
}

class Persona {
    private String nombre;

    public Persona(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
}
```

En este caso, se ha creado una instancia de la clase `Persona` con el nombre `Juan` y se ha llamado al método
`cambiarNombre` con esa instancia. Dentro del método `cambiarNombre`, se ha cambiado el nombre de la persona a
`Pedro`, y este cambio afecta al objeto original fuera del método.

> **Nota:** Los objetos en Java se pasan por valor, lo que significa que se crea una copia de la referencia al objeto y
> se pasa esa copia al método. Cualquier cambio realizado en el objeto dentro del método afectará al objeto original
> fuera del método.

## Conclusión

En Java, los parámetros de los métodos se pasan por valor, lo que significa que se crea una copia del valor original y
se pasa esa copia al método. Esto se aplica tanto a los tipos primitivos como a los objetos en Java. Los tipos
primitivos se pasan por valor, lo que significa que se crea una copia del valor original y se pasa esa copia al método.

Los objetos se pasan por valor, lo que significa que se crea una copia de la referencia al objeto y se pasa esa copia al
método. Cualquier cambio realizado en el objeto dentro del método afectará al objeto original fuera del método, pero no
se puede cambiar la referencia al objeto.
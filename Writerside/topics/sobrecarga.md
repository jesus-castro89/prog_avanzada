# Sobrecarga en Java

La sobrecarga de métodos en Java es una técnica que permite definir varios métodos con el mismo nombre en una clase,
pero con diferentes parámetros. Esto significa que se pueden tener varios métodos con el mismo nombre, pero con
diferentes tipos de parámetros, lo que permite a los programadores escribir código más limpio y fácil de entender.

## Ejemplo de Sobrecarga

Por ejemplo, en el siguiente código se muestra cómo se pueden definir varios métodos con el mismo nombre, pero con
diferentes tipos de parámetros:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println(sumar(5, 10)); // Imprime 15
        System.out.println(sumar(5.5, 10.5)); // Imprime 16.0
    }

    public static int sumar(int a, int b) {
        return a + b;
    }

    public static double sumar(double a, double b) {
        return a + b;
    }
}
```

En este caso, se han definido dos métodos `sumar` con el mismo nombre, pero con diferentes tipos de parámetros. Uno
acepta dos enteros como parámetros y devuelve un entero, mientras que el otro acepta dos números de punto flotante
como parámetros y devuelve un número de punto flotante.

## Reglas de Sobrecarga

Para que dos métodos se consideren sobrecargados, deben cumplir con las siguientes reglas:

1. Los métodos deben tener el mismo nombre.
2. Los métodos deben tener diferentes tipos de parámetros.
3. Los métodos pueden tener diferentes números de parámetros.
4. Los métodos pueden tener diferentes tipos de retorno.
5. Los métodos pueden tener diferentes modificadores de acceso.
6. Los métodos pueden lanzar diferentes excepciones.
7. Los métodos no pueden ser sobrecargados solo por el tipo de retorno.
8. Los métodos no pueden ser sobrecargados solo por el modificador de acceso.
9. Los métodos no pueden ser sobrecargados solo por el número de parámetros.
10. Los métodos no pueden ser sobrecargados solo por el tipo de excepción lanzada.
11. Los métodos no pueden ser sobrecargados solo por el tipo de parámetros.
12. Los métodos no pueden ser sobrecargados solo por el orden de los parámetros.

## Ventajas de la Sobrecarga

La sobrecarga de métodos en Java tiene varias ventajas, entre las que se incluyen:

1. **Facilidad de uso:** Permite a los programadores escribir código más limpio y fácil de entender al tener métodos con
   el mismo nombre pero diferentes tipos de parámetros.
2. **Reutilización de código:** Permite a los programadores reutilizar métodos con el mismo nombre en diferentes partes
   del código.
3. **Flexibilidad:** Permite a los programadores definir métodos con diferentes tipos de parámetros y tipos de retorno
   para adaptarse a diferentes situaciones.
4. **Legibilidad:** Facilita la lectura y comprensión del código al tener métodos con el mismo nombre pero diferentes
   tipos de parámetros.
5. **Mantenimiento:** Facilita el mantenimiento del código al tener métodos con el mismo nombre pero diferentes tipos de
   parámetros, lo que permite realizar cambios de forma más sencilla.
6. **Polimorfismo:** Permite a los programadores utilizar polimorfismo para llamar a métodos con el mismo nombre pero
   diferentes tipos de parámetros.

## Conclusión

En resumen, la sobrecarga de métodos en Java es una técnica poderosa que permite a los programadores escribir código más
limpio, reutilizable y fácil de entender al definir varios métodos con el mismo nombre pero con diferentes tipos de
parámetros.
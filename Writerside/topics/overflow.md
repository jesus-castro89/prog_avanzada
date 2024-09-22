# Sobrecarga de métodos

La sobrecarga es un concepto que permite a los desarrolladores definir múltiples métodos con el mismo nombre en una
clase, pero con diferentes parámetros. Esto significa que los métodos pueden realizar tareas similares, pero con
diferentes tipos de datos o cantidades de parámetros.

## Ejemplo de sobrecarga

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}
```

En este ejemplo, la clase `Calculator` define dos métodos `add` con el mismo nombre, pero con diferentes tipos de
parámetros (`int` y `double`). Esto permite a los desarrolladores utilizar el método `add` con diferentes tipos de
datos sin tener que cambiar el nombre del método.

## Llamada de métodos sobrecargados

```java
Calculator calculator = new Calculator();
// Llamada a los métodos sobrecargados
// Se infiere que se llama al método add(int, int)
int sumInt = calculator.add(1, 2);
// Se infiere que se llama al método add(double, double)
double sumDouble = calculator.add(1.5, 2.5);
/*
 * Error: No se puede encontrar el método add(int, double)
 * Se infiere que se llama al método add(double, double)
 * Se convierte el primer argumento de int a double de forma implícita
 * y se llama al método add(double, double). Por lo que hay que
 * tener cuidado con la sobrecarga de métodos con tipos de datos
 * que se puedan convertir de forma implícita.
 */
sumDouble = calculator.add(1, 2.5);
// Error: No se puede encontrar el método add(int, int, int)
sumInt = calculator.add(1, 2, 3);
```

En este ejemplo, se crea una instancia de la clase `Calculator` y se llama al método `add` con diferentes tipos de
parámetros. La sobrecarga permite a los desarrolladores utilizar el mismo nombre de método para realizar tareas
similares con diferentes tipos de datos.

## Reglas de la sobrecarga

Para sobrecargar un método en Java, se deben seguir las siguientes reglas:

- Los métodos deben tener el mismo nombre.
- Los métodos deben tener diferentes tipos de parámetros o una cantidad diferente de parámetros.
- Los métodos pueden tener diferentes tipos de retorno.
- Los métodos pueden lanzar diferentes excepciones.
- Los métodos no pueden ser sobrecargados solo cambiando el tipo de retorno.
- Los métodos no pueden ser sobrecargados solo cambiando el modificador de acceso.
- Los métodos no pueden ser sobrecargados solo cambiando el modificador `static`.
- Los métodos no pueden ser sobrecargados solo cambiando el modificador `final`.
- Los métodos no pueden ser sobrecargados solo cambiando el modificador `abstract`.

## Ventajas de la sobrecarga

La sobrecarga ofrece las siguientes ventajas:

- **Reutilización de nombres**: Permite a los desarrolladores reutilizar nombres de métodos para realizar tareas
  similares con diferentes tipos de datos.
- **Facilidad de uso**: Simplifica la interfaz de programación al permitir a los desarrolladores utilizar el mismo
  nombre de método para realizar tareas similares.
- **Flexibilidad**: Proporciona flexibilidad al permitir a los desarrolladores definir múltiples versiones de un método
  con diferentes parámetros.
- **Legibilidad**: Mejora la legibilidad del código al utilizar nombres de métodos intuitivos y descriptivos.
- **Mantenibilidad**: Facilita el mantenimiento del código al agrupar métodos relacionados bajo el mismo nombre.
- **Polimorfismo**: Permite el polimorfismo al permitir a los objetos responder de manera diferente a los mismos
  mensajes.
- **Eficiencia**: Mejora la eficiencia al permitir a los desarrolladores reutilizar métodos existentes en lugar de
  crear nuevos métodos para tareas similares.
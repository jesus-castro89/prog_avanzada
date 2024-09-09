# Trabajando con una sola clase

En Java, una clase es una plantilla para crear objetos. Cada clase define un conjunto de atributos y métodos que
caracterizan a los objetos que se pueden crear a partir de ella. Los atributos representan el estado de los objetos, y
los métodos representan su comportamiento.

## Definición de una clase

Para definir una clase en Java, se utiliza la palabra clave `class`, seguida del nombre de la clase y de un bloque de
código que contiene los atributos y métodos de la clase. Por ejemplo:

```java
public class Algorithm{
}
```

En este ejemplo, se define una clase llamada `Algorithm` que no tiene atributos ni métodos. Para añadir métodos, se
pueden definir dentro del bloque de código de la clase. Por ejemplo:

```java
import javax.swing.*;

public class Algorithm {

    public void factorial() {
        int value = Integer.parseInt(
                JOptionPane.showInputDialog("Introduce el valor a calcular su factorial"));
        int factorial = 1;
        for (int i = 1; i <= value; i++) {
            factorial *= i;
        }
        String message = String.format("El factorial de %d es %d", value, factorial);
        JOptionPane.showMessageDialog(null, message);
    }
```

En este ejemplo, se añade un método llamado `factorial` que calcula el factorial de un número introducido por el
usuario. El resultado se muestra en un cuadro de diálogo.

## Creación de objetos

Una vez definida una clase, se pueden crear objetos a partir de ella. Para crear un objeto en Java, se utiliza la
palabra clave `new`, seguida del nombre de la clase y de los paréntesis. Por ejemplo:

```java
import javax.swing.*;

public class Algorithm {

    public static void main(String[] args) {
        Algorithm algorithm = new Algorithm();
        algorithm.factorial();
    }

    public void factorial() {
        int value = Integer.parseInt(
                JOptionPane.showInputDialog("Introduce el valor a calcular su factorial"));
        int factorial = 1;
        for (int i = 1; i <= value; i++) {
            factorial *= i;
        }
        String message = String.format("El factorial de %d es %d", value, factorial);
        JOptionPane.showMessageDialog(null, message);
    }
```

Esta línea es la que permite crear el objeto:

```java
    Algorithm algorithm = new Algorithm();
```

Y esta invocar o llamar a la función `factorial`:

```java
    algorithm.factorial();
```

## Personalizando la salida de datos

Para personalizar una ventana emergente se puede utilizar el método `UIManager.put` de la clase `UIManager`. Por
ejemplo:

```java
// Personalizar el tamaño y la fuente del texto de los mensajes
UIManager.put("OptionPane.messageFont", 
    new Font("Grenze Gotisch", Font.BOLD, 20));
// Personalizar el tamaño y la fuente de los botones de los mensajes
UIManager.put("OptionPane.buttonFont", 
    new Font("Grenze Gotisch", Font.BOLD, 20));
// Cambiar el color del texto de los mensajes
UIManager.put("OptionPane.messageForeground", Color.RED);
```
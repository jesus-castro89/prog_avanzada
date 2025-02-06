# MessageDialog

La función `showMessageDialog` de la clase `JOptionPane` se utiliza para mostrar un mensaje en una ventana emergente.
Esta función tiene varios parámetros que permiten personalizar el mensaje y el tipo de ventana emergente que se
mostrará.

## Sintaxis de la función showMessageDialog con 2 parámetros

La sintaxis de la función `showMessageDialog` con 2 parámetros es la siguiente:

```java
JOptionPane.showMessageDialog(Component parentComponent, Object message);
```

Donde:

- `parentComponent`: Es el componente padre de la ventana emergente. Puede ser `null` si no se desea especificar un
  componente padre.
- `message`: Es el mensaje que se mostrará en la ventana emergente. Puede ser de tipo `String`, `Icon`, `Component` o
  `Object`.

### Ejemplo con 2 parámetros

```java
JOptionPane.showMessageDialog(null, "Este es un mensaje de prueba");
```

## Sintaxis de la función showMessageDialog con 4 parámetros

La sintaxis de la función `showMessageDialog` es la siguiente:

```java
JOptionPane.showMessageDialog(Component parentComponent, Object message, String title, int messageType);
```

Donde:

- `title`: Es el título de la ventana emergente.
- `messageType`: Es el tipo de mensaje que se mostrará en la ventana emergente.

## Tipos de mensajes

La función `showMessageDialog` permite mostrar diferentes tipos de mensajes en la ventana emergente que son:

| Tipo de mensaje                   | Descripción                                                    | 
|-----------------------------------|----------------------------------------------------------------|
| `JOptionPane.PLAIN_MESSAGE`       | Muestra un mensaje simple sin icono.                           |
| `JOptionPane.INFORMATION_MESSAGE` | Muestra un mensaje informativo con un icono de información.    |
| `JOptionPane.QUESTION_MESSAGE`    | Muestra un mensaje de pregunta con un icono de interrogación.  |
| `JOptionPane.WARNING_MESSAGE`     | Muestra un mensaje de advertencia con un icono de advertencia. |
| `JOptionPane.ERROR_MESSAGE`       | Muestra un mensaje de error con un icono de error.             |

## Variante de la función showMessageDialog

La función `showMessageDialog` también tiene una variante que permite personalizar la ventana emergente con un icono
personalizado. La sintaxis de esta variante es la siguiente:

```java
JOptionPane.showMessageDialog(Component parentComponent, Object message, String title, int messageType, Icon icon);
```

Donde:

- `icon`: Es el icono que se mostrará en la ventana emergente. Puede ser de tipo `Icon`.

## Ejemplo

A continuación se muestra un ejemplo de cómo utilizar la función `showMessageDialog` para mostrar un mensaje informativo
en una ventana emergente:

```java
import javax.swing.JOptionPane;

public class MessageDialogExample {

    public static void main(String[] args) {
        JOptionPane.showMessageDialog(null, "Este es un mensaje informativo", 
                                      "Información", JOptionPane.INFORMATION_MESSAGE);
    }
}
```

En este ejemplo, se muestra un mensaje informativo con el texto `"Este es un mensaje informativo"` y el título
`"Información"`.

## Conclusión

La función `showMessageDialog` de la clase `JOptionPane` es una forma sencilla de mostrar mensajes en una ventana
emergente con diferentes estilos y tipos de mensajes. Puedes personalizar el mensaje y el tipo de ventana emergente
según tus necesidades.
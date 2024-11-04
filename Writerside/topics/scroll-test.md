# La clase JScrollPane

En esta sección, vamos a crear un JScrollPane que se utilizará para mostrar un JTextArea en la parte inferior de la
ventana principal. Este JScrollPane se llamará `textScroll` y contendrá un JTextArea llamado `textDisplay` que mostrará
los mensajes al jugador.

Para crear el JScrollPane, vamos a seguir los siguientes pasos:

1. Crearemos una ventana con el editor gráfico de IntelliJ IDEA.
2. Agregaremos un JScrollPane al panel inferior de la ventana.
3. Agregaremos un JTextArea al JScrollPane para mostrar los mensajes al jugador.
4. Haz que el texto del JTextArea no sea editable.
5. Estableceremos el color de fondo del JTextArea de
   `Color.BLACK` y el color de la fuente de `Color.WHITE`.
6. Estableceremos el tamaño del JTextArea y JScrollPane a 1100x200.
7. Estableceremos la política de desplazamiento vertical del JScrollPane a
   `JScrollPane.VERTICAL_SCROLLBAR_ALWAYS`, mientras que la política de desplazamiento horizontal será
   `JScrollPane.HORIZONTAL_SCROLLBAR_NEVER`.
8. Dejaremos la fuente del JTextArea en 22 puntos y estableceremos un borde vacío de 10 píxeles en el JTextArea.
9. Estableceremos el ajuste de línea y la palabra de ajuste de línea en el JTextArea de la siguiente manera:
   ```java
   textDisplay.setLineWrap(true);
   textDisplay.setWrapStyleWord(true);
   ```
10. Dentro de la clase de nuestra ventana, agregaremos un método para mostrar mensajes en el JTextArea.
11. Dentro del método, agregaremos un mensaje al JTextArea y haremos que el JTextArea se desplace automáticamente al
    final del texto.
12. Finalmente, llamaremos al método para mostrar mensajes en el JTextArea desde cualquier parte de nuestra aplicación.
13. Ejecutaremos la aplicación y verificaremos que el JScrollPane y el JTextArea se muestren correctamente en la parte
    inferior de la ventana principal.
14. Verificaremos que los mensajes se muestren correctamente en el JTextArea y que el JTextArea se desplace
    automáticamente al final del texto.
15. Verificaremos que el JTextArea no sea editable y que el color de fondo y la fuente del JTextArea sean los
    correctos.

Con estos pasos, habremos creado un JScrollPane que se utilizará para mostrar mensajes al jugador en la parte inferior
de la ventana principal de nuestra aplicación.

## Función para mostrar mensajes

Para mostrar mensajes en el JTextArea, agregaremos un método a nuestra clase de ventana principal que se encargará de
agregar mensajes al JTextArea y desplazar automáticamente el JTextArea al final del texto. Aquí tienes un ejemplo de
cómo implementar esta función:

```java
public void showMessage(String message) {
    textDisplay.append(message + "\n");
    textDisplay.setCaretPosition(textDisplay.getDocument().getLength());
}
```

En este código, hemos creado un método llamado `showMessage` que recibe un mensaje como parámetro. Dentro del método,
agregamos el mensaje al JTextArea utilizando el método `append` y luego desplazamos el JTextArea al final del texto
utilizando el método `setCaretPosition`.

> **Nota:** Se asume que `textDisplay` es el nombre del JTextArea que contiene los mensajes.

> **Nota:** El método `setCaretPosition` se utiliza para establecer la posición del cursor en el JTextArea. Al pasar
> `textDisplay.getDocument().getLength()` como argumento, estamos estableciendo la posición del cursor al final del
> texto en el JTextArea.
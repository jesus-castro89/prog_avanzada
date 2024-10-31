# 20. El área de mensajes

En esta sección, vamos a crear el área de mensajes que se mostrará en la parte inferior de la ventana principal. Esta
área de mensajes se utilizará para mostrar mensajes al jugador, como mensajes de error, advertencias, etc.

## El área de mensajes

Para el área de mensajes, vamos a utilizar un componente de texto que se mostrará en la parte inferior de la ventana
principal. Este componente de texto se llamará `MessageArea` y se ubicará en la parte inferior de la ventana principal.

Para crear el área de mensajes, vamos a seguir los siguientes pasos:

1. Dividiremos el panel inferior en dos paneles, uno para el área de mensajes y otro para los botones de acción.
2. En el área de botones de acción (izquierdo), agregaremos tres botones, uno para atacar, otro para huir y otro
   para usar habilidades.
3. En el área de mensajes (derecho), agregaremos un JScrollPane (llamado `textScroll`) que contendrá un JTextArea (
   llamada `textDisplay`) que mostrará los mensajes al jugador.
4. Cambiaremos el ancho del área de botones a 250, mientras el del área de mensajes será de 1100.

Para hacer que el área de mensajes funcione correctamente, vamos a modificar la función `initComponents` de la clase
`MainPanel` de la siguiente manera:

```java
private void initComponents() {
        // Acciones previas en el panel
        textScroll.getViewport().setOpaque(false);
        textScroll.setVerticalScrollBarPolicy(
                JScrollPane.VERTICAL_SCROLLBAR_ALWAYS);
        textScroll.setHorizontalScrollBarPolicy(
                JScrollPane.HORIZONTAL_SCROLLBAR_NEVER);
        textDisplay.setFont(UIConstants.FONT.deriveFont(22f));
        textDisplay.setBorder(new EmptyBorder(10, 10, 10, 10));
        textDisplay.setForeground(Color.WHITE);
        textDisplay.setLineWrap(true);
        textDisplay.setWrapStyleWord(true);
}
```

> **Nota:** La clase `UIConstants` es una clase que contiene constantes que se utilizan en la interfaz de usuario.

Con estos cambios, hemos creado el área de mensajes que se mostrará en la parte inferior de la ventana principal. En
esta área de mensajes, se mostrarán los mensajes al jugador, como mensajes de error, advertencias, etc.

> **Nota:** En el área de mensajes, se mostrarán los mensajes en un JTextArea que se encuentra dentro de un JScrollPane.
> Por lo que puedes cambiar el color de fondo del panel contenedor, o hacer que en dicho panel contenedor se dibuje una
> imagen de fondo.

> **Nota:** Recuerda que el área de mensajes debe tener un tamaño adecuado para que los mensajes se muestren
> correctamente al igual que los botones de acción.

## Conclusión

En esta sección, hemos creado el área de mensajes que se mostrará en la parte inferior de la ventana principal. Esta
área de mensajes se utilizará para mostrar mensajes al jugador, como mensajes de error, advertencias, etc. Además, hemos
agregado tres botones de acción en el área de botones de acción, uno para atacar, otro para huir y otro para usar
habilidades.
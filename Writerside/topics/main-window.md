# 23. Nuestra ventana principal

La ventana principal de nuestro juego es la interfaz principal que se mostrará al jugador. En esta ventana, el jugador
podrá ver la información de su personaje, los enemigos a los que se enfrentará, los mensajes que se mostrarán durante el
juego, etc.

En esta sección veremos la estructura de la ventana principal y cómo podemos modificarla para añadir nuevas
funcionalidades.

## Estructura de la ventana principal

Nuestra ventana principal estará compuesta por varios paneles que contendrán diferentes elementos de la interfaz de
usuario. Estos paneles se distribuirán de la siguiente manera:

1. **Panel superior:** En este panel se mostrará la información del jugador, como su nombre, nivel, vida, etc.
2. **Panel central:** En este panel se mostrarán los sprites de los personajes y enemigos.
3. **Panel inferior:** En este panel se mostrarán los mensajes al jugador y los botones de acción.

De tal manera que nuestra ventana se vea así:

![mainWindow.png](..%2Fimages%2FmainWindow.png){display:block}

## Creando la ventana principal

Para nuestra ventana deberemos de entrar en vista de diseño y continuar con nuestra ventana dividida en tres paneles.

### Panel superior

En el panel superior, agregaremos una etiqueta en el extremo izquierdo que muestre el portarretrato del jugador. Junto
a esta etiqueta, agregaremos otra etiqueta que muestre el nombre del jugador y su nivel, junto a ella, agregaremos una
etiqueta para el oro del jugador.

Sobre estas etiquetas, agregaremos tres etiquetas más, una para la vida del jugador, otra para la energía y otra para la
experiencia.

En la parte izquierda del panel, agregaremos una serie de botones que permitan al jugador acceder a diferentes opciones
del juego, como el inventario, la tienda, el herrero, etc. Recuerda que estos botones contarán con una clase que
los defina y que herede de `BaseButton`.

> **Nota:** Las etiquetas de la vida, energía y experiencia serán barras de progreso que se irán llenando conforme el
> jugador avance en el juego.

> **Nota:** Es recomendable seleccionar las tres etiquetas superiores y las dos inferiores y agruparlas en un `JPanel`
> para poder manipularlas de forma más sencilla. Recuerda quitar la opacidad de las etiquetas y paneles que agregues
> para que se muestren correctamente.

### Panel central

En el panel central, dividiremos el panel en dos partes, insertando un `JPanel` en cada lado. En el panel de la
izquierda, agregaremos una etiqueta que muestre el sprite del jugador. En el panel de la derecha, agregaremos una
etiqueta que muestre el sprite del enemigo y sobre esta dos más que muestren el nombre del enemigo y su vida.

> **Nota:** En el panel de sprites de los personajes, solo se mostrará un sprite, mientras que en el panel de sprites de
> los enemigos, se mostrarán tres sprites, uno para el enemigo, otro para el nombre del enemigo y otro para la vida del
> enemigo.

> **Nota:** Los sprites de los personajes y enemigos se mostrarán en el panel de sprites, pero no se moverán.

> **Nota:** Recuerda quitar la opacidad de las etiquetas y paneles que agregues para que se muestren los sprites.

### Panel inferior

En el panel inferior, dividiremos el panel en dos partes, uno para el área de mensajes y otro para los botones de
acción.

En el área de botones de acción (izquierdo), agregaremos tres botones, uno para atacar, otro para huir y otro para usar
habilidades.

En el área de mensajes (derecho), agregaremos un `JScrollPane` (llamado `textScroll`) que contendrá un `JTextArea`
(llamada `textDisplay`) que mostrará los mensajes al jugador.

Cambiaremos el ancho del área de botones a 250, mientras el del área de mensajes será de 1100.

Para hacer que el área de mensajes funcione correctamente, vamos a modificar la función `initComponents` de la clase
`MainPanel` de la siguiente manera:

```java
private void initComponents(){
        // Acciones previas en el panel
        // Definimos la forma de trabajo del ScrollPane
        // Hacemos que el ScrollPane no tenga bordes y sea transparente
        textScroll.getViewport().setOpaque(false);
        textScroll.setBorder(null);
        // Hacemos que el ScrollPane tenga solo la barra vertical
        textScroll.setVerticalScrollBarPolicy(
                JScrollPane.VERTICAL_SCROLLBAR_ALWAYS);
        textScroll.setHorizontalScrollBarPolicy(
                JScrollPane.HORIZONTAL_SCROLLBAR_NEVER);
        // Definimos el color de fondo del display en Blanco y su fuente en 28px
        textDisplay.setFont(UIConstants.FONT.deriveFont(28f));
        textDisplay.setForeground(Color.WHITE);
        // Configuramos el scrool del textDisplay
        textDisplay.setColumns(1);
        textDisplay.setEditable(false);
        textDisplay.setLineWrap(true);
        textDisplay.setWrapStyleWord(true);
}
```

> **Nota:** La clase `UIConstants` es una clase que contiene constantes que se utilizan en la interfaz de usuario.

Con estos cambios, hemos creado el área de mensajes que se mostrará en la parte inferior de la ventana principal. En
esta área de mensajes, se mostrarán los mensajes al jugador, como mensajes de error, advertencias, etc.

> **Nota:** En el área de mensajes, se mostrarán los mensajes en un `JTextArea` que se encuentra dentro de un
> `JScrollPane`. Por lo que puedes cambiar el color de fondo del panel contenedor, o hacer que en dicho panel
> contenedor se dibuje una imagen de fondo.

> **Nota:** Recuerda que el área de mensajes debe tener un tamaño adecuado para que los mensajes se muestren
> correctamente al igual que los botones de acción.

## Función para mostrar mensajes

Para mostrar mensajes en el `JTextArea`, agregaremos un método a nuestra clase de ventana principal que se encargará de
agregar mensajes al `JTextArea` y desplazar automáticamente el `JTextArea` al final del texto. Aquí tienes un ejemplo de
cómo implementar esta función:

```java
public void appendText(String text) {
    // Añadimos el texto al textDisplay
    textDisplay.append(text);
    // Hacemos que el textDisplay se desplace al final del texto
    textDisplay.setCaretPosition(textDisplay.getDocument().getLength());
}
```

> **Nota:** Se asume que `textDisplay` es el nombre del `JTextArea` que contiene los mensajes. Y que las funciones de
> `textDisplay` se encuentran en la clase `MainPanel`.

## Conclusión

En esta sección, hemos creado el área de mensajes que se mostrará en la parte inferior de la ventana principal. Esta
área de mensajes se utilizará para mostrar mensajes al jugador, como mensajes de error, advertencias, etc. Además, hemos
agregado tres botones de acción en el área de botones de acción, uno para atacar, otro para huir y otro para usar
habilidades.
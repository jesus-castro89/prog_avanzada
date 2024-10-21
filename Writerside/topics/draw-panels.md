# 14. Dibujando los paneles

Para efectos de nuestro proyecto, deberemos crear tres paneles que nos permitirán mostrar la interfaz de usuario del
juego. Estos paneles serán los siguientes:

1. **Panel superior**: Este panel nos permitirá mostrar la información del personaje, como su nombre, nivel y puntos de
   vida.
2. **Panel central**: Este panel nos permitirá mostrar el mapa del juego y la ubicación actual del personaje.
3. **Panel inferior**: Este panel nos permitirá mostrar los botones de acción que el jugador puede utilizar para
   interactuar con el juego.

Para poder crear estos paneles, es importante primero definir una clase que herede de `JPanel` y que nos permita
personalizar la apariencia de los paneles. A continuación, se muestra el código de la clase `BackgroundPanel`:

```java
package rpg.gui.panels;

import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;

public abstract class BackgroundPanel extends JPanel {

    protected ImageIcon backgroundImage;
    protected Dimension dimension;

    public BackgroundPanel() {
        init();
    }

    protected abstract void init();

    public void setDimension(Dimension dimension) {
        this.dimension = dimension;
        setPreferredSize(dimension);
        setMinimumSize(dimension);
        setMaximumSize(dimension);
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        // Gestor en 2D para gestionar mejor las cosas
        Graphics2D g2d = (Graphics2D) g;
        // Activamos el antialiasing para que las imágenes se vean mejor
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING,
                RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING,
                RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
        // Activamos la interpolación bicúbica para que las imágenes se vean mejor
        g2d.setRenderingHint(RenderingHints.KEY_INTERPOLATION,
                RenderingHints.VALUE_INTERPOLATION_BICUBIC);
        // Dibujamos la imagen de fondo estirada a lo largo del panel.
        g2d.drawImage(backgroundImage.getImage(), 0, 0,
                dimension.width, dimension.height, null);
    }
}
```

En este código, hemos creado una clase llamada `BackgroundPanel` que hereda de `JPanel`. En el constructor de la clase,
inicializamos el panel llamando al método `init`. Este método es abstracto y deberá ser implementado por las clases que
hereden de `BackgroundPanel`.

Además, la clase `BackgroundPanel` define un método `setDimension` que nos permite establecer las dimensiones del panel.
Este método se encarga de establecer el tamaño preferido, mínimo y máximo del panel de acuerdo a las dimensiones
proporcionadas.

Finalmente, la clase `BackgroundPanel` sobrescribe el método `paintComponent` para dibujar la imagen de fondo del panel.

## Clases `TopPanel`, `MiddlePanel` y `BottomPanel`

Las clases `TopPanel`, `MiddlePanel` y `BottomPanel` heredarán de `BackgroundPanel` y nos permitirán personalizar la
apariencia de los paneles de la interfaz de usuario.

### Clase `TopPanel`

```java
package rpg.gui.panels;

import rpg.gui.WindowConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class TopPanel extends BackgroundPanel {

    @Override
    protected void init() {
        // Buscamos la imagen por ahora directamente en los directorios
        backgroundImage = new ImageIcon(ImageCache.addImage("topPanel",
                "panels/statusPanel.png"));
        setDimension(WindowConstants.TOP_DIMENSION);
        setBorder(WindowConstants.EMPTY_BORDER);
    }
}
```

> **Nota**: En este código, hemos utilizado la clase `WindowConstants` para obtener las dimensiones y bordes de los
> paneles. Es importante tener en cuenta que estas clases y constantes deberán ser definidas en el proyecto para poder
> utilizarlas.

## Conclusiones

En este artículo, hemos aprendido cómo crear paneles personalizados en Java utilizando la clase `JPanel`. Hemos
definido una clase base llamada `BackgroundPanel` que nos permite personalizar la apariencia de los paneles de la
interfaz de usuario. Además, hemos creado las clases `TopPanel`, `MiddlePanel` y `BottomPanel` que heredan de
`BackgroundPanel` y nos permiten mostrar la interfaz de usuario del juego.
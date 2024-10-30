# 18. Las etiquetas de los nombres y el dinero

Para nuestro juego de roles, necesitamos etiquetas para los nombres y el dinero. Las etiquetas son una forma de
clasificar y organizar los datos. En este caso, las etiquetas nos ayudarán a identificar a los personajes y a los
objetos de valor. Las etiquetas de los nombres y el dinero son importantes porque nos permiten identificar a los
personajes y a los objetos de valor de forma rápida y sencilla. Además, las etiquetas nos ayudan a organizar y
clasificar los datos de forma eficiente. En este artículo, te explicaremos cómo crear etiquetas para los nombres y el
dinero en nuestro juego de roles.

## Etiquetas para los nombres

Las etiquetas para los nombres son una forma de identificar a los personajes de nuestro juego de roles. Las etiquetas
para los nombres nos permiten identificar a los personajes de forma rápida y sencilla. Además, las etiquetas para los
nombres nos ayudan a organizar y clasificar los datos de forma eficiente. Para crear etiquetas para los nombres,
necesitamos seguir los siguientes pasos:

1. Crearemos una clase que herede de `JLabel` para representar las etiquetas de los nombres.
2. Crearemos una clase UI que herede de `BasicLabelUI` para personalizar la apariencia de las etiquetas de los nombres.

> **Nota:** Recuerda que cada clase deberá de estar en su correspondiente paquete.

```java
package rpg.gui.labels;

import rpg.gui.ui.NameLabelUI;

import javax.swing.*;

public class NameLabel extends JLabel {

    public NameLabel(String name) {
        super();
        setText(name);
        setUI(new NameLabelUI());
    }
}
```

Con este código, hemos creado una clase `NameLabel` que hereda de `JLabel` y que representa las etiquetas de los
nombres. Además, hemos personalizado la apariencia de las etiquetas de los nombres mediante la clase `NameLabelUI`.

Para esta clase usaremos las siguientes imágenes:

- ![name_label_left.png](..%2Fimages%2Fname_label_left.png)
- ![name_label_center.png](..%2Fimages%2Fname_label_center.png)
- ![name_label_right.png](..%2Fimages%2Fname_label_right.png)

```java
package rpg.gui.ui;

import rpg.gui.UIConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;
import java.awt.image.BufferedImage;

public class NameLabelUI extends GameLabelUI {

    private final BufferedImage[] icons;

    public NameLabelUI() {

        super(null, null);
        icons = new BufferedImage[3];
        ImageCache.addImage("name_l", "labels/name_label_left.png");
        ImageCache.addImage("name_c", "labels/name_label_center.png");
        ImageCache.addImage("name_r", "labels/name_label_right.png");
        icons[0] = ImageCache.getImage("name_l");
        icons[1] = ImageCache.getImage("name_c");
        icons[2] = ImageCache.getImage("name_r");
    }

    @Override
    protected void installDefaults(JLabel c) {

        c.setFont(UIConstants.LABEL_FONT);
        c.setForeground(Color.BLACK);
        c.setVerticalAlignment(JLabel.CENTER);
        c.setHorizontalAlignment(JLabel.CENTER);
        c.setVerticalTextPosition(JLabel.CENTER);
        c.setHorizontalTextPosition(JLabel.CENTER);
        FontMetrics metrics = c.getFontMetrics(c.getFont());
        int textWidth = metrics.stringWidth(c.getText());
        c.setPreferredSize(new Dimension(textWidth + 44, 51));
    }

    @Override
    public void paint(Graphics g, JComponent c) {

        JLabel label = (JLabel) c;
        FontMetrics fm = g.getFontMetrics();
        String clippedText = layout(label, fm, c.getWidth(), c.getHeight());
        int textX = fm.stringWidth(label.getText());
        int textY = paintTextR.y;
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.drawImage(icons[0], 0, 0, icons[0].getWidth(), icons[0].getHeight(), c);
        g2d.translate(icons[0].getWidth(), 0);
        g2d.drawImage(icons[1], 0, 0, textX, icons[1].getHeight(), c);
        g2d.translate(textX, 0);
        g2d.drawImage(icons[2], 0, 0, icons[2].getWidth(), icons[2].getHeight(), c);
        g2d.translate(-textX, 0);
        g2d.drawString(clippedText, 0, textY + fm.getAscent());
    }
}
```

Con este código, hemos creado una clase `NameLabelUI` que hereda de `BasicLabelUI` y que personaliza la apariencia de
las etiquetas de los nombres. Además, hemos añadido las imágenes necesarias para personalizar la apariencia de las
etiquetas de los nombres de la siguiente manera:

* **Constructor:** Cargamos las imágenes necesarias para personalizar la apariencia de las etiquetas de los nombres.
* **`installDefaults`:** Establecemos la fuente, el color y las dimensiones de las etiquetas de los nombres. Toma en
  cuenta que calcula el ancho del texto y se le suma 44 píxeles para establecer la anchura de la etiqueta.
* **`paint`:** Dibujamos las imágenes necesarias para personalizar la apariencia de las etiquetas de los nombres y
  el texto correspondiente. Como puedes notar se dibuja cada una de las tres partes de la etiqueta y se añade el texto
  en la parte central.

> **Nota:** Recuerda que las imágenes deben estar en la carpeta `labels` dentro de la carpeta `image` o dónde hayas
> decidido guardar las imágenes.

Con esta configuración, nos aseguramos que sin importar el tamaño del texto, la etiqueta se ajustará a la longitud del
mismo.

## Etiqueta para el dinero

La etiqueta para el dinero es una forma de identificar la cantidad de piezas de oro con las que cuenta un personaje en
nuestro juego de roles. La etiqueta para el dinero nos permite identificar la cantidad de piezas de oro de forma rápida
y sencilla. Además, la etiqueta para el dinero nos ayuda a organizar y clasificar los datos de forma eficiente. Para
crear la etiqueta para el dinero.

La estructura de la clase `GoldLabel` es similar a la de `NameLabel`, pero con algunas diferencias.

```java
package rpg.gui.labels;

import rpg.gui.UIConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;

public class GoldLabel extends PortraitLabel {

    public GoldLabel() {
        super();
        setFont(UIConstants.LABEL_FONT.deriveFont(Font.BOLD, 20f));
        setForeground(Color.BLACK);
        setVerticalAlignment(JLabel.CENTER);
        setHorizontalAlignment(JLabel.CENTER);
        setVerticalTextPosition(JLabel.CENTER);
        setHorizontalTextPosition(JLabel.CENTER);
    }

    @Override
    public void initComponents() {
        ImageCache.addImage("gold", "labels/goldLabel.png");
        icon = ImageCache.getImageIcon("gold");
        setPreferredSize(new Dimension(
                icon.getIconWidth(), icon.getIconHeight()));
        setIcon(icon);
        setText("1000");
    }
}
```

En este caso, hemos creado una clase `GoldLabel` que hereda de `PortraitLabel` y que representa la etiqueta para el
dinero. Además, hemos personalizado la apariencia de la etiqueta para el dinero mediante la clase `PortraitLabel`.

Para esta clase usaremos la siguiente imagen:

- ![goldLabel.png](..%2Fimages%2FgoldLabel.png)

Con este código, hemos creado una clase `GoldLabel` que hereda de `PortraitLabel` y que representa la etiqueta para el
dinero. Además, hemos personalizado la apariencia de la etiqueta para el dinero mediante la clase `PortraitLabel`.

> **Nota:** Estamos usando la clase `PortraitLabel` para personalizar la apariencia de la etiqueta para el dinero
> Esto debido a que la estructura de la etiqueta para el dinero es similar a la de la etiqueta para los nombres. Solo
> que en esta última agregamos un texto que representa la cantidad de piezas de oro.
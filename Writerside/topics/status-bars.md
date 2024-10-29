# 17. Las barras de estado

Las barras de estado son un
a forma de mostrar información al usuario de una manera visual y rápida. Pueden ser usadas
para mostrar información sobre el progreso de una tarea, el estado de un proceso, o cualquier otra información que sea
relevante para el usuario.

Las barras de estado son comúnmente usadas en aplicaciones de escritorio y aplicaciones web, y son una forma efectiva
de comunicar información al usuario de una manera no intrusiva.

## Las imágenes básicas

Para efecto de este ejemplo de barras de estado, se usarán las siguientes imágenes:

* ![life_bar.png](..%2Fimages%2Flife_bar.png)
* ![life_container.png](..%2Fimages%2Flife_container.png)
* ![life_icon.png](..%2Fimages%2Flife_icon.png)

## Creando una barra de estado

Para nuestro proyecto crearemos dos clases específicas para las barras de estado: `BarLabel` y `BarLabelUI`, así como
un tipo enumerado `BarType` para definir los diferentes tipos de barras de estado que queremos mostrar.

Primero, definimos el tipo enumerado `BarType` dentro de nuestro paquete `rpg.enums`:

```java
package rpg.enums;

import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.image.BufferedImage;

public enum BarType {

    LIFE, MAGIC, EXPERIENCE;

    BufferedImage container;
    BufferedImage icon;
    BufferedImage bar;

    BarType() {
        switch (this) {
            case LIFE -> {
                container = ImageCache.addImage("life_container", "bars/life_container.png");
                icon = ImageCache.addImage("life_icon", "bars/life_icon.png");
                bar = ImageCache.addImage("life_bar", "bars/life_bar.png");
            }
            case MAGIC -> {
                // Se cargan las imágenes para la barra de magia
            }
            case EXPERIENCE -> {
                // Se cargan las imágenes para la barra de experiencia
            }
        }
    }

    public BufferedImage getContainer() {
        return container;
    }

    public BufferedImage getIcon() {
        return icon;
    }

    public BufferedImage getBar() {
        return bar;
    }
}
```

En este código, definimos un tipo enumerado `BarType` que contiene tres valores: `LIFE`, `MAGIC` y `EXPERIENCE`. Cada
valor tiene tres imágenes asociadas: `container`, `icon` y `bar`. Estas imágenes son cargadas en el constructor del
tipo enumerado usando la clase `ImageCache` que hemos definido previamente.

A continuación, definimos la clase `BarLabel` que representa una barra de estado en nuestra aplicación:

> **Nota**: La clase `BarLabel` extiende de `JLabel` y usa un `BarType` para determinar el tipo de barra de estado
> así como un valor actual y un valor máximo para la barra. Si no existe el paquete correspondiente `rpg.gui.labels`,
> se debe crear.

```java
package rpg.gui.labels;

import rpg.enums.BarType;
import rpg.gui.ui.BarLabelUI;

import javax.swing.*;

public class BarLabel extends JLabel {

    private int barValue;
    private int maxValue;
    private final BarType type;

    public BarLabel(int value, int maxValue, BarType type) {

        this.barValue = value;
        this.maxValue = maxValue;
        this.type = type;
        initComponents();
    }

    public void initComponents() {

        setBarValue(barValue);
        setUI(new BarLabelUI(type));
    }

    public void setBarValue(int value) {

        this.barValue = value;
        setText(String.format("%d / %d", value, maxValue));
    }
    
    // Otros métodos de la clase como los getters y setters
}
```

En este código, definimos la clase `BarLabel` que extiende de `JLabel` y representa una barra de estado en nuestra
aplicación. La clase tiene un constructor que toma un valor actual, un valor máximo y un `BarType` como parámetros.

La clase también tiene un método `initComponents()` que inicializa la barra de estado y un método `setBarValue()` que
actualiza el valor de la barra de estado y muestra el valor actual y el valor máximo en el texto de la barra.

Finalmente, definimos la clase `BarLabelUI` que es la clase de apariencia de la barra de estado:

```java
package rpg.gui.ui;

import rpg.enums.BarType;
import rpg.gui.UIConstants;
import rpg.gui.labels.BarLabel;

import javax.swing.*;
import javax.swing.plaf.basic.BasicLabelUI;
import java.awt.*;
import java.awt.image.BufferedImage;

public class BarLabelUI extends BasicLabelUI {

    private final BarType type;

    public BarLabelUI(BarType type) {
        this.type = type;
    }

    @Override
    protected void installDefaults(JLabel c) {

        c.setOpaque(false);
        c.setBorder(null);
        c.setForeground(Color.WHITE);
        c.setFont(UIConstants.BAR_LABEL_FONT);
        c.setVerticalAlignment(JLabel.BOTTOM);
        c.setVerticalTextPosition(JLabel.BOTTOM);
        c.setHorizontalAlignment(JLabel.RIGHT);
        c.setHorizontalTextPosition(JLabel.RIGHT);
    }

    @Override
    public Dimension getPreferredSize(JComponent c) {

        return getBarWidth();
    }

    @Override
    public Dimension getMinimumSize(JComponent c) {

        return getBarWidth();
    }

    @Override
    public Dimension getMaximumSize(JComponent c) {

        return getBarWidth();
    }

    @Override
    protected void paintEnabledText(JLabel l, Graphics g, String s, int textX, int textY) {

        int textMiddle = g.getFontMetrics(g.getFont()).stringWidth(s) / 2;
        g.drawString(s, textX-textMiddle-5, textY+3);
    }

    @Override
    public void paint(Graphics g, JComponent c) {

        Graphics2D g2d = (Graphics2D) g;
        BarLabel barLabel = (BarLabel) c;
        BufferedImage icon = type.getIcon();
        BufferedImage container = type.getContainer();
        BufferedImage bar = type.getBar();
        int barValue = getBarValue(barLabel);
        int maxValue = getMaxBarValue(barLabel);
        int iconX = 0;
        int iconY = 0;
        int iconWidth = UIConstants.BAR_ICON.width;
        int iconHeight = UIConstants.BAR_ICON.height;
        int displayX = UIConstants.BAR_ICON.width - 2;
        int displayY = iconY + 5;
        int displayWidth = UIConstants.BAR_DISPLAY.width;
        int displayHeight = UIConstants.BAR_DISPLAY.height;
        int barWidth = (int) ((double) barValue / maxValue * 157);
        int barHeight = 17;
        int barX = iconWidth + 9;
        int barY = iconY + 15;
        g2d.drawImage(icon, iconX, iconY, iconWidth, iconHeight, null);
        g2d.drawImage(container, displayX, displayY, displayWidth, displayHeight, null);
        g2d.drawImage(bar, barX, barY, barWidth, barHeight, null);
        super.paint(g, c);
    }

    private int getBarValue(JLabel c) {

        return ((BarLabel) c).getBarValue();
    }

    private int getMaxBarValue(JLabel c) {

        return ((BarLabel) c).getMaxValue();
    }

    private Dimension getBarWidth() {

        Dimension iconSize = UIConstants.BAR_ICON;
        Dimension displaySize = UIConstants.BAR_DISPLAY;
        int width = iconSize.width + displaySize.width;
        return new Dimension(width, iconSize.height + 5);
    }
}
```

En este código, definimos la clase `BarLabelUI` que extiende de `BasicLabelUI` y define la apariencia de la barra de
estado. La clase tiene un constructor que toma un `BarType` como parámetro y sobrescribe varios métodos para
personalizar la apariencia de la barra de estado.

### `installDefaults()`

Este método establece los valores predeterminados para la barra de estado, como el color del texto, la fuente y la
alineación del texto.

### `getPreferredSize()`, `getMinimumSize()`, `getMaximumSize()`

Estos métodos devuelven el tamaño preferido, mínimo y máximo de la barra de estado.

### `paintEnabledText()`

Este método pinta el texto de la barra de estado en la posición correcta. Para esto tomamos la fuente del texto y
calculamos el ancho del texto para centrarlo correctamente. Dividimos el ancho del texto por 2 y lo restamos a la
posición `textX` para centrar el texto.

### `paint()`

Este método pinta la barra de estado en la posición correcta. Primero, obtenemos las imágenes del icono, el contenedor
y la barra del tipo de barra de estado. Luego, calculamos las posiciones y dimensiones de cada elemento y las pintamos
en el contexto gráfico `g2d`.

Finalmente, definimos las constantes `UIConstants.BAR_ICON` y `UIConstants.BAR_DISPLAY` que representan el tamaño del
icono y el contenedor de la barra de estado respectivamente.

Con estas clases y métodos, hemos creado una forma efectiva de mostrar barras de estado en nuestra aplicación. Las
barras de estado son una forma visual y rápida de comunicar información al usuario y pueden ser usadas para mostrar
información sobre el progreso de una tarea, el estado de un proceso, o cualquier otra información relevante para el
usuario.

> **Nota**: Las imágenes utilizadas en este ejemplo son solo un ejemplo y pueden ser reemplazadas por cualquier otra
> imagen que se ajuste a las necesidades de la aplicación.

> **Nota**: Para efectos de aclaración las constantes `UIConstants.BAR_ICON` y `UIConstants.BAR_DISPLAY` deben ser
> definidas en la clase `UIConstants` en el paquete `rpg.gui`.

## Actualización de la Interfaz `UIConstants`

```java
package rpg.gui;

import rpg.utils.cache.FontCache;

import javax.swing.border.EmptyBorder;
import java.awt.*;

public interface UIConstants {
    Font FONT = FontCache.addFont("PIXM", "fonts/M6X.ttf");
    Font BAR_LABEL_FONT = FontCache.addFont("PAE", "fonts/PixelAE.ttf").deriveFont(16f);
    Font LABEL_FONT = FontCache.addFont("Retron", "fonts/Retron2000.ttf").deriveFont(Font.BOLD,18f);
    int WINDOW_WIDTH = 1500;
    int TOP_HEIGHT = 150;
    int MIDDLE_HEIGHT = 320;
    int BOTTOM_HEIGHT = 350;
    int SIMPLE_MARGIN = 18;
    int CORNER_WIDTH = 52;
    int CORNER_HEIGHT = 77;
    int CENTER_WIDTH = 350 - 2 * CORNER_WIDTH;
    Dimension BAR_ICON = new Dimension(58, 58);
    Dimension BAR_DISPLAY = new Dimension(179, 58);
    Dimension TOP_DIMENSION = new Dimension(WINDOW_WIDTH, TOP_HEIGHT);
    Dimension MIDDLE_DIMENSION = new Dimension(WINDOW_WIDTH, MIDDLE_HEIGHT);
    Dimension BOTTOM_DIMENSION = new Dimension(WINDOW_WIDTH, BOTTOM_HEIGHT);
    Dimension CORNER_DIMENSION = new Dimension(52, 77);
    Dimension CENTER_DIMENSION = new Dimension(CENTER_WIDTH, 77);
    Dimension BAR_LABEL = new Dimension(172, 51);
    EmptyBorder EMPTY_BORDER = new EmptyBorder(14, SIMPLE_MARGIN,
            SIMPLE_MARGIN, SIMPLE_MARGIN);
}
```

> **Nota**: Toma en consideración que estos tamaños y dimensiones son solo un ejemplo y pueden ser ajustados según las
> necesidades de la aplicación.
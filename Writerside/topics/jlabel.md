# JLabel y BasicLabelUI

## JLabel

JLabel es una clase que extiende a JComponent y que se utiliza para mostrar texto, imágenes o ambos. Es un componente
que no es interactivo, es decir, no se puede seleccionar ni modificar. Se utiliza para mostrar información al usuario.

### Creación de un JLabel

Para efectos óptimos, podemos crear una clase que extienda de JLabel y que nos permita personalizar el JLabel a nuestro
gusto. A continuación se muestra un ejemplo de cómo crear un JLabel personalizado:

```java
public class MiJLabel extends JLabel {
    public MiJLabel(String texto) {
        super(texto);
        setFont(new Font("Arial", Font.BOLD, 14));
        setForeground(Color.BLUE);
    }
}
```

En este caso, hemos creado una clase llamada MiJLabel que extiende de JLabel y que recibe un texto como parámetro. Al
crear un objeto de tipo MiJLabel, el texto se mostrará en negrita y de color azul.

### BasicLabelUI

BasicLabelUI es una clase que extiende a LabelUI y que se encarga de pintar un JLabel. Se utiliza para personalizar la
apariencia de un JLabel. Por defecto, un JLabel utiliza la clase BasicLabelUI para pintarse. Pero nosotros podemos
crear una clase que extienda de BasicLabelUI y que nos permita personalizar la apariencia de un JLabel.

A continuación se muestra un ejemplo de cómo crear una clase que extienda de BasicLabelUI:

```java
public class MiLabelUI extends BasicLabelUI {
    public static ComponentUI createUI(JComponent c) {
        return new MiLabelUI();
    }

    @Override
    public void paint(Graphics g, JComponent c) {
        super.paint(g, c);
        g.setColor(Color.RED);
        g.drawRect(0, 0, c.getWidth() - 1, c.getHeight() - 1);
    }
}
```

En este caso, hemos creado una clase llamada MiLabelUI que extiende de BasicLabelUI. Sobreescribimos el método paint
para pintar un borde rojo alrededor del JLabel. Para utilizar esta clase, debemos establecerla como la clase UI del
JLabel:

```java
JLabel label = new JLabel("Hola, mundo");
label.setUI(new MiLabelUI());
```

Las funciones de la clase BasicLabelUI son las siguientes:

* `public static ComponentUI createUI(JComponent c)`: Crea una instancia de la clase MiLabelUI.
* `public void paint(Graphics g, JComponent c)`: Pinta el JLabel en el componente c.
* `protected String layoutCL(JLabel label, FontMetrics fontMetrics, String text, Icon icon, Rectangle viewR, 
   Rectangle iconR, Rectangle textR)`: Calcula el tamaño y la posición del texto y la imagen en el JLabel.
* `protected String layoutCompoundLabel(JLabel label, FontMetrics fontMetrics, String text, Icon icon, int 
   layoutX, int layoutY, int layoutWidth, int layoutHeight, Rectangle viewR, Rectangle iconR, Rectangle textR)`:
  Calcula el tamaño y la posición del texto y la imagen en el JLabel compuesto.
* `protected String layoutText(JLabel label, FontMetrics fontMetrics, String text, Icon icon, int layoutWidth, 
   int layoutHeight)`: Calcula el tamaño y la posición del texto en el JLabel.
* `protected String layoutIcon(JLabel label, Icon icon, Rectangle viewR, Rectangle iconR)`: Calcula el tamaño y la
  posición de la imagen en el JLabel.
* `protected void paintEnabledText(JLabel l, Graphics g, String s, int textX, int textY)`: Pinta el texto del JLabel
  cuando está habilitado.
* `protected void paintDisabledText(JLabel l, Graphics g, String s, int textX, int textY)`: Pinta el texto del JLabel
  cuando está deshabilitado.

## Usando JLabel y BasicLabelUI en conjunto

Podemos utilizar un JLabel personalizado junto con una BasicLabelUI personalizada para crear un JLabel con una
apariencia única. A continuación se muestra un ejemplo de cómo hacerlo:

```java
public class MiJLabel extends JLabel {
    public MiJLabel(String texto) {
        super(texto);
        setFont(new Font("Arial", Font.BOLD, 14));
        setForeground(Color.BLUE);
        setUI(new MiLabelUI());
    }
}

public class MiLabelUI extends BasicLabelUI {
    public static ComponentUI createUI(JComponent c) {
        return new MiLabelUI();
    }

    @Override
    public void paint(Graphics g, JComponent c) {
        super.paint(g, c);
        g.setColor(Color.RED);
        g.drawRect(0, 0, c.getWidth() - 1, c.getHeight() - 1);
    }
}
```

De esta forma, el JLabel se pintará con un borde rojo alrededor.

En resumen, JLabel es una clase que se utiliza para mostrar texto, imágenes o ambos. Podemos personalizar un JLabel
creando una clase que extienda de JLabel y sobreescribiendo sus métodos. También podemos personalizar la apariencia de
un JLabel creando una clase que extienda de BasicLabelUI y sobreescribiendo el método paint.
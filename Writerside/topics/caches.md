# 12. Las cachés

Las cachés son una forma de almacenar datos en la memoria para que puedan ser recuperados rápidamente. En Java, la clase
`java.util.HashMap` es una implementación de una caché que almacena pares clave-valor. En este tutorial, aprenderás cómo
usar la clase `HashMap` para crear una caché en Java.

## Creación de una caché de Imágenes

Supongamos que estás desarrollando un juego en Java y necesitas cargar imágenes desde el disco duro para mostrarlas en
la pantalla. En lugar de cargar la misma imagen varias veces, puedes almacenarla en una caché para que se pueda
recuperar rápidamente cuando sea necesario.

Aquí hay un ejemplo de cómo crear una caché de imágenes en Java utilizando la clase `HashMap`:

```java
package rpg.utils.cache;

import javax.swing.*;
import java.awt.image.BufferedImage;
import java.util.HashMap;
import java.util.Map;

public class ImageCache {

    private static final String IMAGE_PATH = "image/";
    private static final Map<String, BufferedImage> CACHE = new HashMap<>();

    public static BufferedImage addImage(String name, String path) {

        BufferedImage image;
        if (!CACHE.containsKey(name)) {

            image = ImageLoader.loadImage(IMAGE_PATH + path);
            CACHE.put(name, image);
        } else {
            image = CACHE.get(name);
        }
        return image;
    }

    public static BufferedImage getImage(String imageName) {

        return CACHE.getOrDefault(imageName, null);
    }

    public static ImageIcon getImageIcon(String imageName) {

        return new ImageIcon(getImage(imageName));
    }
}
```

> Usamos BufferedImage en lugar de Image para poder manipular la imagen de forma más eficiente.

Es este ejemplo podemos notar las siguientes funciones:

- `addImage(String name, String path)`: Agrega una imagen a la caché con un nombre y una ruta de archivo.
- `getImage(String imageName)`: Obtiene una imagen de la caché por su nombre.
- `getImageIcon(String imageName)`: Obtiene un `ImageIcon` de la caché por su nombre.
- `cache`: Un `HashMap` que almacena las imágenes en la caché.
- `ImageLoader.loadImage(String path)`: Una función auxiliar que carga una imagen desde el disco duro.

### La clase ImageLoader

La clase `ImageLoader` es una clase auxiliar que se encarga de cargar imágenes desde el disco duro. Aquí tienes un
ejemplo de cómo implementar la clase `ImageLoader`:

```java
package rpg.utils.cache;

import javax.imageio.ImageIO;
import javax.swing.*;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;

public class ImageLoader {

    public static BufferedImage loadImage(String path) {

        try {

            return ImageIO.read(new File(path));
        } catch (IOException e) {
            JOptionPane.showConfirmDialog(null, "Error al cargar la imagen: " + path,
                    "Error", JOptionPane.DEFAULT_OPTION, JOptionPane.ERROR_MESSAGE);
        }
        return null;
    }
}
```

## La caché de Fuentes

Además de las imágenes, también puedes crear una caché de fuentes en Java para almacenar las fuentes que se utilizan
frecuentemente en tu aplicación. Aquí tienes un ejemplo de cómo crear una caché de fuentes en Java:

### El FontLoader

La clase `FontLoader` es una clase auxiliar que se encarga de cargar fuentes desde el disco duro. Aquí tienes un
ejemplo de cómo implementar la clase `FontLoader`:

```java
package rpg.utils.cache;

import javax.swing.*;
import java.awt.*;
import java.io.File;

public class FontLoader {

    public static Font loadFont(String path) {

        try {

            return Font.createFont(Font.TRUETYPE_FONT, new File(path)).deriveFont(12f);
        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, "Error al cargar la fuente: " + path,
                    "Error", JOptionPane.ERROR_MESSAGE);
        }
        return Font.getFont("Arial").deriveFont(12f);
    }
}
```

> Usamos `Font.TRUETYPE_FONT` para cargar fuentes TrueType. Puedes cambiarlo a `Font.TYPE1_FONT` si necesitas cargar
> fuentes Type1. Además, usamos `deriveFont(12f)` para establecer el tamaño de la fuente en 12 puntos.

### La clase FontCache

La clase `FontCache` es una clase que almacena las fuentes en una caché para que puedan ser recuperadas rápidamente.
Aquí tienes un ejemplo de cómo implementar la clase `FontCache`:

```java
package unitec.rpg.ui.cache;

import java.awt.*;
import java.util.HashMap;
import java.util.Map;

public class FontCache {

    public static final Map<String, Font> cache = new HashMap<>();

    public static Font addFont(String fontName, String fontPath) {

        Font font;
        if (!cache.containsKey(fontName)) {

            font = FontLoader.loadFont(fontPath);
            cache.put(fontName, font);
        } else {
            font = cache.get(fontName);
        }
        return font;
    }

    public static Font getFont(String fontName, int style, int size) {

        return cache.getOrDefault(fontName, Font.getFont("Arial")).deriveFont(style, size);
    }

    public static Font getFont(String fontName) {

        return getFont(fontName, Font.PLAIN, 12);
    }

    public static Font getFont(String fontName, int size) {

        return getFont(fontName, Font.PLAIN, size);
    }
}
```
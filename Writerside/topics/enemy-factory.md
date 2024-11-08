# 22. La fábrica de enemigos

Una vez que hemos actualizado nuestras clases en combate (`Player` y `Enemy`), es momento de crear una fábrica de
enemigos que nos permita crear enemigos de forma dinámica. La fábrica de enemigos será una clase que se encargará de
creár enemigos de diferentes tipos y niveles, y nos permitirá obtener un enemigo aleatorio para que el jugador pueda
enfrentarse a él.

## Incluyendo la librería Reflections

Para poder crear una fábrica de enemigos que nos permita crear enemigos de diferentes tipos y niveles, necesitamos
incluir la librería Reflections en nuestro proyecto. Reflections es una librería de Java que nos permite analizar y
manipular clases en tiempo de ejecución, lo que nos permitirá crear enemigos de forma dinámica.

Para agregar esta dependencia, deberemos de modificar nuestro proyecto desde IntelliJ IDEA. Para ello, seguiremos los
siguientes pasos:

1. Daremos clic derecho sobre el nombre de nuestro proyecto en el panel izquierdo.
2. Seleccionaremos la opción `Open Module Settings`.
   ![maven1.png](..%2Fimages%2Fmaven1.png){display:block}
3. En la ventana que se abre, seleccionaremos la pestaña `Libraries`.
   ![maven2.png](..%2Fimages%2Fmaven2.png){display:block}
4. Daremos clic en el botón `+` y seleccionaremos la opción `From Maven...`.
5. En la ventana que se abre, buscaremos la librería `org.reflections` y daremos clic en el botón de la lupa y
   seleccionaremos la versión `0.9.12`
   ![maven3.png](..%2Fimages%2Fmaven3.png){display:block}
6. Seleccionamos la opción `Download to` por defecto es proceso creará la carpeta `lib` en nuestro proyecto y
   descargará la librería Reflections.
   ![maven4.png](..%2Fimages%2Fmaven4.png){display:block}
7. Por último, daremos clic en el botón `OK` y luego en `Apply` y `OK` para cerrar la ventana de configuración.

Con estos pasos, hemos agregado la librería Reflections a nuestro proyecto y podremos utilizarla para crear la fábrica
de enemigos.

## Creando la fábrica de enemigos

Para crear la fábrica de enemigos, crearemos una clase llamada `EnemyFactory` en el paquete `rpg.factory`. Esta clase
será la encargada de creár enemigos de diferentes tipos y niveles, y nos permitirá obtener un enemigo aleatorio para
que el jugador pueda enfrentarse a él.

```java
package rpg.factory;

import org.reflections.Reflections;
import org.reflections.scanners.FieldAnnotationsScanner;
import org.reflections.scanners.SubTypesScanner;
import org.reflections.util.ClasspathHelper;
import org.reflections.util.ConfigurationBuilder;
import rpg.entities.enemies.Enemy;
import rpg.enums.EnemyType;

import java.util.ArrayList;
import java.util.List;
import java.util.Random;
import java.util.Set;

public class EnemyFactory {

    private static final Random random = new Random();

    public static Enemy getEnemy() {

        Enemy enemyInstance;
        Set<Class<? extends Enemy>> enemyClasses;
        List<Class<? extends Enemy>> classList;
        // Configura Reflections para buscar clases en el classpath
        Reflections reflections = new Reflections(new ConfigurationBuilder()
                .setUrls(ClasspathHelper.forJavaClassPath())
                .setScanners(new SubTypesScanner(), new FieldAnnotationsScanner()));
        // Obtiene todas las clases que extienden de Enemy
        enemyClasses = reflections.getSubTypesOf(Enemy.class);
        // Filtra las clases para obtener solo las de tipo básico
        classList = filterList(enemyClasses.stream().toList(), EnemyType.BASIC);
        try {
            int randomIndex;
            if (classList != null) {

                randomIndex = random.nextInt(classList.size());
                enemyInstance = classList.get(randomIndex).getDeclaredConstructor()
                        .newInstance();
            }else {
                throw new Exception();
            }
        } catch (Exception e) {
            return null;
        }
        return enemyInstance;
    }

    private static List<Class<? extends Enemy>> filterList(List<Class<? extends Enemy>> classList, EnemyType enemyType) {

        Enemy enemy;
        List<Class<? extends Enemy>> classListFiltered = new ArrayList<>();
        for (Class<? extends Enemy> enemyClass : classList) {

            try {
                enemy = enemyClass.getDeclaredConstructor().newInstance();
                if (enemy.getType() == enemyType) {
                    classListFiltered.add(enemyClass);
                }
            } catch (Exception e) {
                return null;
            }
        }
        return classListFiltered;
    }
}
```

Esta clase contiene un método estático `getEnemy` que se encarga de obtener un enemigo aleatorio de tipo básico. Para
ello, utiliza la librería Reflections para buscar todas las clases que extienden de `Enemy` y filtra la lista para
obtener solo las clases de tipo básico. Luego, selecciona un índice aleatorio de la lista y crea una instancia del
enemigo correspondiente.

Con esta clase, hemos creado una fábrica de enemigos que nos permitirá crear enemigos de forma dinámica y obtener un
enemigo aleatorio para que el jugador pueda enfrentarse a él.

> **Nota:** La librería Reflections nos permite analizar y manipular clases en tiempo de ejecución, lo que nos permite
> crear enemigos de forma dinámica. En este caso, hemos utilizado Reflections para buscar todas las clases que
> extienden de `Enemy` y filtrar la lista para obtener solo las clases de tipo básico.

> **Nota:** Puedes y debes crear más métodos en la clase `EnemyFactory` para obtener enemigos de diferentes tipos y
> niveles, según las necesidades de tu juego.

## Conclusión

En esta sección, hemos creado una fábrica de enemigos que nos permitirá crear enemigos de forma dinámica y obtener un
enemigo aleatorio para que el jugador pueda enfrentarse a él. La fábrica de enemigos es una clase que se encarga de
creár enemigos de diferentes tipos y niveles, y nos permitirá obtener un enemigo aleatorio para que el jugador pueda
enfrentarse a él. Con esta clase, hemos completado la actualización de nuestras clases en combate y estamos listos para
seguir implementando nuevas funcionalidades en nuestro juego.
# 2.- Creando los paquetes

Para nuestro proyecto, vamos a crear los siguientes paquetes:

- `rpg`: Contendrá las clases principales del juego de RPG.
- `rpg.entities`: Contendrá las clases relacionadas con los personajes del juego.
- `rpg.enums`: Contendrá las enumeraciones utilizadas en el juego.

Para crear un paquete en IntelliJ, se deben seguir los siguientes pasos:

1. Abrir IntelliJ.
2. Hacer clic en `File` en la barra de menú.
3. Seleccionar `New` y luego `Package`.
   ![new-package.png](new_package.png){style="block"}
4. En el cuadro de diálogo `Create New Package`, ingresar el nombre del paquete.
    - Por ejemplo, para crear el paquete `rpg`, se debe ingresar `rpg`.
    - Para crear un paquete dentro de otro paquete, se debe utilizar la notación de puntos. Por ejemplo, para crear el
      paquete `rpg.entities`, se debe ingresar `rpg.entities`.
      ![create-package.png](create-package.png){style="block"}
    - Presionar `Enter` para crear el paquete.
5. Una vez creado el paquete, se verá el paquete en la estructura del proyecto.

Repite estos pasos para crear los paquetes `rpg.entities` y `rpg.enums`.

Al finalizar estos pasos, tendrás los paquetes necesarios para organizar el código del juego de RPG en Java. Estos
paquetes te ayudarán a mantener una estructura clara y organizada en tu proyecto, facilitando el desarrollo y la
mantenibilidad del código.

En el siguiente capítulo, veremos cómo crear las clases dentro de estos paquetes y cómo utilizarlos en el juego de RPG.
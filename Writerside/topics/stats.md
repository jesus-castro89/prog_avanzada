# 3.- Creando las clases y enumeraciones

Para nuestro proyecto, vamos a crear las siguientes clases y enumeraciones:

- `Enemy`: Representará a los enemigos del juego.
- `Player`: Representará al jugador del juego.

Además, vamos a crear las siguientes enumeraciones:

- `Stats`: Enumeración que contendrá los atributos de los personajes.

Para crear una clase en IntelliJ, se deben seguir los siguientes pasos:

1. Abrir IntelliJ.
2. Hacer clic en `File` en la barra de menú.
3. Seleccionar `New` y luego `Java Class`.
4. En el cuadro de diálogo `Create New Class`, ingresar el nombre de la clase.
    - Por ejemplo, para crear la clase `Enemy`, se debe ingresar `Enemy`.
    - Para crear una clase dentro de un paquete, se debe seleccionar el paquete en el cuadro de diálogo.
    - Presionar `Enter` para crear la clase.
5. Una vez creada la clase, se verá la clase en la estructura del proyecto.
6. Repite estos pasos para crear las clases `Player` y `Stats`.
7. Para crear una enumeración, se deben seguir los mismos pasos, pero seleccionando `Java Enum` en el cuadro de
   diálogo `Create New Class`.

Al finalizar estos pasos, tendrás las clases y enumeraciones necesarias para representar a los personajes y enemigos del
juego de RPG en Java. Estas clases y enumeraciones te permitirán modelar las interacciones y características de los
personajes en el juego.

## 3.1.- Implementando las clases

En esta sección, vamos a implementar las clases `Enemy`, `Player` y `Stats` con sus respectivos atributos y métodos.
Cada clase tendrá una funcionalidad específica en el juego y nos permitirá interactuar con los personajes y enemigos.

Para implementar una clase en Java, se deben seguir los siguientes pasos:

1. Definir los atributos de la clase.
2. Crear el constructor de la clase.
3. Implementar los métodos necesarios para interactuar con los atributos de la clase.
4. Probar la clase para verificar su funcionamiento.
5. Repetir estos pasos para cada clase.

Al finalizar esta sección, tendrás las clases `Enemy`, `Player` y `Stats` implementadas con sus respectivos atributos y
métodos. Estas clases te permitirán representar a los personajes y enemigos del juego de RPG en Java y modelar sus
características y habilidades.

Para la implementación de nuestras clases y tipos enumerados, nos basaremos del siguiente diagrama de clases:

![class-diagram](class-diagram.png){style="block"}

En el diagrama de clases, se puede observar la relación entre las clases `Enemy`, `Player` y `Stats`, así como los
atributos y métodos de cada clase. Este diagrama nos servirá como guía para la implementación de las clases y
enumeraciones en el proyecto de RPG en Java.

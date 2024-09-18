# 5.- La interacción entre el jugador y los enemigos

En esta sección, vamos a implementar la interacción entre el jugador y los enemigos en el juego de RPG. Para ello,
utilizaremos las clases `Player` y `Enemy` que hemos creado previamente, así como las enumeraciones `Stats`
y `CombatAction` que representan los atributos y acciones de los personajes en el juego.

## 5.1.- Implementando la interacción

Para implementar la interacción entre el jugador y los enemigos, vamos a seguir los siguientes pasos:

1. Crea la clase `Game` que gestionará la lógica del juego.
2. Implementa el método `startGame()` en la clase `Game` para iniciar el juego.
3. En el método constructor de la clase `Game`, crea una instancia del jugador y un enemigo.
4. Implementa la lógica de combate en el método `startGame()` para simular la interacción entre el jugador y los
   enemigos.
5. Muestra el resultado del combate al finalizar la interacción.
6. Repite el combate hasta que el jugador o los enemigos sean derrotados.
7. Al finalizar el combate, muestra un mensaje de victoria o derrota según el resultado.
8. Implementa la lógica de turno para alternar entre el jugador y los enemigos en el combate.
9. Actualiza los atributos de los personajes según las acciones realizadas en el combate.
10. Implementa la lógica de victoria o derrota según el estado de los personajes al finalizar el combate.
11. Refactoriza el código para mejorar la legibilidad y mantenibilidad.

Al seguir estos pasos, podrás implementar la interacción entre el jugador y los enemigos en el juego de RPG. Esta
interacción permitirá simular combates entre el jugador y los enemigos, así como gestionar el estado de los personajes
durante el juego.

## 5.2.- Ejemplo de interacción

A continuación, se muestra un ejemplo de cómo podría ser la interacción entre el jugador y los enemigos en el juego de
RPG:

```java
public class Game {
    private Player player;
    private Enemy enemy;

    public Game() {
        this.player = new Player("Hero");
        this.enemy = new Enemy("Goblin");
    }

    public void startGame() {
        while (player.isAlive() && enemy.isAlive()) {
            player.attack(enemy);
            if (enemy.isAlive()) {
                enemy.attack(player);
            }
        }

        if (player.isAlive()) {
            System.out.println("You defeated the enemy!");
        } else {
            System.out.println("Game over. You were defeated by the enemy.");
        }
    }
}
```   
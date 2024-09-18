# 4.- Creando al jugador y al enemigo

Para nuestro proyecto, vamos a crear las clases `Player` y `Enemy`, que representarán al jugador y al enemigo del juego
de RPG.

## 4.1.- Creando la clase `Player`

Comenzaremos creando la clase `Player`, que representará al jugador del juego. Esta clase contendrá los atributos y
métodos necesarios para modelar al personaje principal del juego.

Para hacer esto deberás crear la clase en el paquete `rpg.entities` y agregar los siguientes atributos y métodos:

### Atributos de la clase `Player`

- `name`: Nombre del jugador.
- `stats`: Atributos del jugador (vida, ataque, defensa, etc.).

### Métodos de la clase `Player`

- `getName()`: Método para obtener el nombre del jugador.
- `getStats()`: Método para obtener los atributos del jugador.
- `constructor`: Constructor de la clase `Player` que inicializa el nombre y los atributos del jugador.
- `isAlive()`: Método que verifica si el jugador está vivo.
- `attack(Enemy enemy)`: Método que permite al jugador atacar a un enemigo.

Al finalizar la implementación de la clase `Player`, tendrás un personaje principal con sus atributos y métodos
necesarios para interactuar con el juego.

### El constructor de la clase `Player`

El constructor de la clase `Player` se encarga de inicializar el nombre y los atributos del jugador. Aquí un ejemplo de
cómo se podría implementar:

```java
public Player(String name) {
        this.name = name;
        this.stats = new HashMap<>();
        this.stats.put(Stats.MAX_HP, 100);
        this.stats.put(Stats.HP, 100);
        this.stats.put(Stats.MAX_MP, 50);
        this.stats.put(Stats.MP, 50);
        this.stats.put(Stats.ATTACK, 10);
        this.stats.put(Stats.DEFENSE, 5);
    }
```

En este ejemplo, se inicializan los atributos del jugador con valores predeterminados. Puedes ajustar estos valores
según las necesidades de tu juego.

### Implementando el método `attack(Enemy enemy)`

El método `attack(Enemy enemy)` permite al jugador atacar a un enemigo. Aquí un ejemplo de cómo se podría implementar:

```java
public void attack(Enemy enemy) {
        int damage = this.stats.get(Stats.ATTACK) - enemy.getStats().get(Stats.DEFENSE);
        if (damage > 0) {
            enemy.getStats().put(Stats.HP, enemy.getStats().get(Stats.HP) - damage);
            System.out.println(this.name + " attacks " + enemy.getName() + " for " + damage + " damage!");
        } else {
            System.out.println(this.name + " attacks " + enemy.getName() + " but does no damage!");
        }
}
```

## 4.2.- Creando la clase `Enemy`

Ahora, vamos a crear la clase `Enemy`, que representará a los enemigos del juego. Esta clase contendrá los atributos y
métodos necesarios para modelar a los enemigos con los que el jugador se enfrentará.

Para hacer esto deberás crear la clase en el paquete `rpg.entities` y agregar los siguientes atributos y métodos:

### Atributos de la clase `Enemy`

- `name`: Nombre del enemigo.
- `stats`: Atributos del enemigo (vida, ataque, defensa, etc.).

### Métodos de la clase `Enemy`

- `getName()`: Método para obtener el nombre del enemigo.
- `getStats()`: Método para obtener los atributos del enemigo.
- `constructor`: Constructor de la clase `Enemy` que inicializa el nombre y los atributos del enemigo.
- `isAlive()`: Método que verifica si el enemigo está vivo.
- `attack(Player player)`: Método que permite al enemigo atacar al jugador.

Al finalizar la implementación de la clase `Enemy`, tendrás un enemigo con sus atributos y métodos necesarios para
interactuar con el juego.

### El constructor de la clase `Enemy`

El constructor de la clase `Enemy` se encarga de inicializar el nombre y los atributos del enemigo. Aquí un ejemplo de
cómo se podría implementar:

```java
public Enemy(String name) {
        this.name = name;
        this.stats = new HashMap<>();
        this.stats.put(Stats.MAX_HP, 50);
        this.stats.put(Stats.HP, 50);
        this.stats.put(Stats.ATTACK, 5);
        this.stats.put(Stats.DEFENSE, 2);
    }
```

### Implementando el método `attack(Player player)`

El método `attack(Player player)` permite al enemigo atacar al jugador. Aquí un ejemplo de cómo se podría implementar:

```java
public void attack(Player player) {
        int damage = this.stats.get(Stats.ATTACK) - player.getStats().get(Stats.DEFENSE);
        if (damage > 0) {
            player.getStats().put(Stats.HP, player.getStats().get(Stats.HP) - damage);
            System.out.println(this.name + " attacks " + player.getName() + " for " + damage + " damage!");
        } else {
            System.out.println(this.name + " attacks " + player.getName() + " but does no damage!");
        }
}
```
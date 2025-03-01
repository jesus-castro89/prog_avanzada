# Proyecto: Diseño de un Juego `BrickBreak` en Java

## Definición

El juego `BrickBreak` es un juego de arcade en el que el jugador controla una paleta que rebota una pelota hacia arriba
para romper ladrillos. El objetivo del juego es romper todos los ladrillos en la parte superior de la pantalla sin que
la pelota caiga al suelo. El jugador gana puntos por cada ladrillo que rompe y pierde una vida si la pelota cae al
suelo. El juego termina cuando el jugador ha roto todos los ladrillos o ha perdido todas sus vidas.

El juego consta de los siguientes elementos:

- **Paleta**: El jugador controla una paleta que se mueve de izquierda a derecha en la parte inferior de la pantalla.
  La paleta rebota la pelota hacia arriba cuando la pelota la golpea.
- **Pelota**: La pelota rebota en la pantalla y rompe los ladrillos cuando los golpea. La pelota rebota en la paleta
  cuando la golpea y cae al suelo si no rebota en la paleta.
- **Ladrillos**: Los ladrillos están dispuestos en la parte superior de la pantalla y el jugador debe romperlos con la
  pelota para ganar puntos. Cada ladrillo tiene un valor de puntos asociado y se rompe cuando la pelota lo golpea.
- **Vidas**: El jugador tiene un número limitado de vidas y pierde una vida cada vez que la pelota cae al suelo. El
  jugador pierde el juego si se queda sin vidas.
- **Puntuación**: El jugador gana puntos por cada ladrillo que rompe y la puntuación se muestra en la pantalla. El
  jugador puede ganar puntos adicionales al romper varios ladrillos seguidos sin que la pelota caiga al suelo.
- **Niveles**: El juego tiene varios niveles con diferentes disposiciones de ladrillos y dificultades. El jugador
  avanza al siguiente nivel cuando ha roto todos los ladrillos en el nivel actual.
- **Power-ups**: Los power-ups son objetos especiales que aparecen en la pantalla y otorgan al jugador habilidades
  especiales temporales, como una paleta más grande, una pelota extra o una pelota que atraviesa los ladrillos.
- **Sonido**: El juego tiene efectos de sonido para la pelota, la paleta, los ladrillos y los power-ups para mejorar la
  experiencia del jugador.
- **Pantalla de inicio**: El juego tiene una pantalla de inicio con opciones para comenzar un nuevo juego, cargar un
  juego guardado, ver las puntuaciones más altas y salir del juego.
- **Pantalla de juego**: La pantalla de juego muestra la paleta, la pelota, los ladrillos, las vidas, la puntuación y
  los power-ups en la pantalla. El jugador controla la paleta con el teclado y rebota la pelota para romper los
  ladrillos.
- **Pantalla de fin de juego**: La pantalla de fin de juego muestra la puntuación final del jugador y opciones para
  volver a jugar, guardar la puntuación y salir del juego.
- **Guardado de juego**: El juego permite al jugador guardar su progreso y cargar un juego guardado en cualquier
  momento. El jugador puede guardar su puntuación más alta y cargarla en futuras partidas.
- **Puntuaciones más altas**: El juego guarda las puntuaciones más altas de los jugadores y las muestra en la pantalla
  de inicio. El jugador puede intentar superar las puntuaciones más altas de otros jugadores.
- **Controles**: El jugador controla la paleta con las teclas de flecha izquierda y derecha y lanza la pelota con la
  tecla de espacio. El jugador puede pausar el juego con la tecla de pausa y salir del juego con la tecla de escape.
- **Dificultad**: El juego tiene varios niveles de dificultad que afectan la velocidad de la pelota, la cantidad de
  ladrillos y la aparición de power-ups. El jugador puede elegir el nivel de dificultad al comenzar un nuevo juego.
- **Gráficos**: El juego tiene gráficos simples, pero efectivos que muestran la paleta, la pelota, los ladrillos, los
  power-ups y las pantallas de inicio, juego y fin de juego.

El juego `BrickBreak` es un juego clásico de arcade que desafía la habilidad y la destreza del jugador para romper
ladrillos y ganar puntos. El juego es fácil de aprender pero difícil de dominar, lo que lo convierte en un juego
divertido y adictivo para jugadores de todas las edades. El diseño de un juego `BrickBreak` en Java es un proyecto
divertido y educativo que enseña a los estudiantes a programar en Java y a desarrollar juegos de arcade simples pero
divertidos.
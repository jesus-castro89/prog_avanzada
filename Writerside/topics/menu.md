# Menus interactivos con JOptionPane

En Java, la clase `JOptionPane` proporciona métodos estáticos para mostrar ventanas de diálogo interactivas, como
ventanas de mensaje, confirmación, entrada de datos y selección. Estas ventanas de diálogo son útiles para interactuar
con el usuario y obtener información o confirmación de acciones.

## Definiendo las opciones de un menú

Para crear un menú interactivo con `JOptionPane`, primero necesitamos definir las opciones que se mostrarán al usuario.

```java
String[] options = { "Option 1", "Option 2", "Option 3" };
``

## Mostrando un menú de selección

Para mostrar un menú de selección con `JOptionPane`, usamos el método `showOptionDialog()` y pasamos los 
siguientes parámetros: 

- `null`: El componente padre de la ventana de diálogo.
- "Select an option": El mensaje que se mostrará en la ventana de diálogo.
- "Menu": El título de la ventana de diálogo.
- `JOptionPane.DEFAULT_OPTION`: El tipo de icono que se mostrará en la ventana de diálogo.
- `JOptionPane.QUESTION_MESSAGE`: El tipo de mensaje que se mostrará en la ventana de diálogo.
- `null`: El icono personalizado que se mostrará en la ventana de diálogo.
- `options`: Las opciones que se mostrarán al usuario.
- `options[0]`: La opción predeterminada seleccionada por el usuario.

```java
int choice = JOptionPane.showOptionDialog(null, "Select an option", "Menu",
    JOptionPane.DEFAULT_OPTION, JOptionPane.QUESTION_MESSAGE, null, options, options[0]);
```

## Procesando la selección del usuario

Después de mostrar el menú de selección, podemos procesar la selección del usuario utilizando el valor devuelto por
`showOptionDialog()`.

```java
if (choice == 0) {
    System.out.println("Option 1 selected");
} else if (choice == 1) {
    System.out.println("Option 2 selected");
} else if (choice == 2) {
    System.out.println("Option 3 selected");
}
```




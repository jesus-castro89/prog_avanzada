# Entrada de datos con showInputDialog

En Java, la clase JOptionPane proporciona métodos para mostrar ventanas de diálogo que permiten al usuario interactuar
con la aplicación. Uno de los métodos más utilizados es `showInputDialog`, que permite al usuario introducir datos a
través de una ventana emergente.

## Sintaxis de la función showInputDialog con 1 parámetro

La sintaxis de la función `showInputDialog` con 1 parámetro es la siguiente:

```java
String input = JOptionPane.showInputDialog(Object message);
```

Donde:

- `message`: Es el mensaje que se mostrará en la ventana emergente para solicitar la entrada de datos. Puede ser de tipo
  `String`, `Icon`, `Component` o `Object`.

> **Nota**: El valor introducido por el usuario se devuelve como una cadena de texto (`String`).

Si se desea convertir la entrada de datos a un tipo de dato específico, se puede utilizar la conversión de tipos
correspondiente. Por ejemplo, para convertir la entrada de datos a un número entero, se puede utilizar el método
`Integer.parseInt`.

```java
int numero = Integer.parseInt(
                    JOptionPane.showInputDialog("Ingrese un número:"));
double decimal = Double.parseDouble(
                    JOptionPane.showInputDialog("Ingrese un número decimal:"));
float flotante = Float.parseFloat(
                    JOptionPane.showInputDialog("Ingrese un número flotante:"));
```

### Ejemplo con 1 parámetro

```java
String nombre = JOptionPane.showInputDialog("Ingrese su nombre:");
```

En este ejemplo, se muestra una ventana emergente con el mensaje "Ingrese su nombre:" y se guarda la entrada de datos en
la variable `nombre`.

## Sintaxis de la función showInputDialog con 2 parámetros

La sintaxis de la función `showInputDialog` con 2 parámetros es la siguiente:

```java
String input = JOptionPane.showInputDialog(Component parentComponent, Object message);
```

Donde:

- `parentComponent`: Es el componente padre de la ventana emergente. Puede ser `null` si no se desea especificar un
  componente padre.
- `message`: Es el mensaje que se mostrará en la ventana emergente para solicitar la entrada de datos. Puede ser de tipo
  `String`, `Icon`, `Component` o `Object`.

### Ejemplo con 2 parámetros

```java
String nombre = JOptionPane.showInputDialog(null, "Ingrese su nombre:");
```

En este ejemplo, se muestra una ventana emergente con el mensaje "Ingrese su nombre:" y se guarda la entrada de datos en
la variable `nombre`. El componente padre se especifica como `null`.

### Sintaxis de la función showInputDialog con 4 parámetros

La sintaxis de la función `showInputDialog` con 4 parámetros es la siguiente:

```java
String input = JOptionPane.showInputDialog(Component parentComponent, Object message, String title, int messageType);
```

Función exactamente igual que el `showMessagedialog`, pero en este caso se espera una entrada de datos.

Donde:

- `parentComponent`: Es el componente padre de la ventana emergente. Puede ser `null` si no se desea especificar un
  componente padre.
- `message`: Es el mensaje que se mostrará en la ventana emergente para solicitar la entrada de datos. Puede ser de tipo
  `String`, `Icon`, `Component` o `Object`.
- `title`: Es el título de la ventana emergente.
- `messageType`: Es el tipo de mensaje que se mostrará en la ventana emergente.

### Ejemplo con 4 parámetros

```java
String nombre = JOptionPane.showInputDialog(null, "Ingrese su nombre:", "Entrada de datos", JOptionPane.QUESTION_MESSAGE);
```

En este ejemplo, se muestra una ventana emergente con el mensaje "Ingrese su nombre:", el título "Entrada de datos" y el
tipo de mensaje `QUESTION_MESSAGE`. La entrada de datos se guarda en la variable `nombre`.

## Sintaxis de la función showInputDialog con 7 parámetros

La sintaxis de la función `showInputDialog` con 7 parámetros es la siguiente:

```java
String input = JOptionPane.showInputDialog(Component parentComponent, Object message, String title, int messageType, Icon icon, Object[] selectionValues, Object initialSelectionValue);
```

Donde:

- `parentComponent`: Es el componente padre de la ventana emergente. Puede ser `null` si no se desea especificar un
  componente padre.
- `message`: Es el mensaje que se mostrará en la ventana emergente para solicitar la entrada de datos. Puede ser de tipo
  `String`, `Icon`, `Component` o `Object`.
- `title`: Es el título de la ventana emergente.
- `messageType`: Es el tipo de mensaje que se mostrará en la ventana emergente.
- `icon`: Es el icono que se mostrará en la ventana emergente. Puede ser de tipo `Icon`.
- `selectionValues`: Es un arreglo de objetos que representa los valores de selección disponibles.
- `initialSelectionValue`: Es el valor inicial de selección.

### Ejemplo con 7 parámetros

```java
String opcion = (String) JOptionPane.showInputDialog(null, 
                                    "Seleccione una opción:", 
                                    "Selección", 
                                    JOptionPane.QUESTION_MESSAGE, 
                                    null, 
                                    new String[]{"Opción 1", "Opción 2", "Opción 3"}, 
                                    "Opción 1");
```

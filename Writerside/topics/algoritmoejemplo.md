# Ejemplo

```java
import javax.swing.*;
import java.awt.*;

public class Algorithm {

    public static void main(String[] args) {
        Algorithm myExample = new Algorithm();
        //algorithm.isMarried();
        myExample.factorial();
        myExample.combinations();
    }

    public Algorithm() {
        setLookAndFeel();
    }

    private void setLookAndFeel() {
        Font font = new Font("El Rio Lobo", Font.PLAIN, 36);
        // Establecemos el tipo de fuente para los mensajes y botones de las ventanas emergentes.
        UIManager.put("OptionPane.messageFont", font);
        UIManager.put("OptionPane.buttonFont", font);
        UIManager.put("TextField.font", font);
        // Establecemos el color de la fuente para los mensajes y botones de las ventanas emergentes.
        UIManager.put("OptionPane.messageForeground", Color.BLUE);
        UIManager.put("OptionPane.yesButtonText", "Sí");
    }

    public void isMarried() {
        // Leemos un valor booleano.
        boolean isMarried = JOptionPane.showConfirmDialog(null,
                "¿Estás casado?",
                "Estado Civil", JOptionPane.YES_NO_OPTION) == JOptionPane.YES_OPTION;
        // Formateamos el mensaje que se mostrará en la ventana emergente.
        String message = isMarried ? "Sí, estoy casado" : "No, no estoy casado";
        // Esta función muestra un mensaje en una ventana emergente.
        JOptionPane.showMessageDialog(null, message);
    }

    public void factorial() {
        // Leemos un número entero.
        int value = Integer.parseInt(
                JOptionPane.showInputDialog("Introduce un número Para calcular su factorial"));
        // Invocamos la función factorial y guardamos el resultado.
        factorial(value);
    }

    public void combinations() {
        // Leemos los valores de n y r.
        JOptionPane.showMessageDialog(null, "Vamos a calcular C(n, r)");
        // Nota: Recuerda que n debe ser mayor o igual a r.
        int n = Integer.parseInt(JOptionPane.showInputDialog("Introduce el valor de n"));
        int r = Integer.parseInt(JOptionPane.showInputDialog("Introduce el valor de r"));
        // Calculamos el resultado de C(n, r).
        int result = factorial(n) / (factorial(r) * factorial(n - r));
        // Aquí formateamos el mensaje que se mostrará en la ventana emergente.
        String message = String.format("El resultado de C(%d, %d) es %d", n, r, result);
        // Esta función muestra un mensaje en una ventana emergente.
        JOptionPane.showMessageDialog(null, message);
    }

    private int factorial(int value) {
        // Inicializamos la variable factorial a 1.
        int factorial = 1;
        // Iteramos desde 1 hasta el valor ingresado.
        int i = 1;
        for (; i <= value; i++) {
            // Multiplicamos el valor actual de factorial por i.
            factorial *= i;
        }
        // Formateamos el mensaje que se mostrará en la ventana emergente.
        String message = String.format("El factorial de %d es %d", value, factorial);
        // Esta función muestra un mensaje en una ventana emergente.
        JOptionPane.showMessageDialog(null, message);
        return factorial;
    }
}
```
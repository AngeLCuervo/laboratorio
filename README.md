1.creamos el proyecto en springboot y creamos el proyevto
![image](https://github.com/user-attachments/assets/2b10380c-0dda-451a-b6b7-22108b48760c)

2. ya descargada inicializamos con github y revisamos que todo este correctamente
![image](https://github.com/user-attachments/assets/991da634-ea2f-4bcb-a0f6-d6fd6280d896)

![image](https://github.com/user-attachments/assets/e9e6b227-d87d-4f18-9b93-6d47edfc6806)

4. compilamos el proyecto y que todo funcione
   - mvn package (terminal)
   - mvn compile
  
5. Las clases
   1. producto

       public Producto(String name, int cantidad, int precio, String categoria){
        this.name = name;
        this.cantidad = cantidad;
        this.categoria = categoria;
        this.precio = precio;
    }

    /**
     * Nos da el nombre del producto buscado
     * @return name del producto
     */
    public String getName(){return name;}

    public int getCantidad(){return cantidad; }

    public String getCategoria(){return categoria;}

    public int getPrecio(){return precio; }

    public void aumentarCantidad(){
        }

    public String modificarProducto(Producto producto){
        Producto productos = new Producto(name, cantidad, precio, categoria);
        if (producto.getCantidad() == 0){
            return null;
        }
        return null;
    }
}


   3. alerta
package eci.edu.cvds.parcialCVDS2025.Agente;

public class Alerta{
    private String mensaje;

    public Alerta(String mensaje) {
        this.mensaje = mensaje;
    }

    public String getMensaje() {
        return mensaje;
    }

    public String productoAgotado(Producto producto) {
        if (producto.getCantidad() < 5) {
            mensaje = "ALERTA!!! El stock del Producto " + "" + producto.getName() + "" + "es muy bajo, solo quedan" + "" + producto.getCantidad();
            return mensaje;
        }
        return mensaje;
    }
]

4. package eci.edu.cvds.parcialCVDS2025;

import eci.edu.cvds.parcialCVDS2025.Agente.Alerta;
import eci.edu.cvds.parcialCVDS2025.Agente.Producto;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import java.util.*;


@SpringBootApplication
public class ParcialCvds2025Application {
	private final Map<Producto, Integer> productos;
	private final List<Alerta> alertas;

    public ParcialCvds2025Application() {
        productos = new HashMap<>();
        alertas = new ArrayList<>();
    }

    /**
     * Add to the system a new product if this one is not in the system and also maps the name and the number of the product that is in
     * @param producto
     * @return True if is successfully the product in the system and false otherwise
     */
    public boolean addProducto(Producto producto){
        if (producto == null){
            return false;
        }
        if (productos.containsKey(producto)) {
            productos.put(producto, productos.get(producto) + 1);
            return true;
        } else {
            productos.put(producto, 1);
        }
        return true;
    }

    public static void main(String[] args) {

    }

}

test 
package eci.edu.cvds.parcialCVDS2025.AlertaTest;

import eci.edu.cvds.parcialCVDS2025.Agente.Alerta;
import eci.edu.cvds.parcialCVDS2025.Agente.Producto;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class AlertasTest {
    private Alerta alerta = new Alerta("Alerta el producto se esta agotando");


    @Test
    public void testGetAlerta(){
        assertEquals("Alerta el producto se esta agotando", alerta.getMensaje(), "El mensaje es: Alerta el producto se esta agotando");
    }

    @Test
    public void testProductoAgotado(){
        Producto producto = new Producto("a", 2, 3000, "Consola");
        alerta.productoAgotado(producto);
        assertEquals("ALERTA!!! El stock del Producto " + "" + producto.getName() + "" + "es muy bajo, solo quedan" + "" + producto.getCantidad(), alerta.productoAgotado(producto), "El mensaje debe ser el correcto" );
    }
}


5 .lab 3: https://github.com/JeissonS02/LAB-03-CVDS-2025-1





6 . se hacen la pruebas de unidad y se comprueba en jacoco 

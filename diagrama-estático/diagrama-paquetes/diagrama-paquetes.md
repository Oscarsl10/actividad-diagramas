# Documentación del Diagrama de Paquetes del Sistema de Carrito de Compras
-Karen Johana Caicedo Arias.
-Oscar Guillermo Sierra Lozano.

## Descripción 
El diagrama de paquetes organiza el sistema de carrito de compras en tres módulos principales: **Usuarios**, **Productos** y **Compras**. 

- **Usuarios** gestiona el registro y la sesión de los usuarios mediante las clases `Usuario` y `Sesion`.
- **Productos** maneja la información y disponibilidad de los productos con las clases `Producto` e `Inventario`.
- **Compras** administra el carrito de compras y la generación de facturas a través de las clases `Carrito`, `DetalleCarrito` y `Factura`.

Las relaciones entre paquetes indican que **Usuarios** interactúa con **Compras** para gestionar el carrito después del inicio de sesión, y **Productos** proporciona la información necesaria para la selección de productos en el carrito.

## Diagrama de Paquetes

A continuación se presenta el diagrama de paquetes del sistema:

```plantuml
@startuml

package "Usuarios" {
  class Usuario {
    - nombre: String
    - correo: String
    - contraseña: String
    + registrarse(): void
    + iniciarSesion(): boolean
  }

  class Sesion {
    - estado: String
    + iniciar(): void
    + cerrar(): void
  }

  Usuario --> Sesion : "gestiona"
}

package "Productos" {
  class Producto {
    - id: Integer
    - nombre: String
    - descripcion: String
    - precio: Float
    - stock: Integer
    + verCatalogo(): List<Producto>
  }

  class Inventario {
    + verificarDisponibilidad(idProducto: Integer, cantidad: Integer): boolean
  }

  Producto --> Inventario : "mantiene"
}

package "Compras" {
  class Carrito {
    - items: List<DetalleCarrito>
    + agregarProducto(producto: Producto, cantidad: Integer): void
    + modificarCantidad(idProducto: Integer, cantidad: Integer): void
    + verCarrito(): List<DetalleCarrito>
  }

  class DetalleCarrito {
    - producto: Producto
    - cantidad: Integer
    - subtotal: Float
  }

  class Factura {
    - detalles: List<DetalleCarrito>
    + generarFactura(): void
  }

  Carrito --> DetalleCarrito : "contiene"
  Factura --> DetalleCarrito : "contiene"
}

"Usuarios" --> "Compras" : "permite gestión de carrito"
"Productos" --> "Compras" : "proporciona información de productos"

@enduml
```
# Resultado

![Diagrama de Paquetes](img/diagrama-paquetes.png)

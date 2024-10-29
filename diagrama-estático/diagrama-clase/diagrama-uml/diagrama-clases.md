# Documentación del Diagrama de Clases del Sistema de Carrito de Compras
-Karen Johana Caicedo Arias.
-Oscar Guillermo Sierra Lozano.

## Objetivo
El objetivo de este documento es describir la estructura del sistema de carrito de compras mediante un diagrama de clases. Este diagrama muestra las principales clases involucradas, sus atributos, métodos y las relaciones entre ellas.

## Diagrama de Clases
A continuación se presenta el diagrama de clases del sistema:

```plantuml
@startuml

class Usuario {
    + id: int
    + nombre: String
    + correo: String
    + contraseña: String
    + registrar(): void
    + iniciarSesion(): boolean
}

class Producto {
    + id: int
    + nombre: String
    + descripcion: String
    + precio: float
    + cantidadEnStock: int
    + mostrarDetalles(): void
}

class Inventario {
    + id: int
    + cantidad: int
    + actualizarStock(cantidad: int): void
}

class Carrito {
    + id: int
    + usuarioId: int
    + agregarProducto(producto: Producto, cantidad: int): void
    + modificarProducto(producto: Producto, cantidad: int): void
    + eliminarProducto(producto: Producto): void
    + verCarrito(): List<Producto>
}

class DetalleFactura {
    + id: int
    + productoId: int
    + cantidad: int
    + precioUnitario: float
    + calcularSubtotal(): float
}

class Factura {
    + id: int
    + usuarioId: int
    + fecha: Date
    + detalles: List<DetalleFactura>
    + total: float
    + generarFactura(): void
    + calcularTotal(): float
}

Usuario "1" --> "1" Carrito : "posee"
Carrito "1" --> "*" Producto : "contiene"
Producto "1" --> "1" Inventario : "se encuentra en"
Carrito "1" --> "*" DetalleFactura : "compuesto de"
Factura "1" --> "*" DetalleFactura : "incluye"
Usuario "1" --> "*" Factura : "realiza"

@enduml


## Diagrama de Clases
![Diagrama de Clases](img/umlclases.png)


# Documentación del Diagrama de Objetos del Sistema de Carrito de Compras
-Karen Johana Caicedo Arias.
-Oscar Guillermo Sierra Lozano.

## Descripción
- El Diagrama de Objetos muestra instancias del sistema de carrito de compras. **Usuario_1** (Juan Pérez) tiene un **Carrito_1** que incluye **Producto_1** (Laptop) y **Producto_2** (Mouse), disponibles en **Inventario_1** y **Inventario_2**. Al confirmar la compra, se genera **Factura_1**, que incluye **DetalleFactura_1** y **DetalleFactura_2** con la cantidad y precio unitario de cada producto, ilustrando las interacciones del usuario con el sistema.

## Diagrama de Objetos
A continuación se presenta el diagrama de objetos del sistema:

```plantuml
@startuml

object Usuario_1 {
    id = 1
    nombre = "Juan Pérez"
    correo = "juan.perez@example.com"
    contraseña = "****"
}

object Carrito_1 {
    id = 101
    usuarioId = 1
}

object Producto_1 {
    id = 201
    nombre = "Laptop"
    descripcion = "Laptop con 16GB RAM y 512GB SSD"
    precio = 5'000,000 COP
    cantidadEnStock = 5
}

object Producto_2 {
    id = 202
    nombre = "Mouse"
    descripcion = "Mouse inalámbrico"
    precio = 100,000 COP
    cantidadEnStock = 10
}

object Inventario_1 {
    id = 301
    cantidad = 5
}

object Inventario_2 {
    id = 302
    cantidad = 10
}

object DetalleFactura_1 {
    id = 401
    productoId = 201
    cantidad = 1
    precioUnitario = 5'000,000 COP
}

object DetalleFactura_2 {
    id = 402
    productoId = 202
    cantidad = 2
    precioUnitario = 100,000 COP
}

object Factura_1 {
    id = 501
    usuarioId = 1
    fecha = "2024-10-30"
    total = 5'200,000 COP
}

Usuario_1 --> Carrito_1 : "posee"
Carrito_1 --> Producto_1 : "contiene"
Carrito_1 --> Producto_2 : "contiene"
Producto_1 --> Inventario_1 : "se encuentra en"
Producto_2 --> Inventario_2 : "se encuentra en"
Factura_1 --> DetalleFactura_1 : "incluye"
Factura_1 --> DetalleFactura_2 : "incluye"
Usuario_1 --> Factura_1 : "realiza"

@enduml
```

## Resultado
![Diagrama de Objetos](img/diagrama-objetos.png)

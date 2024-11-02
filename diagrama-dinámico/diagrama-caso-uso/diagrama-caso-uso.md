# Diagrama caso de uso el Sistema de Carrito de Compras
- Oscar Guillermo Sierra Lozano.
- Karen Johana Caicedo Arias.

## Descripción 
Este diagrama de casos de uso muestra un sistema de Carrito de Compras con dos tipos de usuarios: Usuario y Administrador.

El Usuario puede registrarse, iniciar sesión, ver el catálogo de productos, agregar productos al carrito, ver y modificar su
carrito, eliminar productos del carrito, confirmar su compra, y ver la factura.
El Administrador tiene permisos adicionales para gestionar el catálogo de productos (añadir, modificar, o eliminar productos) y ver
reportes de ventas del sistema.
Ambos actores interactúan con el sistema de acuerdo a sus permisos, y las operaciones están respaldadas por la base de datos (Db).

## Diagrama

```plantuml
@startuml
left to right direction

actor Usuario
actor Administrador
database Db

rectangle "Sistema Carrito de Compras" {
    (Registrarse)
    (Iniciar Sesión)
    (Ver Catálogo de Productos)
    (Agregar Producto al Carrito)
    (Ver Carrito)
    (Modificar Carrito)
    (Eliminar Producto del Carrito)
    (Confirmar Compra)
    (Ver Factura)
    (Gestionar Productos)
    (Ver Reportes de Ventas)
}

Db -> "Sistema Carrito de Compras"

Usuario -- (Registrarse)
(Registrarse) .> (Iniciar Sesión) : <<include>>
Usuario -- (Iniciar Sesión)
(Iniciar Sesión) .> (Ver Catálogo de Productos) : <<include>>
Usuario -- (Ver Catálogo de Productos)
(Ver Catálogo de Productos) --> (Agregar Producto al Carrito)
Usuario -- (Agregar Producto al Carrito)
Usuario -- (Ver Carrito)
(Ver Carrito) .> (Modificar Carrito) : <<extend>>
(Ver Carrito) .> (Eliminar Producto del Carrito) : <<extend>>
Usuario -- (Confirmar Compra)
(Confirmar Compra) .> (Ver Factura) : <<include>>

Administrador -- (Iniciar Sesión)
Administrador -- (Gestionar Productos)
Administrador -- (Ver Reportes de Ventas)

@enduml
```
## Resultado
![Resultado](img/diagrama-caso-uso.png)
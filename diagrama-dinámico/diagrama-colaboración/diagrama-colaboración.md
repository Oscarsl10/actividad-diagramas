# Diagrama de Colaboración (o Comunicación) del Sistema de Carrito de Compras
- Oscar Guillermo Sierra Lozano.
- Karen Johana Caicedo Arias.

## Descripción 
Este diagrama de colaboración representa la interacción entre un usuario y los diferentes módulos de un sistema de compras. El actor
Usuario realiza acciones como registrarse, iniciar sesión, ver el catálogo de productos, agregar productos al carrito, ver y
modificar el carrito, y finalmente confirmar la compra. Cada uno de estos módulos (Registro, Sesión, Catálogo, Carrito y Factura)
responde al usuario con una confirmación, un error, o mostrando la información solicitada. El flujo de interacciones sigue un orden
lógico de cómo un usuario utilizaría el sistema para realizar una compra.

## Diagrama
```plantuml
@startuml
actor Usuario
participant Registro
participant Sesion
participant Catalogo
participant Carrito
participant Factura

Usuario -> Registro: Registrar datos
Registro -> Usuario: Confirmación/Error

Usuario -> Sesion: Iniciar sesión
Sesion -> Usuario: Acceso/Error

Usuario -> Catalogo: Ver productos
Catalogo -> Usuario: Mostrar productos

Usuario -> Carrito: Agregar producto
Carrito -> Usuario: Confirmación/Error

Usuario -> Carrito: Ver carrito
Carrito -> Usuario: Mostrar carrito

Usuario -> Carrito: Modificar carrito
Carrito -> Usuario: Confirmación

Usuario -> Factura: Confirmar compra
Factura -> Usuario: Factura generada
@enduml
```
## Resultado
![Resultado](img/diagrama-colaboración.png)
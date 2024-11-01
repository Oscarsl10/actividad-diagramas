# Diagrama de Estados (o de Estado-Transición) del Sistema de Carrito de Compras
- Oscar Guillermo Sierra Lozano.
- Karen Johana Caicedo Arias.

## Descripción 
Este diagrama de estado describe el flujo de estados en un sistema de carrito de compras. Comienza con el registro, donde el usuario
ingresa sus datos. Si los datos son válidos, el registro se confirma, y el usuario pasa al estado de inicio de sesión. Si las
credenciales son correctas, el usuario accede al sistema; si son incorrectas, se muestra un error.

Después de iniciar sesión, el usuario entra en el estado de ver catálogo, donde puede explorar los productos y seleccionar uno. Esto
lo lleva al estado de carrito, donde puede agregar productos especificando cantidades. Si el producto está en stock, se agrega al
carrito; de lo contrario, se muestra un error. En el carrito, el usuario puede modificar las cantidades o eliminar productos, y
luego confirmar los cambios.

Finalmente, el usuario pasa al estado de confirmación de compra, donde el sistema genera una factura. Cuando la factura es creada,
el proceso de compra termina. Este flujo asegura que el usuario pase por los pasos clave de registro, sesión, visualización de
productos, y compra final, con control de errores en cada etapa.

## Diagrama
```plantuml
@startuml
[*] --> Registro : Inicio del proceso

state Registro {
  [*] --> IngresandoDatos : Datos de registro
  IngresandoDatos --> RegistroConfirmado : Datos válidos
  IngresandoDatos --> ErrorRegistro : Datos inválidos
}

RegistroConfirmado --> Sesion : Iniciar sesión

state Sesion {
  [*] --> IniciandoSesion : Credenciales
  IniciandoSesion --> AccesoConcedido : Credenciales válidas
  IniciandoSesion --> ErrorSesion : Credenciales inválidas
}

AccesoConcedido --> VerCatalogo : Acceso al catálogo

state VerCatalogo {
  [*] --> MostrandoProductos : Visualizar productos
  MostrandoProductos --> ProductoSeleccionado : Seleccionar producto
}

ProductoSeleccionado --> Carrito : Agregar producto

state Carrito {
  [*] --> AgregandoProducto : Selección de cantidad
  AgregandoProducto --> ProductoAgregado : Producto en stock
  AgregandoProducto --> ErrorCarrito : Sin stock
  ProductoAgregado --> ModificandoCarrito : Modificar cantidad/eliminar
  ModificandoCarrito --> CarritoConfirmado : Confirmar cambios
}

CarritoConfirmado --> ConfirmacionCompra : Confirmar compra

state ConfirmacionCompra {
  [*] --> GenerandoFactura : Generación de factura
  GenerandoFactura --> FacturaGenerada : Factura creada
}

FacturaGenerada --> [*] : Fin del proceso

@enduml
```
## Rsultado
![Resultado](img/diagrama-estado.png)
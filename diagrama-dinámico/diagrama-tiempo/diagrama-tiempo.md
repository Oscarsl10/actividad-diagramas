# Diagrama de Tiempo (Timing) del Sistema de Carrito de Compras
- Oscar Guillermo Sierra Lozano.
- Karen Johana Caicedo Arias.

## Descripción 
ESte diagrama de tiempo nos muestra el proceso de interacción entre el usuario y el sistema de carrito de compras:

1. **Registro del Usuario**: El usuario inicia el proceso de registro, el sistema guarda los datos en la base de datos y confirma el
registro exitoso.
2. **Inicio de Sesión**: El usuario se autentica, el sistema valida las credenciales con la base de datos y confirma el acceso.
3. **Visualización del Catálogo**: El usuario solicita ver los productos, el sistema consulta la base de datos y muestra el catálogo
disponible.
4. **Agregar Producto al Carrito**: El usuario agrega un producto, el sistema actualiza el carrito en la base de datos y confirma la
acción.
5. **Confirmación de Compra**: Finalmente, el usuario confirma la compra, el sistema genera una factura en la base de datos y
muestra la factura al usuario.

El diagrama detalla la secuencia de interacciones y el tiempo que cada acción toma, donde evidencia cómo los diferentes componentes
del sistema trabajan juntos para completar el proceso de compra.

## Diagrama
```plantuml
plantuml
@startuml
    title Diagrama de Tiempo - Proceso de Carrito de Compras

    participant Usuario
    participant Sistema
    participant Db

    Usuario -> Sistema : Registrarse
    activate Sistema
    Sistema -> Db : Guardar datos
    activate Db
    Db --> Sistema : Confirmación
    deactivate Db
    Sistema --> Usuario : Registro exitoso
    deactivate Sistema

    Usuario -> Sistema : Iniciar sesión
    activate Sistema
    Sistema -> Db : Validar credenciales
    activate Db
    Db --> Sistema : Acceso permitido
    deactivate Db
    Sistema --> Usuario : Inicio de sesión exitoso
    deactivate Sistema

    Usuario -> Sistema : Ver catálogo de productos
    activate Sistema
    Sistema -> Db : Consultar catálogo
    activate Db
    Db --> Sistema : Productos disponibles
    deactivate Db
    Sistema --> Usuario : Mostrar catálogo
    deactivate Sistema

    Usuario -> Sistema : Agregar producto al carrito
    activate Sistema
    Sistema -> Db : Actualizar carrito
    activate Db
    Db --> Sistema : Confirmación de actualización
    deactivate Db
    Sistema --> Usuario : Producto agregado
    deactivate Sistema

    Usuario -> Sistema : Confirmar compra
    activate Sistema
    Sistema -> Db : Generar factura
    activate Db
    Db --> Sistema : Factura generada
    deactivate Db
    Sistema --> Usuario : Mostrar factura
    deactivate Sistema
@enduml
```

## Resultado
![Diagrama](img/diagrama-tiempo.png)
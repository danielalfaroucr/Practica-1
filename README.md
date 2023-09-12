# Sistema de Gestión de Negocios

Este es un sistema de gestión de negocios que utiliza una base de datos SQL para almacenar y administrar información relacionada con categorías, subcategorías, proveedores, productos, clientes y facturación.

## Descripción

Este sistema permite a los usuarios realizar las siguientes acciones:

- Registrar y administrar categorías y subcategorías de productos.
- Gestionar información de proveedores, incluyendo detalles de contacto.
- Mantener un catálogo de productos, incluyendo precios, tamaños y colores.
- Gestionar información de clientes y sus pedidos.
- Generar facturas con detalles de productos y cálculos de impuestos y descuentos.


## Descripción de las Tablas

El sistema utiliza las siguientes tablas para almacenar y organizar los datos:

### Tabla `Categoria`

- `id_categoria`: Identificador único de la categoría.
- `nombre`: Nombre de la categoría.

### Tabla `Subcategoria`

- `id_subcategoria`: Identificador único de la subcategoría.
- `nombre`: Nombre de la subcategoría.
- `id_categoria`: Identificador de la categoría a la que pertenece (clave foránea).

### Tabla `Provincia`

- `id_provincia`: Identificador único de la provincia.
- `nombre`: Nombre de la provincia.

### Tabla `Canton`

- `id_canton`: Identificador único del cantón.
- `nombre`: Nombre del cantón.
- `id_provincia`: Identificador de la provincia a la que pertenece (clave foránea).

### Tabla `Distrito`

- `id_distrito`: Identificador único del distrito.
- `nombre`: Nombre del distrito.
- `id_canton`: Identificador del cantón al que pertenece (clave foránea).

### Tabla `Proveedor`

- `cedula`: Número de cédula del proveedor (identificador único).
- `nombre`: Nombre del proveedor.
- `correo`: Correo electrónico del proveedor.
- `telefono`: Número de teléfono del proveedor.
- `id_distrito`: Identificador del distrito en el que se encuentra el proveedor (clave foránea).
- `TipoCedula`: Tipo de cédula del proveedor.

### Tabla `Producto`

- `consecutivo`: Identificador único del producto.
- `id_universal`: Identificador universal del producto.
- `nombre`: Nombre del producto.
- `precio`: Precio del producto.
- `id_subcat`: Identificador de la subcategoría a la que pertenece el producto (clave foránea).
- `tamano`: Tamaño del producto (opcional).
- `color`: Color del producto.
- `cedula`: Número de cédula del proveedor que suministra el producto (clave foránea).

### Tabla `Cliente`

- `cedula`: Número de cédula del cliente (identificador único).
- `nombre`: Nombre del cliente.
- `direccion`: Dirección del cliente.
- `correo`: Correo electrónico del cliente.
- `TipoCedula`: Tipo de cédula del cliente.
- `id_distrito`: Identificador del distrito en el que vive el cliente (clave foránea).

### Tabla `Factura`

- `id_factura`: Identificador único de la factura.
- `cedula`: Número de cédula del cliente al que se emite la factura (clave foránea).
- `fecha`: Fecha de emisión de la factura.

## Relaciones entre Tablas

El sistema utiliza las siguientes relaciones entre tablas para organizar y relacionar los datos:

- **Tabla `Subcategoria` con `Categoria`**:
  - La tabla `Subcategoria` tiene una relación de clave foránea con la tabla `Categoria`. Esto permite relacionar subcategorías con categorías específicas.

- **Tabla `Canton` con `Provincia`**:
  - La tabla `Canton` tiene una relación de clave foránea con la tabla `Provincia`. Esto asocia cada cantón con la provincia a la que pertenece.

- **Tabla `Distrito` con `Canton`**:
  - La tabla `Distrito` tiene una relación de clave foránea con la tabla `Canton`. Esto vincula cada distrito con el cantón al que pertenece.

- **Tabla `Proveedor` con `Distrito`**:
  - La tabla `Proveedor` tiene una relación de clave foránea con la tabla `Distrito`. Esto asocia a cada proveedor con el distrito en el que se encuentra.

- **Tabla `Producto` con `Subcategoria`**:
  - La tabla `Producto` tiene una relación de clave foránea con la tabla `Subcategoria`. Esto permite clasificar los productos en subcategorías específicas.

- **Tabla `Producto` con `Proveedor`**:
  - La tabla `Producto` tiene una relación de clave foránea con la tabla `Proveedor`. Esto indica qué proveedor suministra cada producto.

- **Tabla `Cliente` con `Distrito`**:
  - La tabla `Cliente` tiene una relación de clave foránea con la tabla `Distrito`. Esto relaciona a cada cliente con el distrito en el que reside.

- **Tabla `Factura` con `Cliente`**:
  - La tabla `Factura` tiene una relación de clave foránea con la tabla `Cliente`. Esto permite asociar cada factura con el cliente al que se emite.

- **Tabla `productofactura` con `Factura` y `Producto`**:
  - La tabla `productofactura` tiene relaciones de clave foránea con las tablas `Factura` y `Producto`. Esto vincula cada entrada de producto en una factura con la factura correspondiente y el producto comprado.


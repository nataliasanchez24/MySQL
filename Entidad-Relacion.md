EJERCICIO 1: ARTÍCULOS Y ENCARGOS
CLIENTE (NumCliente, Saldo, LimiteCredito, Descuento)
donde
{LimiteCredito} debe ser ≤ 3.000.000 €
DIRECCION_ENVIO (NumCliente, Calle, Numero, Ciudad, CodigoPostal)
donde
{NumCliente} referencia CLIENTE
PEDIDO (NumCliente + Calle + Numero + Ciudad + CodigoPostal, FechaHoraPedido)
donde
{NumCliente, Calle, Numero, Ciudad, CodigoPostal} referencia DIRECCION_ENVIO
ARTICULO (NumArticulo, Descripcion)
LINEA_PEDIDO (NumCliente + Calle + Numero + Ciudad + CodigoPostal + FechaHoraPedido + NumArticulo, Cantidad)
donde
{NumCliente, Calle, Numero, Ciudad, CodigoPostal, FechaHoraPedido} referencia PEDIDO
{NumArticulo} referencia ARTICULO
FABRICA (NumFabrica, TelefonoContacto)
ARTICULO_FABRICA (NumArticulo + NumFabrica, Existencias)
donde
{NumArticulo} referencia ARTICULO
{NumFabrica} referencia FABRICA
FABRICA_ALTERNATIVA (NumFabricaOrigen + NumFabricaAlternativa)
donde
{NumFabricaOrigen} referencia FABRICA
{NumFabricaAlternativa} referencia FABRICA



EJERCICIO 2: SISTEMA DE VENTAS
PROVEEDOR (CIF_Proveedor, Nombre, Telefono, Calle, Numero, Ciudad, Codigo_Postal, Pagina_Web)
CATEGORIA (Id_Categoria, Nombre, Descripcion)
PRODUCTO (Id_Producto, Nombre, Precio_Actual, Stock, CIF_Proveedor, Id_Categoria)
donde
{CIF_Proveedor} referencia PROVEEDOR
{Id_Categoria} referencia CATEGORIA
CLIENTE (CIF_Cliente, Nombre, Calle, Numero, Ciudad, Codigo_Postal)
CLIENTE_TELEFONO (CIF_Cliente + Num_Telefono)
donde
{CIF_Cliente} referencia CLIENTE
FACTURA (Num_Factura, Fecha, Descuento, Importe_Final, CIF_Cliente)
donde
{CIF_Cliente} referencia CLIENTE
DETALLE_VENTA (Num_Factura + Id_Producto, Precio_Venta, Cantidad)
donde
{Num_Factura} referencia FACTURA
{Id_Producto} referencia PRODUCTO
Modelo Relacional Resultante (Formato Diapositiva)



EJERCICIO 3: RED DE CARRETERAS Y TRAMOS
CATEGORIA (Id_Categoria, Nombre_Categoria, Titularidad, Nivel, Prefijo, Color, Señal)
CARRETERA (Cod_Carretera, Nombre, Tipo_Via, Acceso_Controlado, Doble_Calzada, Observaciones, Id_Categoria)
donde
{Id_Categoria} referencia CATEGORIA
TRAMO (Cod_Tramo, Km_Inicial, Km_Final, Tipo_Terreno, Entorno, Velocidad_Limite, Carriles_Por_Sentido, Observaciones, Cod_Carretera)
donde
{Cod_Carretera} referencia CARRETERA
COMUNIDAD_AUTONOMA (Cod_CA, Nombre_CA)
PROVINCIA (Cod_Provincia, Nombre_Provincia, Cod_CA)
donde
{Cod_CA} referencia COMUNIDAD_AUTONOMA
TRAMO_PROVINCIA (Cod_Tramo + Cod_Provincia, Km_Inicio_Provincia, Km_Fin_Provincia)
donde
{Cod_Tramo} referencia TRAMO
{Cod_Provincia} referencia PROVINCIA
EXTREMO_TRAMO (Cod_Tramo + Tipo_Extremo)
donde
{Cod_Tramo} referencia TRAMO
CONFLUENCIA (Id_Confluencia, Km_Confluencia, Cod_Tramo_Origen, Tipo_Extremo_Origen, Cod_Carretera_Destino, Cod_Tramo_Destino, Cod_Provincia_Destino)
donde
{Cod_Tramo_Origen, Tipo_Extremo_Origen} referencia EXTREMO_TRAMO
{Cod_Carretera_Destino} referencia CARRETERA
{Cod_Tramo_Destino} referencia TRAMO
{Cod_Provincia_Destino} referencia PROVINCIA



EJERCICIO 4: SISTEMA DE VUELOS
AEROPUERTO (Cod_Aeropuerto, Nombre, Ciudad, País)
MODELO_AVION (Cod_Modelo, Capacidad)
AEROPUERTO_MODELO (Cod_Aeropuerto + Cod_Modelo)
donde
{Cod_Aeropuerto} referencia AEROPUERTO
{Cod_Modelo} referencia MODELO_AVION
PROGRAMA_VUELO (Num_Vuelo, Linea_Aerea, Cod_Aero_Despegue, Cod_Aero_Aterrizaje)
donde
{Cod_Aero_Despegue} referencia AEROPUERTO
{Cod_Aero_Aterrizaje} referencia AEROPUERTO
PROGRAMA_VUELO_DIA (Num_Vuelo + Dia_Semana)
donde
{Num_Vuelo} referencia PROGRAMA_VUELO


# Ejercicios de Modelo Relacional

Colección de cuatro ejercicios prácticos de diseño de bases de datos mediante el modelo relacional. Se detallan las tablas, las claves primarias (PK), las claves foráneas (FK) y las principales relaciones entre entidades.

## Ejercicio 1. Artículos y encargos

### 1. CLIENTE

| Campo | Descripción |
|---|---|
| `NumCliente` | **PK** — Número de cliente |
| `Saldo` | Saldo del cliente |
| `LimiteCredito` | Límite de crédito |
| `Descuento` | Descuento aplicado |

**Restricción:** `LimiteCredito ≤ 3.000.000 €`

### 2. DIRECCION_ENVIO

| Campo | Descripción |
|---|---|
| `NumCliente` | **PK, FK** → CLIENTE |
| `Calle` | **PK** — Calle |
| `Numero` | **PK** — Número |
| `Ciudad` | **PK** — Ciudad |
| `CodigoPostal` | **PK** — Código postal |

### 3. PEDIDO

| Campo | Descripción |
|---|---|
| `NumCliente` | **PK, FK** → DIRECCION_ENVIO |
| `Calle` | **PK, FK** → DIRECCION_ENVIO |
| `Numero` | **PK, FK** → DIRECCION_ENVIO |
| `Ciudad` | **PK, FK** → DIRECCION_ENVIO |
| `CodigoPostal` | **PK, FK** → DIRECCION_ENVIO |
| `FechaHoraPedido` | **PK** — Fecha y hora del pedido |

### 4. ARTICULO

| Campo | Descripción |
|---|---|
| `NumArticulo` | **PK** — Número de artículo |
| `Descripcion` | Descripción del artículo |

### 5. LINEA_PEDIDO

| Campo | Descripción |
|---|---|
| `NumCliente` | **PK, FK** → PEDIDO |
| `Calle` | **PK, FK** → PEDIDO |
| `Numero` | **PK, FK** → PEDIDO |
| `Ciudad` | **PK, FK** → PEDIDO |
| `CodigoPostal` | **PK, FK** → PEDIDO |
| `FechaHoraPedido` | **PK, FK** → PEDIDO |
| `NumArticulo` | **PK, FK** → ARTICULO |
| `Cantidad` | Cantidad solicitada |

### 6. FABRICA

| Campo | Descripción |
|---|---|
| `NumFabrica` | **PK** — Número de fábrica |
| `TelefonoContacto` | Teléfono de contacto |

### 7. ARTICULO_FABRICA

| Campo | Descripción |
|---|---|
| `NumArticulo` | **PK, FK** → ARTICULO |
| `NumFabrica` | **PK, FK** → FABRICA |
| `Existencias` | Unidades disponibles |

### 8. FABRICA_ALTERNATIVA

| Campo | Descripción |
|---|---|
| `NumFabricaOrigen` | **PK, FK** → FABRICA |
| `NumFabricaAlternativa` | **PK, FK** → FABRICA |

### Relaciones principales

- **CLIENTE — DIRECCION_ENVIO:** un cliente puede tener varias direcciones de envío.
- **DIRECCION_ENVIO — PEDIDO:** cada pedido queda asociado a una dirección de envío.
- **PEDIDO — LINEA_PEDIDO:** un pedido puede contener varias líneas.
- **ARTICULO — LINEA_PEDIDO:** cada línea identifica un artículo y su cantidad.
- **ARTICULO — FABRICA:** relación N:M mediante `ARTICULO_FABRICA`.
- **FABRICA — FABRICA:** relación recursiva mediante `FABRICA_ALTERNATIVA`.

## Ejercicio 2. Sistema de ventas

### 1. PROVEEDOR

| Campo | Descripción |
|---|---|
| `CIF_Proveedor` | **PK** — CIF del proveedor |
| `Nombre` | Nombre |
| `Telefono` | Teléfono |
| `Calle` | Calle |
| `Numero` | Número |
| `Ciudad` | Ciudad |
| `Codigo_Postal` | Código postal |
| `Pagina_Web` | Página web |

### 2. CATEGORIA

| Campo | Descripción |
|---|---|
| `Id_Categoria` | **PK** — Identificador |
| `Nombre` | Nombre |
| `Descripcion` | Descripción |

### 3. PRODUCTO

| Campo | Descripción |
|---|---|
| `Id_Producto` | **PK** — Identificador |
| `Nombre` | Nombre |
| `Precio_Actual` | Precio actual |
| `Stock` | Existencias |
| `CIF_Proveedor` | **FK** → PROVEEDOR |
| `Id_Categoria` | **FK** → CATEGORIA |

### 4. CLIENTE

| Campo | Descripción |
|---|---|
| `CIF_Cliente` | **PK** — CIF del cliente |
| `Nombre` | Nombre |
| `Calle` | Calle |
| `Numero` | Número |
| `Ciudad` | Ciudad |
| `Codigo_Postal` | Código postal |

### 5. CLIENTE_TELEFONO

| Campo | Descripción |
|---|---|
| `CIF_Cliente` | **PK, FK** → CLIENTE |
| `Num_Telefono` | **PK** — Número de teléfono |

### 6. FACTURA

| Campo | Descripción |
|---|---|
| `Num_Factura` | **PK** — Número de factura |
| `Fecha` | Fecha de emisión |
| `Descuento` | Descuento aplicado |
| `Importe_Final` | Importe total |
| `CIF_Cliente` | **FK** → CLIENTE |

### 7. DETALLE_VENTA

| Campo | Descripción |
|---|---|
| `Num_Factura` | **PK, FK** → FACTURA |
| `Id_Producto` | **PK, FK** → PRODUCTO |
| `Precio_Venta` | Precio de venta |
| `Cantidad` | Unidades vendidas |

### Relaciones principales

- **PROVEEDOR — PRODUCTO:** un proveedor puede suministrar varios productos.
- **CATEGORIA — PRODUCTO:** una categoría puede agrupar varios productos.
- **CLIENTE — CLIENTE_TELEFONO:** permite registrar varios teléfonos por cliente.
- **CLIENTE — FACTURA:** un cliente puede tener varias facturas.
- **FACTURA — PRODUCTO:** relación N:M mediante `DETALLE_VENTA`.

### Modelo relacional resultante

El modelo integra proveedores, productos, categorías, clientes y facturación. La tabla `DETALLE_VENTA` permite relacionar cada factura con los productos vendidos, registrando el precio y la cantidad de cada uno.

## Ejercicio 3. Red de carreteras y tramos

### 1. CATEGORIA

| Campo | Descripción |
|---|---|
| `Id_Categoria` | **PK** — Identificador |
| `Nombre_Categoria` | Nombre de la categoría |
| `Titularidad` | Titularidad |
| `Nivel` | Nivel |
| `Prefijo` | Prefijo |
| `Color` | Color |
| `Señal` | Señal |

### 2. CARRETERA

| Campo | Descripción |
|---|---|
| `Cod_Carretera` | **PK** — Código de carretera |
| `Nombre` | Nombre |
| `Tipo_Via` | Tipo de vía |
| `Acceso_Controlado` | Acceso controlado |
| `Doble_Calzada` | Doble calzada |
| `Observaciones` | Observaciones |
| `Id_Categoria` | **FK** → CATEGORIA |

### 3. TRAMO

| Campo | Descripción |
|---|---|
| `Cod_Tramo` | **PK** — Código de tramo |
| `Km_Inicial` | Kilómetro inicial |
| `Km_Final` | Kilómetro final |
| `Tipo_Terreno` | Tipo de terreno |
| `Entorno` | Entorno |
| `Velocidad_Limite` | Velocidad máxima |
| `Carriles_Por_Sentido` | Carriles por sentido |
| `Observaciones` | Observaciones |
| `Cod_Carretera` | **FK** → CARRETERA |

### 4. COMUNIDAD_AUTONOMA

| Campo | Descripción |
|---|---|
| `Cod_CA` | **PK** — Código |
| `Nombre_CA` | Nombre |

### 5. PROVINCIA

| Campo | Descripción |
|---|---|
| `Cod_Provincia` | **PK** — Código |
| `Nombre_Provincia` | Nombre |
| `Cod_CA` | **FK** → COMUNIDAD_AUTONOMA |

### 6. TRAMO_PROVINCIA

| Campo | Descripción |
|---|---|
| `Cod_Tramo` | **PK, FK** → TRAMO |
| `Cod_Provincia` | **PK, FK** → PROVINCIA |
| `Km_Inicio_Provincia` | Kilómetro inicial en la provincia |
| `Km_Fin_Provincia` | Kilómetro final en la provincia |

### 7. EXTREMO_TRAMO

| Campo | Descripción |
|---|---|
| `Cod_Tramo` | **PK, FK** → TRAMO |
| `Tipo_Extremo` | **PK** — Tipo de extremo |

### 8. CONFLUENCIA

| Campo | Descripción |
|---|---|
| `Id_Confluencia` | **PK** — Identificador |
| `Km_Confluencia` | Kilómetro de la confluencia |
| `Cod_Tramo_Origen` | **FK compuesta** → EXTREMO_TRAMO |
| `Tipo_Extremo_Origen` | **FK compuesta** → EXTREMO_TRAMO |
| `Cod_Carretera_Destino` | **FK** → CARRETERA |
| `Cod_Tramo_Destino` | **FK** → TRAMO |
| `Cod_Provincia_Destino` | **FK** → PROVINCIA |

### Relaciones principales

- **CATEGORIA — CARRETERA:** una categoría puede clasificar varias carreteras.
- **CARRETERA — TRAMO:** una carretera puede dividirse en varios tramos.
- **COMUNIDAD_AUTONOMA — PROVINCIA:** una comunidad autónoma puede contener varias provincias.
- **TRAMO — PROVINCIA:** relación N:M mediante `TRAMO_PROVINCIA`.
- **TRAMO — EXTREMO_TRAMO:** los extremos se identifican mediante el código del tramo y el tipo de extremo.
- **EXTREMO_TRAMO — CONFLUENCIA:** identifica el extremo de origen de una confluencia.

## Ejercicio 4. Sistema de vuelos

### 1. AEROPUERTO

| Campo | Descripción |
|---|---|
| `Cod_Aeropuerto` | **PK** — Código |
| `Nombre` | Nombre |
| `Ciudad` | Ciudad |
| `País` | País |

### 2. MODELO_AVION

| Campo | Descripción |
|---|---|
| `Cod_Modelo` | **PK** — Código del modelo |
| `Capacidad` | Capacidad de pasajeros |

### 3. AEROPUERTO_MODELO

| Campo | Descripción |
|---|---|
| `Cod_Aeropuerto` | **PK, FK** → AEROPUERTO |
| `Cod_Modelo` | **PK, FK** → MODELO_AVION |

### 4. PROGRAMA_VUELO

| Campo | Descripción |
|---|---|
| `Num_Vuelo` | **PK** — Número de vuelo |
| `Linea_Aerea` | Línea aérea |
| `Cod_Aero_Despegue` | **FK** → AEROPUERTO |
| `Cod_Aero_Aterrizaje` | **FK** → AEROPUERTO |

### 5. PROGRAMA_VUELO_DIA

| Campo | Descripción |
|---|---|
| `Num_Vuelo` | **PK, FK** → PROGRAMA_VUELO |
| `Dia_Semana` | **PK** — Día de la semana |

### Relaciones principales

- **AEROPUERTO — MODELO_AVION:** relación N:M mediante `AEROPUERTO_MODELO`.
- **AEROPUERTO — PROGRAMA_VUELO:** cada vuelo referencia un aeropuerto de despegue y otro de aterrizaje.
- **PROGRAMA_VUELO — PROGRAMA_VUELO_DIA:** permite registrar los días de operación de cada vuelo.

## Leyenda

| Abreviatura | Significado |
|---|---|
| **PK** | Clave primaria (*Primary Key*) |
| **FK** | Clave foránea (*Foreign Key*) |
| **PK, FK** | Campo que forma parte de la clave primaria y referencia otra tabla |
| **N:M** | Relación de muchos a muchos |




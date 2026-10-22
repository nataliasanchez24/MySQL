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

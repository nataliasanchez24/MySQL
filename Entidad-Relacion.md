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



<h2 style="color:#cc0000">EJERCICIO 1: ARTÍCULOS Y ENCARGOS</h2>

<pre>
<span style="color:#cc0000">CLIENTE</span> (<u>NumCliente</u>, Saldo, LimiteCredito, Descuento)
donde
  {LimiteCredito} ≤ 3.000.000 €

<span style="color:#cc0000">DIRECCION_ENVIO</span> (<u>NumCliente</u>, <u>Calle</u>, <u>Numero</u>, <u>Ciudad</u>, <u>CodigoPostal</u>)
donde
  {NumCliente} referencia CLIENTE

<span style="color:#cc0000">PEDIDO</span> (<u>NumCliente</u> + <u>Calle</u> + <u>Numero</u> + <u>Ciudad</u> + <u>CodigoPostal</u> + <u>FechaHoraPedido</u>)
donde
  {NumCliente, Calle, Numero, Ciudad, CodigoPostal} referencia DIRECCION_ENVIO

<span style="color:#cc0000">ARTICULO</span> (<u>NumArticulo</u>, Descripcion)

<span style="color:#cc0000">LINEA_PEDIDO</span> (<u>NumCliente</u> + <u>Calle</u> + <u>Numero</u> + <u>Ciudad</u> + <u>CodigoPostal</u> + <u>FechaHoraPedido</u> + <u>NumArticulo</u>, Cantidad)
donde
  {NumCliente, Calle, Numero, Ciudad, CodigoPostal, FechaHoraPedido} referencia PEDIDO
  {NumArticulo} referencia ARTICULO

<span style="color:#cc0000">FABRICA</span> (<u>NumFabrica</u>, TelefonoContacto)

<span style="color:#cc0000">ARTICULO_FABRICA</span> (<u>NumArticulo</u> + <u>NumFabrica</u>, Existencias)
donde
  {NumArticulo} referencia ARTICULO
  {NumFabrica} referencia FABRICA

<span style="color:#cc0000">FABRICA_ALTERNATIVA</span> (<u>NumFabricaOrigen</u> + <u>NumFabricaAlternativa</u>)
donde
  {NumFabricaOrigen} referencia FABRICA
  {NumFabricaAlternativa} referencia FABRICA
</pre>

<h2 style="color:#cc0000">EJERCICIO 2: SISTEMA DE VENTAS</h2>

<pre>
<span style="color:#cc0000">PROVEEDOR</span> (<u>CIF_Proveedor</u>, Nombre, Telefono, Calle, Numero, Ciudad, Codigo_Postal, Pagina_Web)

<span style="color:#cc0000">CATEGORIA</span> (<u>Id_Categoria</u>, Nombre, Descripcion)

<span style="color:#cc0000">PRODUCTO</span> (<u>Id_Producto</u>, Nombre, Precio_Actual, Stock, CIF_Proveedor, Id_Categoria)
donde
  {CIF_Proveedor} referencia PROVEEDOR
  {Id_Categoria} referencia CATEGORIA

<span style="color:#cc0000">CLIENTE</span> (<u>CIF_Cliente</u>, Nombre, Calle, Numero, Ciudad, Codigo_Postal)

<span style="color:#cc0000">CLIENTE_TELEFONO</span> (<u>CIF_Cliente</u> + <u>Num_Telefono</u>)
donde
  {CIF_Cliente} referencia CLIENTE

<span style="color:#cc0000">FACTURA</span> (<u>Num_Factura</u>, Fecha, Descuento, Importe_Final, CIF_Cliente)
donde
  {CIF_Cliente} referencia CLIENTE

<span style="color:#cc0000">DETALLE_VENTA</span> (<u>Num_Factura</u> + <u>Id_Producto</u>, Precio_Venta, Cantidad)
donde
  {Num_Factura} referencia FACTURA
  {Id_Producto} referencia PRODUCTO
</pre>

<h2 style="color:#cc0000">EJERCICIO 3: RED DE CARRETERAS Y TRAMOS</h2>

<pre>
<span style="color:#cc0000">CATEGORIA</span> (<u>Id_Categoria</u>, Nombre_Categoria, Titularidad, Nivel, Prefijo, Color, Señal)

<span style="color:#cc0000">CARRETERA</span> (<u>Cod_Carretera</u>, Nombre, Tipo_Via, Acceso_Controlado, Doble_Calzada, Observaciones, Id_Categoria)
donde
  {Id_Categoria} referencia CATEGORIA

<span style="color:#cc0000">TRAMO</span> (<u>Cod_Tramo</u>, Km_Inicial, Km_Final, Tipo_Terreno, Entorno, Velocidad_Limite, Carriles_Por_Sentido, Observaciones, Cod_Carretera)
donde
  {Cod_Carretera} referencia CARRETERA

<span style="color:#cc0000">COMUNIDAD_AUTONOMA</span> (<u>Cod_CA</u>, Nombre_CA)

<span style="color:#cc0000">PROVINCIA</span> (<u>Cod_Provincia</u>, Nombre_Provincia, Cod_CA)
donde
  {Cod_CA} referencia COMUNIDAD_AUTONOMA

<span style="color:#cc0000">TRAMO_PROVINCIA</span> (<u>Cod_Tramo</u> + <u>Cod_Provincia</u>, Km_Inicio_Provincia, Km_Fin_Provincia)
donde
  {Cod_Tramo} referencia TRAMO
  {Cod_Provincia} referencia PROVINCIA

<span style="color:#cc0000">EXTREMO_TRAMO</span> (<u>Cod_Tramo</u> + <u>Tipo_Extremo</u>)
donde
  {Cod_Tramo} referencia TRAMO

<span style="color:#cc0000">CONFLUENCIA</span> (<u>Id_Confluencia</u>, Km_Confluencia, Cod_Tramo_Origen, Tipo_Extremo_Origen, Cod_Carretera_Destino, Cod_Tramo_Destino, Cod_Provincia_Destino)
donde
  {Cod_Tramo_Origen, Tipo_Extremo_Origen} referencia EXTREMO_TRAMO
  {Cod_Carretera_Destino} referencia CARRETERA
  {Cod_Tramo_Destino} referencia TRAMO
  {Cod_Provincia_Destino} referencia PROVINCIA
</pre>

<h2 style="color:#cc0000">EJERCICIO 4: SISTEMA DE VUELOS</h2>

<pre>
<span style="color:#cc0000">AEROPUERTO</span> (<u>Cod_Aeropuerto</u>, Nombre, Ciudad, País)

<span style="color:#cc0000">MODELO_AVION</span> (<u>Cod_Modelo</u>, Capacidad)

<span style="color:#cc0000">AEROPUERTO_MODELO</span> (<u>Cod_Aeropuerto</u> + <u>Cod_Modelo</u>)
donde
  {Cod_Aeropuerto} referencia AEROPUERTO
  {Cod_Modelo} referencia MODELO_AVION

<span style="color:#cc0000">PROGRAMA_VUELO</span> (<u>Num_Vuelo</u>, Linea_Aerea, Cod_Aero_Despegue, Cod_Aero_Aterrizaje)
donde
  {Cod_Aero_Despegue} referencia AEROPUERTO
  {Cod_Aero_Aterrizaje} referencia AEROPUERTO

<span style="color:#cc0000">PROGRAMA_VUELO_DIA</span> (<u>Num_Vuelo</u> + <u>Dia_Semana</u>)
donde
  {Num_Vuelo} referencia PROGRAMA_VUELO
</pre>


# MySQL — Ejercicios y diseño de bases de datos

Repositorio de ejercicios prácticos de **MySQL**, diseño de bases de datos y transformación de modelos entidad-relación a modelo relacional.

## 1. Ciclo de vida de los datos

[**Ver ejercicios del ciclo de vida de los datos**](Ciclo_de_vida_datos.md)

## 2. Diseño de bases de datos

Ejercicios de diseño y modelado de bases de datos.

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Diseño 1</strong><br><br>
      <img src="Diseno1.png" alt="Diseño 1" width="100%">
    </td>
    <td align="center" width="50%">
      <strong>Diseño 2</strong><br><br>
      <img src="Diseno2.png" alt="Diseño 2" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <strong>Diseño 3</strong><br><br>
      <img src="Diseno3.png" alt="Diseño 3" width="100%">
    </td>
    <td align="center" width="50%">
      <strong>Diseño 4</strong><br><br>
      <img src="Diseno4.png" alt="Diseño 4" width="100%">
    </td>
  </tr>
</table>

## 3. Modelo entidad-relación → modelo relacional

Ejercicios de transformación de diagramas entidad-relación en modelos relacionales, identificando entidades, atributos, claves y relaciones.

[**Ver ejercicios de entidad-relación a modelo relacional**](Entidad-Relacion.md)

## 4. Proyecto final

Desarrollo del proyecto final de diseño y modelado de entidades.

<p align="center">
  <img src="proyecto_final.png" alt="Proyecto final de entidades" width="80%">
</p>

### Introducción y Justificación del Proyecto

* **Contexto:** El proyecto consiste en el diseño, modelado e implementación de una base de datos relacional orientada a centralizar, estructurar y analizar la evolución del consumo eléctrico en los hogares españoles durante el periodo de transición energética comprendido entre 2006 y 2026.
* **Justificación:** El análisis del metabolismo energético residencial requiere cruzar múltiples variables heterogéneas (sociales, económicas, tecnológicas y políticas) que habitualmente se encuentran dispersas en diferentes organismos oficiales (INE, Eurostat, IDAE, REE). Esta base de datos unifica toda esa información en un único modelo normalizado y coherente para permitir consultas analíticas complejas.

### Objetivos del Proyecto

* **Objetivo General:** Desarrollar una infraestructura de datos robusta que almacene y relacione de forma eficiente el consumo eléctrico de los hogares en España con los factores socioeconómicos, tecnológicos y normativos que lo condicionan.
* **Objetivos Específicos:**
  * Almacenar las series temporales de producción y consumo eléctrico bruto y residencial entre 2006 y 2026.
  * Relacionar el consumo eléctrico con variables demográficas y sociales (tamaño del hogar, tipologías familiares y evolución de hogares unipersonales).
  * Integrar indicadores económicos clave (renta por quintiles, evolución del precio del kWh corregido por inflación y gasto en energía).
  * Gestionar el impacto de factores tecnológicos (penetración del autoconsumo fotovoltaico, aerotermia y eficiencia de electrodomésticos).
  * Registrar el marco regulatorio e institucional (normativa de eficiencia en edificios, ayudas del IDAE y el impacto histórico de políticas fiscales como el "impuesto al sol").

### Alcance y Delimitación (Scope)

* **Ámbito Geográfico:** España (con enfoque principal en el sistema eléctrico peninsular y nacional según disponibilidad de registros).
* **Ámbito Temporal:** Serie histórica de 2006 a 2026 (con extensiones puntuales hasta 2023 para métricas recientes de autoconsumo fotovoltaico).
* **Población de Estudio:** Exclusivamente el sector residencial (hogares), excluyendo de manera deliberada los sectores industriales y de transporte, tal como delimita el estudio original.

### Fuentes de Datos de Origen

Para poblar y alimentar el sistema de bases de datos, se utilizarán los conjuntos de datos públicos extraídos de las referencias del TFG:

* **INE (Instituto Nacional de Estadística):** Encuesta de Presupuestos Familiares (EPF), gasto medio por hogar y distribución del tamaño/tipo de hogares.
* **Eurostat:** Balances energéticos y consumo final por usos del sector residencial.
* **IDAE (Instituto para la Diversificación y Ahorro de la Energía):** Informes de consumos en usos residenciales y datos de eficiencia.
* **REE (Red Eléctrica de España) / OMIE:** Curvas de demanda horaria y estructura de generación eléctrica.
* **APPA / Statista:** Estadísticas de potencia instalada y número de instalaciones de autoconsumo fotovoltaico.

### Casos de Uso y Consultas Analíticas (SQL / Business Intelligence)

El planteamiento del proyecto se validará demostrando que la base de datos puede responder a las siguientes preguntas de investigación mediante consultas SQL que relacionen las diferentes tablas:

**Pregunta 1. Evolución del consumo eléctrico según el tipo de hogar**

¿Cómo ha evolucionado el consumo eléctrico medio por hogar y por persona en España entre 2006 y 2026, y qué diferencias existen según el número de miembros y la tipología familiar?

- **Tablas relacionadas:** `CONSUME ELÉCTRICO EN LOS HOGARES`, `AÑO` y `CARACTERÍSTICAS DEL HOGAR`.
- **Variables:** año, consumo total, consumo per cápita, tipo de hogar, número de miembros y tamaño del hogar.

**Qué se podría obtener:** comparar hogares unipersonales, parejas y hogares de cuatro o más miembros, identificando qué tipologías presentan mayor consumo por persona y cómo ha cambiado a lo largo del tiempo.

**Pregunta 2. Relación entre renta familiar y consumo eléctrico**

¿Qué relación existe entre el nivel de renta de los hogares y su consumo eléctrico medio, y cómo ha evolucionado esta relación entre 2006 y 2026?

- **Tablas relacionadas:** `INDICADORES ECONÓMICOS`, `CONSUME ELÉCTRICO EN LOS HOGARES`, `AÑO` y `CARACTERÍSTICAS DEL HOGAR`.
- **Variables:** año, quintil de renta, renta disponible media, PIB per cápita, consumo total y consumo per cápita.

**Qué se podría obtener:** comparar los distintos quintiles de renta y analizar si los hogares con mayores ingresos presentan un consumo eléctrico superior o si las diferencias se han reducido con el tiempo.

**Pregunta 3. Evolución del precio de la electricidad y del gasto familiar**

¿Cómo ha evolucionado el precio medio del kWh y qué relación tiene con el gasto energético de los hogares y el porcentaje de renta destinado a electricidad?

- **Tablas relacionadas:** `PRECIO Y GASTO ENERGÉTICO`, `INDICADORES ECONÓMICOS` y `AÑO`.
- **Variables:** año, precio del kWh, tipo de tarifa, impuestos, gasto medio por hogar, porcentaje de renta destinado a energía, IPC e inflación.

**Qué se podría obtener:** identificar los periodos de mayor encarecimiento de la electricidad y comprobar si el gasto energético de los hogares ha aumentado en la misma proporción que los precios.

**Pregunta 4. Autoconsumo fotovoltaico y evolución del consumo residencial**

¿Cómo ha evolucionado la implantación del autoconsumo fotovoltaico en España y qué relación existe entre la potencia instalada, la energía autoconsumida y el consumo eléctrico de los hogares?

- **Tablas relacionadas:** `AUTOCONSUMO FOTOVOLTAICO`, `CONSUME ELÉCTRICO EN LOS HOGARES` y `AÑO`.
- **Variables:** año, número de instalaciones, potencia instalada, energía autoconsumida, energía excedente y consumo total de los hogares.

**Qué se podría obtener:** identificar los años de mayor crecimiento del autoconsumo, analizar su evolución y comparar el aumento de la generación doméstica con la evolución del consumo eléctrico residencial.

**Pregunta 5. Tecnología doméstica y eficiencia energética**

¿Cómo ha evolucionado la incorporación de tecnologías de eficiencia energética en los hogares españoles y qué relación existe entre su implantación y el consumo eléctrico residencial?

- **Tablas relacionadas:** `TECNOLOGÍA DEL HOGAR`, `CARACTERÍSTICAS DEL HOGAR`, `CONSUME ELÉCTRICO EN LOS HOGARES` y `AÑO`.
- **Variables:** año, electrodomésticos, eficiencia energética, sistemas de calefacción, aerotermia, climatización y consumo eléctrico.

**Qué se podría obtener:** comparar la evolución de la adopción de tecnologías eficientes y analizar si los años con mayor implantación coinciden con cambios en el consumo eléctrico.

**Pregunta 6. Políticas energéticas y evolución del autoconsumo**

¿Cómo ha evolucionado el marco regulatorio energético en España y qué relación temporal existe entre los cambios normativos y el crecimiento de las instalaciones de autoconsumo fotovoltaico?

- **Tablas relacionadas:** `POLÍTICAS ENERGÉTICAS`, `AUTOCONSUMO FOTOVOLTAICO` y `AÑO`.
- **Variables:** año, nombre de la política, tipo de regulación, fecha de inicio, fecha de finalización, número de instalaciones y potencia instalada.

**Qué se podría obtener:** comparar los periodos anteriores y posteriores a determinadas reformas regulatorias, como la derogación del denominado "impuesto al sol", y observar cómo evolucionó el autoconsumo.

**Pregunta 7. Consumo residencial y evolución del mercado eléctrico**

¿Qué relación existe entre la evolución de la demanda eléctrica residencial, la generación eléctrica y el precio del mercado eléctrico en España entre 2006 y 2026?

- **Tablas relacionadas:** `CONSUME ELÉCTRICO EN LOS HOGARES`, `INDICADORES DEL MERCADO ELÉCTRICO` y `AÑO`.
- **Variables:** año, consumo residencial, demanda bruta, generación bruta, precio del mercado y tipo de generación.

**Qué se podría obtener:** comparar la evolución de la demanda residencial con la generación eléctrica y los precios del mercado, identificando los periodos en los que se producen mayores diferencias.

## 5. Ejercicios en Microsoft Access

### Ejercicio 2

<p align="center">
  <img src="Ejercicio2_Access.png" alt="Ejercicio 2 en Access" width="80%">
</p>

### Ejercicio 3

<p align="center">
  <img src="Ejercicio3_Access.png" alt="Ejercicio 3 en Access" width="80%">
</p>

### Ejercicio 4

<p align="center">
  <img src="Ejercicio4_Access.png" alt="Ejercicio 4 en Access" width="80%">
</p>

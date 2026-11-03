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

1. **¿Cómo ha evolucionado el consumo eléctrico medio por hogar y por persona en España entre 2006 y 2026, y qué diferencias existen según el número de miembros y la tipología familiar?** (Análisis de las diferencias de consumo entre hogares unipersonales, parejas y hogares de cuatro o más miembros, así como de las economías de escala).

2. **¿Qué relación existe entre el nivel de renta de los hogares y su consumo eléctrico medio, y cómo ha evolucionado esta relación entre 2006 y 2026?** (Comparación del consumo eléctrico entre quintiles de renta para identificar diferencias en los patrones de consumo según la capacidad económica de los hogares).

3. **¿Cómo ha evolucionado el precio medio del kWh y qué relación tiene con el gasto energético de los hogares y el porcentaje de renta destinado a electricidad?** (Análisis de la evolución de los precios, los impuestos, la inflación y el esfuerzo económico que representa el consumo eléctrico para las familias).

4. **¿Cómo ha evolucionado la implantación del autoconsumo fotovoltaico en España y qué relación existe entre la potencia instalada, la energía autoconsumida y el consumo eléctrico de los hogares?** (Estudio del crecimiento de las instalaciones fotovoltaicas y de su relación con la evolución del consumo residencial).

5. **¿Cómo ha evolucionado la incorporación de tecnologías de eficiencia energética en los hogares españoles y qué relación existe entre su implantación y el consumo eléctrico residencial?** (Análisis de la penetración de electrodomésticos eficientes, aerotermia, sistemas de calefacción y climatización, y su relación con los patrones de consumo).

6. **¿Cómo ha evolucionado el marco regulatorio energético en España y qué relación temporal existe entre los cambios normativos y el crecimiento de las instalaciones de autoconsumo fotovoltaico?** (Comparación de los periodos anteriores y posteriores a reformas regulatorias, como la derogación del denominado "impuesto al sol", para estudiar la evolución de la adopción del autoconsumo).

7. **¿Qué relación existe entre la evolución de la demanda eléctrica residencial, la generación eléctrica y el precio del mercado eléctrico en España entre 2006 y 2026?** (Comparación de la demanda residencial, la generación eléctrica y los precios del mercado para identificar tendencias y cambios en el sistema eléctrico).

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

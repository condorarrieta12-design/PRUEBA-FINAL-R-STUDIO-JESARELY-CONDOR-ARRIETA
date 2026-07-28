Autor: Condor Arrieta Jesarely
Curso: Ofimática para Economistas
Docente: Mirko Smith Caja Ventura
Año: 2026
#------------------------------------------------------------------------------
# PRUEBA-FINAL-R-STUDIO-JESARELY
"Análisis exploratorio de las multas administrativas activas de la Municipalidad Distrital de Ate"

## 1. Contexto del conjunto de datos

La base corresponde a registros administrativos de multas activas de la **Municipalidad Distrital de Ate**. La fecha de corte incluida en el archivo es el **19 de junio de 2024**.

Las variables principales analizadas son el año y fecha de la multa, zona, giro, código y descripción de la infracción, monto, interés, gastos, costas, descuento y total registrado.

La base original se conserva sin modificaciones en:

`data/multas_ate_original.csv`

## 2. Objetivo

Realizar un Análisis Exploratorio de Datos con R para identificar patrones temporales, describir la distribución de los importes y reconocer los giros que concentran la mayor cantidad de registros y el mayor importe total.

## 3. Limpieza y preparación

Las transformaciones se encuentran en `scripts/EDA.R` y siguen las funciones trabajadas en clase: `read_csv()`, `glimpse()`, `is.na()`, `rename()`, `mutate()`, `select()`, `filter()`, `group_by()`, `summarise()`, `count()` y `ggplot()`.

Se realizaron las siguientes acciones:

1. Cambio de nombres de variables.
2. Conservación de códigos como texto.
3. Eliminación de 2 registros duplicados exactos.
4. Conversión de fechas numéricas al formato fecha.
5. Corrección documentada de `21070704` a `20170704`.
6. Reemplazo de vacíos por cero únicamente en interés, gastos, costas y descuento.
7. Limpieza de espacios repetidos en giro y descripción.
8. Creación de año, mes, presencia de descuento y rango del importe total.
9. Guardado de la base limpia como objeto propio de R mediante `saveRDS()`.

### Archivos de datos

- `data/multas_ate_original.csv`: archivo oficial original.
- `data/multas_ate_limpia.R`: objeto limpio de R incluido y listo para cargar con `source()`.
- `data/multas_ate_limpia.rds`: se genera automáticamente al ejecutar `scripts/EDA.R`.

**No se entrega una segunda base limpia en CSV.**

## 4. Estadísticas descriptivas

Después de eliminar duplicados se analizaron **53,504 registros**.

| Indicador | Resultado |
|---|---:|
| Importe total acumulado | S/ 240.362.646,18 |
| Promedio por registro | S/ 4.492,42 |
| Mediana por registro | S/ 592,50 |
| Desviación estándar | S/ 141.999,37 |
| Valor mínimo | S/ 0,01 |
| Valor máximo | S/ 31.184.042,89 |

El promedio es muy superior a la mediana. Esto indica que existen valores extremos que elevan el promedio y que la distribución no es simétrica.

## 5. Visualizaciones del EDA

![Collage de gráficos](figures/collage_graficos.png)

Los gráficos presentan la evolución anual, los giros con más registros, los giros con mayor importe y la distribución de los importes. El dato de 2024 es parcial porque el corte se realizó el 19 de junio.

# Parte 2: análisis final

## Pregunta

**¿Los giros con mayor cantidad de registros de multas también presentan el mayor importe total registrado?**

## Resultados

El giro con más registros es **TRANSPORTE**, con **4.684 registros** y un importe acumulado aproximado de **S/ 2.691.465,98**.

El mayor importe total corresponde a **OF. ADMINISTRATIVA**, con aproximadamente **S/ 34.257.793,02** y solamente **460 registros**.

![Gráfico final](figures/grafico_final_giros.png)

## Conclusiones

1. La respuesta a la pregunta es **no**: los giros con más registros no necesariamente concentran el mayor importe total.
2. Transporte encabeza la cantidad de registros, pero no el importe acumulado.
3. Oficina Administrativa presenta el mayor importe total con una cantidad mucho menor de registros.
4. La diferencia entre promedio y mediana confirma la presencia de importes extremos.
5. El análisis es descriptivo y se limita a los registros activos contenidos en la base al corte de junio de 2024.
